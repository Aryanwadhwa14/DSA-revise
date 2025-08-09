# DSA-revision of the 150 question series (3 per day) with notes ofc. (Documenting my journey) 
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

### Code : (in cpp)

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
- If nums`i` is not equal to val, it means it is a non-target element.
- Set nums `index` to nums`i` to store the non-target element at the current index position.
- Increment index by 1 to move to the next position for the next non-target element.
4. Continue this process until all elements in the array have been processed.
5. Finally, return the value of index, which represents the length of the modified array.

### Complexity : 
Time complexity: O(n)
Space complexity: O(1)

--- 
## 3.  Remove Duplicates from Sorted Array [link](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/?envType=study-plan-v2&envId=top-interview-150)
## Notes : 
### Approach & Step-by-Step Visualization:
The code starts iterating from `i = 1` because we need to compare each element with its previous element to check for duplicates.

1 . Initialize `j = 1` (first unique element is already at nums[0]).

2 . Loop from `i = 1` to end:

If `nums[i] != nums[i-1]` (new unique element found):
▪ Store it at `nums[j]`
▪ Increment `j`

3 . Return `j` (number of unique elements).

### code : 
```bash
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int j = 1; // two pointer approach
        for(int i = 1; i < nums.size(); i++){
            if(nums[i] != nums[i - 1]){
                nums[j] = nums[i];
                j++;
            } // for loop, if to check whether the element is in the array or not 
        }    
        return j;
    }
};
```

### Complexity : 
Time Complexity : O (N) 
Space complexity : O(1)

---
## 4. Remove Duplicates from Sorted Array II [link](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/description/?envType=study-plan-v2&envId=top-interview-150)
## Notes : 
### Approach
The goal of this function is to remove duplicates from the nums vector while keeping at most two occurrences of any element. The function returns the length of the modified vector after removing duplicates.

Here's the approach implemented in the code:

Initialize an integer variable i to 0. This variable will keep track of the current position in the modified nums vector.

Use a for loop to iterate through each element ele in the nums vector using the range-based for loop.

Inside the loop, check the following conditions:
- i == 0: This condition ensures that the first element is always included in the modified vector.
- i == 1: This condition ensures that the second element is always included in the modified vector.
- nums[i-2] != ele: This condition checks if the current element ele is not the same as the element two positions before the current position i. This ensures that only two occurrences of any element are included in the modified vector.
- If any of the above conditions are met, copy the current element ele to the nums[i] position in the modified vector, and increment i by 1 to move to the next position.
- Repeat this process for all elements in the nums vector.

- Finally, return the value of i, which represents the length of the modified vector with duplicates removed.

- This approach effectively modifies the nums vector in place, removing duplicates while keeping at most two occurrences of each element. The function returns the length of the modified - vector, which can be used to access the unique elements in the first i positions of the vector

### Code : 
```bash
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int a = 0;
        for(int i = 0;i<nums.size();i++){
           if(a < 2 || nums[i] != nums[a-2]){
            nums[a++] = nums[i];
           }  // again for loop 
           
        }
        return a;
    }
};
```
### Complexity : 
Time complexity:0(N)
Space complexity:0(1)

---

## 5. Majority Element. [link](https://leetcode.com/problems/majority-element/submissions/?envType=study-plan-v2&envId=top-interview-150)
### Notes : Approach 1: Sorting
### Intuition:
The intuition behind this approach is that if an element occurs more than n/2 times in the array (where n is the size of the array), it will always occupy the middle position when the array is sorted. Therefore, we can sort the array and return the element at index n/2.

Explanation:
The code begins by sorting the array nums in non-decreasing order using the sort function from the C++ Standard Library. This rearranges the elements such that identical elements are grouped together.
- Once the array is sorted, the majority element will always be present at index n/2, where n is the size of the array.
- This is because the majority element occurs more than n/2 times, and when the array is sorted, it will occupy the middle position.
- The code returns the element at index n/2 as the majority element.

### Complexity : 
Time Complexity : O(nlogn) 
Space Complexity : O(1) 

### Code : 
```bash
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        int n = nums.size();
        return nums[n/2];
    }
};
```
---
## 6. Rotate Array : [link](https://leetcode.com/problems/rotate-array/description/?envType=study-plan-v2&envId=top-interview-150)
### Notes : Approach
Simple use of reverse function

### Complexity : 
Time complexity: O(N)
Space complexity: O(1)

Code : 
```bash
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        int n = nums.size();
        k = k % n; // Ensure k is within the range [0, n)

        // Reverse the entire array
        reverse(nums.begin(), nums.end());
        
        // Reverse the first k elements
        reverse(nums.begin(), nums.begin() + k);
        
        // Reverse the rest of the elements after k
        reverse(nums.begin() + k, nums.end());
    }
};
```
---
7. -




