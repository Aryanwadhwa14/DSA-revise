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
