# Arrays
An array is a collection of values of the same data type stored in contiguous memory locations.

## Advantages
- **Random Access**: Allows accessing any element in O(1) time.
- **Cache Friendly**: When an element is accessed from memory to cache, pre-processors often fetch nearby elements. Arrays benefit from this as their elements are stored in contiguous memory.

## Categories of Arrays Based on Size

### 1. Fixed-Size Arrays (Static Arrays)
- **Characteristics**:
  - The size is fixed and cannot be changed once declared.
  **Code Examples in C++**:
    ```cpp
    int arr[100];          // Fixed size
    int arr[n];            // Size determined at runtime (if supported by the compiler)
    int *arr = new int[100]; // Dynamically allocated
    int arr[] = {1, 2, 3}; // Initialization with predefined values
  -  Allocated memory generally in 2 ways
       - Area in Heap Segement(Dynamically Allocated)
           ```cpp
            new int[n];
       - Area in Stack Segment(Static)
    All other ways of creating arrays as shown above
 
### 2. Dynamic Size Array
- **Characteristics**:
  - Resizes themselves automatically.
    - Ex: C++ vectors, Python Lists, Java ArrayList
    - Initally when initialized some space is given say 50 cells and once if it reaches 50. It will allocate double the space and move the elements to newly allocated location. The amortized complexity is still O(1).


   
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
