---
title: "[LeetCode] 0001. Two Sum [Easy]"
date: 2021-06-15 01:51:55
categories: leetcode
tags:
  - leetcode
  - array
  - hash table
keywords: leetcode
description: "[LeetCode] 0001. Two Sum [Easy]"
abbrlink: 1c0001
---



[Two Sum - LeetCode](https://leetcode.com/problems/two-sum/)



### Two Loops - Time Limit Exceeded

```python
# Time: O(n²)
# Space: O(1)
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i, x in enumerate(nums):
            for j, y in enumerate(nums):
                if j > i and x + y == target:
                    return [i, j]
        return [None, None]
```



### One Loop with index

```python
# Time: O(n²)
# Space: O(1)
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for idx, num in enumerate(nums):
            if target - num in nums[idx+1:]:
              	idx2 = idx + 1 + nums[idx+1:].index(target - num)
              	return [idx, idx2]
        return [None, None]
```



### Hash Table 1

```python
# Time: O(n)
# Space: O(n)
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hash_table = {}
        for idx, num in enumerate(nums):
            hash_table[num] = idx
        # hash_table = {num: idx for idx, num in enumerate(nums)}
        for idx, num in enumerate(nums):
            if target - num in hash_table and hash_table[target - num] != idx:
                return [idx, hash_table[target - num]]
        return [None, None]

```



### Hash Table 2

```python
# Time: O(n)
# Space: O(n)
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hash_table = {}
        for idx, num in enumerate(nums):
            if target - num in hash_table:
                return [hash_table[target - num], idx]
            hash_table[num] = idx
        return [None, None]
```



### Next Challs

- [3Sum](https://leetcode.com/problems/3sum/) - Medium
- [4Sum](https://leetcode.com/problems/4sum/) - Medium
- [Two Sum II - Input array is sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/) - Easy
- [Two Sum III - Data structure design](https://leetcode.com/problems/two-sum-iii-data-structure-design/) - Easy
- [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/) - Medium
- [Two Sum IV - Input is a BST](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/) - Easy
- [Two Sum Less Than K](https://leetcode.com/problems/two-sum-less-than-k/) - Easy
- [Max Number of K-Sum Pairs](https://leetcode.com/problems/max-number-of-k-sum-pairs/) - Medium
- [Count Good Meals](https://leetcode.com/problems/count-good-meals/) - Medium

