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
## 7. Best time to buy and sell stock : [link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/?envType=study-plan-v2&envId=top-interview-150)
### Notes : Approach
 - Initialize variables buy with the first element of the prices array and profit as 0.
 - Iterate through the prices starting from the second element.
 - Update the buy variable if the current price is lower than the current buying price.
 - Update the profit if the difference between the current price and the buying price is greater than the current profit.
 - Return the final profit.

### Kadane's Algorithm
Kadane's Algorithm is a dynamic programming technique used to find the maximum subarray sum in an array of numbers. The algorithm maintains two variables: max_current represents the maximum sum ending at the current position, and max_global represents the maximum subarray sum encountered so far. At each iteration, it updates max_current to include the current element or start a new subarray if the current element is larger than the accumulated sum. The max_global is updated if max_current surpasses its value.

### Relating with the Approach
In the provided approach for finding the maximum profit in stock prices, the algorithm can be seen as a variation of Kadane's Algorithm. Instead of finding the maximum subarray sum directly, it focuses on finding the maximum positive difference between consecutive elements (prices) in the array.

### Here's how the approach relates to Kadane's Algorithm:

Initialization:

In Kadane's Algorithm, max_current and max_global are initialized to the first element of the array.
In the stock profit approach, buy is initialized with the first element of the prices array, and profit is initialized to 0.
Iteration:

Kadane's Algorithm iterates through the array, updating max_current based on the current element's value and deciding whether to start a new subarray.
The stock profit approach iterates through the prices array, updating buy when a lower price is encountered and treating the difference between the current price and buy as a potential profit.
Comparison and Update:

Kadane's Algorithm compares and updates max_current and max_global at each iteration.
The stock profit approach compares and updates profit whenever a positive difference between the current price and buy exceeds the current profit.

### Complexity
Time complexity: O(n), where n is the length of the prices array. The algorithm iterates through the array once.
Space complexity: O(1), as only a constant amount of extra space is used. 

code : 
```bash
class Solution {
public:
    int maxProfit(std::vector<int>& prices) {
        int buy = prices[0];
        int profit = 0;
        for (int i = 1; i < prices.size(); i++) {
            if (prices[i] < buy) {
                buy = prices[i];
            } else if (prices[i] - buy > profit) {
                profit = prices[i] - buy;
            }
        }
        return profit;
    }
};
```
--- 
## 8. Best time to buy stock (part 2) [link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/?envType=study-plan-v2&envId=top-interview-150)
### Notes : 
Intuition
Approach
We can find max profit, using greedy approach. i.e. we make optimal decision as we iterate over array.
If prices[i] < prices[i+1], add profit = prices[i + 1] - prices[i] into sum.
At the end of array we will have maximum profit that can be made. Return the sum.
Complexity
Time complexity: O(n)
Space complexity: O(1) 

### Code : 
```bash
class Solution {
public:
    int maxProfit(vector<int>& prices) {
         int res = 0;
        int n = prices.size();

        for (int i = 1; i < n; i++) {
            if (prices[i] > prices[i - 1]) {
                res += prices[i] - prices[i - 1];
            }
        }
        return res;
    }
};
```
## 9. Jump game [link](https://leetcode.com/problems/jump-game/?envType=study-plan-v2&envId=top-interview-150)
### notes : Intuition
The goal is to determine if we can reach the last index from the first index.
Since each number represents how far we can jump, we need a way to track the farthest point reachable as we go.

### Approach
We use a greedy strategy and keep a variable maxReach to store the farthest index we can reach at any point.
As we iterate through the array:

If the current index i is greater than maxReach, it means we are stuck and can't proceed.
Otherwise, we update maxReach to the maximum of its current value and i + nums[i].
If we can iterate through the entire array without getting stuck, we can reach the last index.

### Complexity
Time complexity:
O(n) — We iterate through the array once

Space complexity:
O(1) — No extra space used

Code : 
``` bash
class Solution {
public:
    bool canJump(vector<int>& nums) {
        int need = 1;
        if(nums.size() == 1) return true;
        for (int i=nums.size()-2; i>0; i--) {
            if (nums[i] < need) {
                need++;
            } else {
                need = 1;
            }
        }
        return (nums[0] >= need); 
    }
};
```
---
## 10. Jump Game II [link](https://leetcode.com/problems/jump-game-ii/?envType=study-plan-v2&envId=top-interview-150)
### Notes : Intuition
The problem asks for the minimum number of jumps to reach the last index in an array where each element represents the maximum jump length from that position. My first thought is to treat this like a greedy range expansion problem—at each position, jump to the place that allows us to reach the farthest in the future. Instead of checking every possible sequence of jumps (which would be too slow), we can always choose the jump that gives the maximum reach from the current range.

