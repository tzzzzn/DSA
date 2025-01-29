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
  -  Allocated memory generally in two ways
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

## C++
```cpp
#include<bits/stdc++.h>
using namespace std;
int main()
{
    // Integer Array Initiallization
    int arr1[5]={1,2,3,4,5};
    int arr2[5]; // Uninitialized Garbage Values
    int arr3[5]={1,3};// Partially initialized, rest are intiallized to 0.
    int *arr6 = new int[10]; // Initialized 10 elements with 0 value, as it is uninitialized.
    int *arr7 = new int(10); // Initialized with one value i.e 10. And this is not an array.
    delete[] arr6; // For arrays
    delete arr7;   // For a single integer

    //String or Char array
    char *arr4 = "Hello"; //Null terminated string '\0' so string size will be 6.
    char arr5[]="Hello";

    // Size of Array
    cout<<sizeof(arr5)/sizeof(arr5[0]);

    // Vector intialization
    vector<int> a;
    vector<int> b(5,10); // creates a vectors of size 5, all elements initialized to 10.
    vector<int> v={1,2,3,4,5};
    vector<vector<int>> matrix(3, vector<int>(4, 0));  // 3x4 matrix initialized with 0
    // Insertion
    a.push_back(10);
    a.push_back(11);
    // Deletion
    a.pop_back();
    a.pop_back();
    // Size
    cout<<a.size();//returns integer size of the array.
    // Reverse
    reverse(a.begin(), a.end());
    // Last Element
    cout<<a.back();
    // Sort
    sort(a.begin(),a.end());
    
    // Iteration
    for(int i:v)
        cout<<i<<" "; // prints all elements
    // Iteration of iterators we can apply this to any other Data structures like maps, sets,..etc
    for(auto it = v.begin(); it != v.end(); ++it)
    cout << *it << " ";
}
```

#### Custom Sort function
```cpp
#include <bits/stdc++.h>
using namespace std;

// Custom comparator for descending order
bool comp(int a, int b) {
      return a > b;
}

int main() {
    int arr[5] = {5, 3, 2, 1, 4};
      int n = sizeof(arr)/sizeof(arr[0]);

    // Sort array in descending order
    sort(arr, arr + n, comp);

    for (int i : arr)
        cout << i << " ";
    return 0;
}
```
## Python
```python
# In python lists are dynamic and can store different data types.
l = [] # list initialized 
l.append(5) # inserting element at the end.
l.pop() # removes last elment.
numbers = [1, 3, 4, 2]
numbers.sort()
numbers.sort(reverse=True)

def sortSecond(val):
    return val[1] 
list1 = [(1,2),(3,3),(1,1)]
# sorts the array in ascending according to 
# second element 
list1.sort(key=sortSecond) 
print(list1)
# In python sort the key only returns the value and it will be sorted in ascending order 
# say if we have more than one comparison then we have to 

arr = [(1, 5, 2), (3, 3, 2), (2, 4, 3), (1, 2, 3), (4, 1, 3)]
# Sorting by third element, then second, then first
arr.sort(key=lambda x: (x[2], x[1], x[0]))
# Sorting by third element (ascending), then second element (descending), then first element (ascending)
arr.sort(key=lambda x: (x[2], -x[1], x[0]))
```

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
