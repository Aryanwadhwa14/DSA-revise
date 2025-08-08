# DSA-revision of the 150 question series (3 per day) with notes ofc.   
---
# Top Interview 150 Leetcode  [link](https://leetcode.com/studyplan/top-interview-150/) 
---
## 1. Merge Sorted array.  [link](https://leetcode.com/problems/merge-sorted-array/description/?envType=study-plan-v2&envId=top-interview-150)
## Notes :  
### Intuition : 
We are given two sorted arrays nums1 and nums2 of sizes m and n, respectively. We need to merge these two arrays into a single sorted array, and the result should be stored inside nums1. Since nums1 is of size m+n, we can use this extra space to store the merged array. We can iterate through the arrays from the end and place the larger element in the end of nums1.

### Approach : Using STL
1. Traverse through nums2 and append its elements to the end of nums1 starting from index m.
2. Sort the entire nums1 array using sort() function.

### Code (in cpp) 
```bash
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        for (int j = 0, i = m; j<n; j++){
            nums1[i] = nums2[j];
            i++;
        }
        sort(nums1.begin(),nums1.end());
    }
};
```

### Complexity
 - Time complexity: O((m+n)log(m+n))
   due to the sort() function

 - Space complexity: O(1) 2
   We are not using any extra space, so the space complexity is O(1).
---
## 2. Remove element. [link](https://leetcode.com/problems/remove-element/?envType=study-plan-v2&envId=top-interview-150)
## Notes : 
### Intuition
The intuition behind this solution is to iterate through the array and keep track of two pointers: index and i. The index pointer represents the position where the next non-target element should be placed, while the i pointer iterates through the array elements. By overwriting the target elements with non-target elements, the solution effectively removes all occurrences of the target value from the array.

### Code : 

```bash
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int index = 0; // for loop approach, v easy with indentation 
        for(int i = 0; i< nums.size(); i++){
            if(nums[i] != val){
                nums[index] = nums[i];
                index++;
            }
        }
        return index;
    }
};
```

### Approach
1. Initialize index to 0, which represents the current position for the next non-target element.
2. Iterate through each element of the input array using the i pointer.
3. For each element nums`i`, check if it is equal to the target value.
- If nums[i] is not equal to val, it means it is a non-target element.
- Set nums `index` to nums`i` to store the non-target element at the current index position.
- Increment index by 1 to move to the next position for the next non-target element.
4. Continue this process until all elements in the array have been processed.
5. Finally, return the value of index, which represents the length of the modified array.

### Complexity
Time complexity:
O(n)

Space complexity:
O(1)
--- 
##

