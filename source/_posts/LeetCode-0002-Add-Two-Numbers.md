---
title: "[LeetCode] 0002. Add Two Numbers [Medium]"
date: 2021-06-15 02:24:55
categories: leetcode
tags:
  - leetcode
  - linked-list
  - math
keywords: leetcode
description: "[LeetCode] 0002. Add Two Numbers [Medium]"
abbrlink: 1c0002
---



[Add Two Numbers - LeetCode](https://leetcode.com/problems/add-two-numbers/)



### While

```python
# Time: O(n)
# Space: O(n)
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        dummy = ListNode(0)
        head = dummy
        sum = 0
        while l1 or l2:
            if l1:
                sum += l1.val
                l1 = l1.next
            if l2:
                sum += l2.val
                l2 = l2.next
            head.next = ListNode(sum % 10)
            sum //= 10
            head = head.next
        if 1 == sum:
            head.next = ListNode(1)
        return dummy.next

```



### Recursive

```python
# Time: O(n)
# Space: O(n)
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        if not l1: return l2
        if not l2: return l1

        target = l1.val + l2.val
        res = ListNode(target % 10)
        res.next = self.addTwoNumbers(l1.next, l2.next)

        if 1 == target // 10:
            res.next = self.addTwoNumbers(res.next, ListNode(1))

        return res
```



### Next Challs

- [Multiply Strings](https://leetcode.com/problems/multiply-strings/) - Medium
- [Add Binary](https://leetcode.com/problems/add-binary/) - Easy
- [Sum of Two Integers](https://leetcode.com/problems/sum-of-two-integers/) - Medium
- [Add Strings](https://leetcode.com/problems/add-strings/) - Easy
- [Add Two Numbers II](https://leetcode.com/problems/add-two-numbers-ii/) - Medium
- [Add to Array-Form of Integer](https://leetcode.com/problems/add-to-array-form-of-integer/) - Easy
- [Add Two Polynomials Represented as Linked Lists](https://leetcode.com/problems/add-two-polynomials-represented-as-linked-lists/) -Medium