### Approach
We first precompute a jumps array where jumps[i] = i + nums[i] (the farthest position reachable from index i).
We start at index 0 and repeatedly select the next position that can reach the farthest point in the future within the current jump's range. This is done by iterating over all positions from i+1 to i + nums[i] and picking the one with the maximum jumps[j]. Each time we move to this new position, we increment the jump count. If from the current position we can already reach or cross the last index, we make one final jump and terminate. This greedy strategy ensures the minimum number of jumps.

### Complexity : 

Time complexity: O(n^2)

Space complexity: O(n)

### Code : 
```bash
class Solution {
public:

    int jump(vector<int>& nums) {

      for(int i = 1; i < nums.size(); i++)
      {
        nums[i] = max(nums[i] + i, nums[i-1]);
      }

      int ind = 0;
      int ans = 0;

      while(ind < nums.size() - 1)
      {
        ans++;
        ind = nums[ind];
      }

      return ans;
    }
};
```
--- 
## 11. H-index [link](https://leetcode.com/problems/h-index/solutions/7068659/fastest-most-optimal-binary-search-approach-no-extra-space-h-index/?envType=study-plan-v2&envId=top-interview-150)
### Notes : Intuition
Instead of sorting the array or using extra space, we can use binary search on the possible h values (from 0 to max(citation)), counting how many papers meet the threshold each time.

### Approach
 - Find the maximum citations in the array to define the binary search range.
 - Apply binary search on h:
Count how many papers have citations ≥ mid.
 - If count ≥ mid, move right (possible higher h-index).
 - Else, move left.
Return the best possible h.

### Time Complexity
O(n log m), where n is the number of papers and m is the max citation count.

### Space Complexity
O(1) — No extra arrays used.

### Code :

```bash
class Solution {
public:
    int hIndex(vector<int>& citations) {
        int papers = citations.size();
        vector<int> citationBuckets(papers + 1, 0);

        for (int citation : citations) {
            citationBuckets[min(citation, papers)]++;
        }

        int cumulativePapers = 0;
        for (int hIndex = papers; hIndex >= 0; hIndex--) {
            cumulativePapers += citationBuckets[hIndex];
            if (cumulativePapers >= hIndex) {
                return hIndex;
            }
        }Insert Delete GetRandom O(1)
        return 0;        
    }
};
```
---
## 12. Insert Delete GetRandom O(1) [link](https://leetcode.com/problems/insert-delete-getrandom-o1/description/?envType=study-plan-v2&envId=top-interview-150)
### Notes : Intuition
To support all operations in average O(1) time, we need:
An array for O(1) random access.
A hash map to track element positions for O(1) insert/delete.

### Approach
 - insert: Add to array and store index in a map.
 - remove: Swap target with last, pop it, and update map.
 - getRandom: Return a random element from array.
 - This trick is a must-know for interviews and shows up often in design questions.

### Complexity

Time Complexity:
( O(1) ) — for insert, remove, and getRandom.

Space Complexity:
( O(n) ) — to store elements and positions.

### Code : 
```bash
class RandomizedSet {
    vector<int> v;
    unordered_map<int,int> mp;
public:
   
    RandomizedSet() {
    }

    bool search(int val){

         if(mp.find(val)!=mp.end())
            return true;
         return false;

    }

    
    bool insert(int val) {

        if(search(val))
            return false;

        v.push_back(val);
        mp[val] = v.size()-1;
        return true;
    }

    
    bool remove(int val) {

        if(!search(val))
            return false;

       
        auto it = mp.find(val);
        v[it->second] = v.back();
        v.pop_back();
        mp[v[it->second]] = it->second;
        mp.erase(val);
        return true;
    }

   
    int getRandom() {

        return v[rand()%v.size()];
    }
};
```
## 13. Product of Array except Self [link](https://leetcode.com/problems/product-of-array-except-self/description/?envType=study-plan-v2&envId=top-interview-150)
### Notes : Intuition
Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

### My Approach : 
Our approach is simple. now we have to take the product of the array and store it.
here we have three cases:-
where we do have no zeros at all :- here we can just simply store the product and at each nums[i]=product/nums[i] which results in getting the complete product except that number.
where we have 1 zero :- Here we have to return all the elements as zero except that one original zero as the product of rest all numbers.
where we have more than 1 zero :- here the complete array would be zero as the result so we simply return the n size array containing all zeros.

### Complexity : 
Time complexity: O(n)
Space complexity: O(n)

