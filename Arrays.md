# Arrays
# Coding Problem: Two Sum

<details>
<summary>Question</summary>

Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

</details>

<details>
<summary>Hints</summary>

1. Think about using a hash table to store the numbers you've seen so far.
2. Check if the complement (target - current number) exists in the hash table.
3. Focus on achieving O(n) time complexity.

</details>

<details>
<summary>Approach 1</summary>

**Using a Hash Map:**

```python
def two_sum(nums, target):
    seen = {}
    for i, num in enumerate(nums):
        complement = target - num
        if complement in seen:
            return [seen[complement], i]
        seen[num] = i
