# LEETCODE-Arrays-1800
**Code:**

```java
class Solution {
    public int maxAscendingSum(int[] nums) {
        int n =nums.length;
        int maxsum=0;
        int sum=nums[0];
        for(int i=1;i<n;i++)
        {
            if(nums[i]>nums[i-1])
            {
                sum+=nums[i];
            }
            else{
                maxsum=Math.max(maxsum,sum);
                sum=nums[i];
            }
            
        }
        return Math.max(maxsum,sum);
    }
}
```

**Explanation:**

This code finds the maximum sum of a contiguous ascending subsequence in an array.

1. **Initialization:**
   - `n`: Stores the length of the input array `nums`.
   - `maxsum`: Stores the maximum sum of any ascending subsequence found so far, initialized to 0.
   - `sum`: Stores the sum of the current ascending subsequence. Initially, it's set to the first element of the array `nums[0]`.

2. **Iteration:**
   - The code iterates through the array `nums` starting from the second element (index 1).
   - **If `nums[i]` > `nums[i-1]`:**
      - The current subsequence is still ascending. 
      - Add `nums[i]` to the `sum`.
   - **If `nums[i]` <= `nums[i-1]`:**
      - The current ascending subsequence ends.
      - Update `maxsum` with the maximum of the current `maxsum` and the `sum` of the previous ascending subsequence.
      - Reset `sum` to the current element `nums[i]` to start a new potential ascending subsequence.

3. **Return Result:**
   - After iterating through the entire array, return the maximum of `maxsum` and the final value of `sum`. This ensures that the last potential ascending subsequence is also considered.

**Dry Run Example:**

Let's consider:

- `nums = [10,20,30,5,10]`

1. **Initialization:**
   - `n = 5`, `maxsum = 0`, `sum = 10`

2. **Iteration:**
   - `i = 1`: 
      - `nums[1] > nums[0]` (20 > 10) 
      - `sum = 10 + 20 = 30`
   - `i = 2`:
      - `nums[2] > nums[1]` (30 > 20)
      - `sum = 30 + 30 = 60`
   - `i = 3`:
      - `nums[3] <= nums[2]` (5 <= 30)
      - `maxsum = max(maxsum, sum) = max(0, 60) = 60` 
      - `sum = 5`
   - `i = 4`:
      - `nums[4] > nums[3]` (10 > 5)
      - `sum = 5 + 10 = 15`

3. **Return Result:**
   - `return Math.max(maxsum, sum) = max(60, 15) = 60`

The maximum sum of any ascending subsequence in the given array is 60.