### Code : 
```bash
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int n = nums.size();
        vector<int> result(n);
        int zeroCount = 0;
        int product = 1;
        
        for (int i = 0; i < n; i++) {
            if (nums[i] == 0) {
                zeroCount++;
            } else {
                product *= nums[i];
            }
        }
        
        if (zeroCount > 1) {
            return vector<int>(n, 0);
        }
        
        for (int i = 0; i < n; i++) {
            if (zeroCount == 1) {
                if (nums[i] == 0) {
                    result[i] = product;
                } else {
                    result[i] = 0;
                }
            } else {
                result[i] = product / nums[i];
            }
        }
        
        return result;
    }
};
```
## 14. Gas Station : [link](https://leetcode.com/problems/gas-station/solutions/3011141/c-easy-solution-with-explaination-in-o-n-time-complexity-beats-97/?envType=study-plan-v2&envId=top-interview-150)
### Notes : Intuition
Here we will apply greedy approach

### Approach
In the question given that
If there exists a solution, it is guaranteed to be unique
-This lines clearly tells us that we have unique or no solution exists

Here two cases are possible

if our total_gas is less than our total cost in that case we can't complete our journey ,so will return -1
Now we have a unique solution that means single starting_point exists
To find that point we will keep track of my current_gas+=gas[i]-cost[i]
lets suppose at any index our current gas became negative so we can clearly say that till that index all the gas station between ith and starting point are bad, starting point as well.
So, this means we can start trying at next gas_station on the i+1 station

### Complexity
Time complexity:O(N)
Space complexity:O(1)

### Code : 
```bash
class Solution {
public:
    int canCompleteCircuit(vector<int>& gas, vector<int>& cost) {
        ios_base::sync_with_stdio(false);
        cin.tie(NULL);
        int n = cost.size(), bal = 0, start = 0, deficit = 0;

        for(int i = 0; i< n; i++){
            bal += gas[i] - cost[i];

            if(bal < 0){

                deficit += bal;
                start = i+1;
                bal = 0;
            }
        }
        return bal + deficit >= 0 ? start : -1;
    }
}; //beats 100% solutions 
```
## 15. Candy [link](https://leetcode.com/problems/candy/solutions/7082183/greedy-candy-giveaway/?envType=study-plan-v2&envId=top-interview-150)
### Notes : Intuition
One pass can only satisfy one side’s rule (left or right neighbor). Two passes ensure both rules holds. Taking the max ensures the child meets both requirements.

### Approach
Left to Right pass: Start with 1 candy each. If ratings[i] > ratings[i-1], give left[i] = left[i-1] + 1.
Right to Left pass: Again start with 1 candy each from the right. If ratings[i] > ratings[i+1], give right[i] = right[i+1] + 1.
Combine: For each child, take max(left[i], right[i]) and sum.

### Complexity
Time complexity:
O(3n) — 3 passes over the array.

Space complexity:
Space: O(2n) — two helper arrays.

### Code : 
```bash
class Solution {
public:
    int candy(vector<int>& ratings) 
    {
        int n=ratings.size();
        vector<int>left(n,-1);
        int inc=0;
        left[0]=1;
        for(int i=1;i<n;i++)
        {
            if(ratings[i-1]<ratings[i])
            {
                inc = left[i - 1] + 1; 
                left[i] = inc;
            }
            else
            {
                inc=1;
                left[i]=inc;
            }
        }
        vector<int>right(n,-1);
        right[n-1]=1;
        for(int i=n-2;i>=0;i--)
        {
            if(ratings[i]>ratings[i+1])
            {
                inc=right[i+1]+1;
                right[i]=inc;
            }
            else
            {
                inc=1;
                right[i]=inc;
            }
        }
        int ans=0;
        for(int i=0;i<n;i++)
        {
            ans+=max(left[i],right[i]);
        }
        return ans;
    }
//please upvote 
};
```
## 16. Trapping rain water [link](https://leetcode.com/problems/trapping-rain-water/description/?envType=study-plan-v2&envId=top-interview-150)
### Intuition
Imagine water trapped between bars. The amount of water at each index depends on the shorter of the tallest bars to the left and right.
We can precompute this and use math to subtract the height of the current bar to find the trapped water at that point.

### Approach : 
Use two arrays:
left[i]: the max height from the left up to index i
right[i]: the max height from the right up to index i
For each index i, trapped water is min(left[i], right[i]) - height[i]
Sum this for all indices to get total water.

### Complexity : 
Time Complexity: O(n) – single pass for left, right, and result.
Space Complexity: O(n) – extra arrays left and right.

### Code : 
```bash
class Solution {
public:
    int trap(vector<int>& height) {
        int left = 0;
        int right = height.size() - 1;
        int leftMax = height[left];
        int rightMax = height[right];
        int water = 0;

        while (left < right) {
            if (leftMax < rightMax) {
                left++;
                leftMax = max(leftMax, height[left]);
                water += leftMax - height[left];
            } else {
                right--;
                rightMax = max(rightMax, height[right]);
                water += rightMax - height[right];
            }
        }

        return water;        
    }
};
```









