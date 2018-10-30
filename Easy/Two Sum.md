# Problem

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:

Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9, return [0, 1].

# Solution

## Idea

hash table, exchange space complexity for time complexity (instant search with `O(1)`)

use x's complements as key, x's index as value

time complexity: `O(n)`

space complexity: `O(n)`

## Code

```
class Solution:
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        
        table = dict()
        for i in range(len(nums)):
            if nums[i] in table:
                return [table[nums[i]], i]
            complement = target - nums[i]
            table[complement] = i
```