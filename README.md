# Ethan Cornwill T2A1 - Workbook Part B

## Q1 Identify and explain the workings of TWO sorting algorithms and discuss and compare their performance/efficiency (i.e. Big O)

### Bogo Sort

Bogo sort, also known as permutation sort, stupid sort, slow sort, shotgun sort, or monkey sort, is a highly inefficient sorting algorithm. It is based on the generate-and-test paradigm, where the algorithm generates permutations of its input until it finds one that is sorted.

The process of bogo sort can be likened to sorting a deck of cards by throwing them into the air, picking them up at random, and repeating the process until the deck is sorted. The algorithm works as follows:

- Generate a random permutation of the input list.
- Check if the list is sorted.
- If the list is sorted, return it.
- If the list is not sorted, go back to step 1 and repeat.
- The pseudocode for bogo sort is quite simple:

```py
while not is_sorted(list):
    shuffle(list)
```

Despite its simplicity, bogo sort is extremely inefficient. Its average time complexity is `O(n x n!)`, where `(n)` is the number of elements in the list. This is because there are `(n!)` possible permutations of a list of `(n)` elements, and on average, the algorithm will need to generate about half of these permutations before finding the sorted one. In the worst case, the time complexity is unbounded, meaning the algorithm could theoretically run forever if it never happens to generate the sorted permutation.

Bogo sort is not used in practice due to its inefficiency. It is often presented as a humorous example of a bad algorithm and is used to emphasize the importance of using efficient sorting algorithms for practical purposes. The name “bogo” is derived from the words “bogus” and “go,” indicating the randomness and inefficiency of this algorithm.

https://www.geeksforgeeks.org/bogosort-permutation-sort/
https://www.educative.io/answers/what-is-bogo-sort
https://web.archive.org/web/20131210012102/http://richardhartersworld.com/cri_d/cri/2001/badsort.html

### Bubble Sort

Bubble sort is one of the simplest sorting algorithms, often used as an introductory example in computer science courses. It works by repeatedly stepping through the list to be sorted, comparing each pair of adjacent items and swapping them if they are in the wrong order. This process is repeated until the list is sorted.

The algorithm can be described in the following steps:

- Start at the beginning of the list.
- Compare the first two elements. If the first is greater than the second, swap them.
- Move to the next pair of elements, compare them, and swap if necessary.
- Continue this process for each pair of adjacent elements to the end of the list. This completes one pass.
- Repeat the process for the entire list until no swaps are needed during a pass, indicating that the list is sorted.

#### Example

Consider the list `[5, 1, 4, 2, 8]`

##### First Pass

- Compare 5 and 1, swap: `[1, 5, 4, 2, 8]`
- Compare 5 and 4, swap: `[1, 4, 5, 2, 8]`
- Compare 5 and 2, swap: `[1, 4, 2, 5, 8]`
- Compare 5 and 8, no swap: `[1, 4, 2, 5, 8]`

##### Second Pass

- Compare 1 and 4, no swap: `[1, 4, 2, 5, 8]`
- Compare 4 and 2, swap: `[1, 2, 4, 5, 8]`
- Compare 4 and 5, no swap: `[1, 2, 4, 5, 8]`
- Compare 5 and 8, no swap: `[1, 2, 4, 5, 8]`

##### Third Pass

- Compare 1 and 2, no swap: `[1, 2, 4, 5, 8]`
- Compare 2 and 4, no swap: `[1, 2, 4, 5, 8]`
- Compare 4 and 5, no swap: `[1, 2, 4, 5, 8]`
- Compare 5 and 8, no swap: `[1, 2, 4, 5, 8]`

Since no swaps were needed in the third pass, the list is sorted.

Bubble sort has a worst-case and average-case time complexity of `O(n^2)`, where `(n)` is the number of items being sorted. This makes it inefficient for large lists. However, it has a best-case time complexity of `O(n)` when the list is already sorted, as it only needs one pass to confirm the order.

```py
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        swapped = False
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
                swapped = True
        if not swapped:
            break
```

https://www.geeksforgeeks.org/bubble-sort-algorithm/
https://www.freecodecamp.org/news/bubble-sort/
https://www.programiz.com/dsa/bubble-sort

### Comparison

Let’s compare the performance and efficiency of Bogo sort and Bubble sort, focusing on their time complexity, practical use cases, and overall efficiency.

#### Time Complexity

##### Bogo Sort

- **Average Case:** `O(n x n!)`
- **Worst Case:** Unbounded (theoretically could run forever)
- **Best Case:** `O(n)` (if the list is already sorted and the first permutation is correct)

##### Bubble Sort

- **Average Case:** `O(n^2)`
- **Worst Case:** `O(n^2)`
- **Best Case:** `O(n)` (if the list is already sorted)

#### Practical Use Cases

##### Bogo Sort

- **Educational Tool:** Used to illustrate the concept of inefficient algorithms.
- **Humour:** Often cited as a joke in computer science due to its impracticality.
- **Theoretical Interest:** Sometimes discussed in theoretical computer science to understand the limits of algorithm efficiency.

##### Bubble Sort

- **Educational Tool:** Commonly used to teach the basics of sorting algorithms.
- **Small Datasets:** Can be used for small lists where performance is not a critical concern.
- **Stability:** Maintains the relative order of equal elements, which can be useful in certain applications.

#### Efficiency

##### Bogo Sort

- **Highly Inefficient:** Due to its reliance on generating random permutations, it is extremely slow and impractical for any real-world use.
- **Unpredictable**: The time it takes to sort a list can vary wildly, making it unreliable.
- **Optimisable**: Can be optimised by removing already checked permutations, rather than randomly generating the same permutations over and over again.

##### Bubble Sort

- **Inefficient for Large Lists:** With a time complexity of `O(n^2)`, it becomes impractical for large datasets.
- **Predictable:** The number of comparisons and swaps is more predictable compared to Bogo sort.
- **Optimsable:** Can be slightly optimised by stopping early if no swaps are made during a pass.

While both Bogo sort and Bubble sort are not suitable for large-scale sorting tasks, Bubble sort is significantly more practical and predictable. Bogo sort serves as a cautionary example of inefficiency, while Bubble sort, despite its limitations, can be useful in specific scenarios and is a good starting point for learning about sorting algorithms.

## Q2 Identify and explain the workings of TWO search algorithms and discuss and compare their performance/efficiency (i.e. Big O)

### Binary Search

Binary search is an efficient algorithm for finding the position of a target value within a sorted array. It operates on the principle of divide and conquer, significantly reducing the number of comparisons needed to find the target value compared to linear search.

#### How Binary Search Works

- **Initial Setup:** Start with two pointers, `low` and `high`, which represent the range of indices in the array. Initially, `low` is set to the first index `(0)` and `high` is set to the last index `(n-1)`.
- **Finding the Middle:** Calculate the middle index `mid` using the formula: `mid = low + (high - low) / 2`. This formula ensures that the middle index is correctly calculated even for large values of `low` and `high`.
- **Comparison:**
  - If the middle element is the target: Return the index `mid`.
  - If the target is less than the middle element: Narrow the search to the left half by setting high to `mid - 1`.
  - If the target is greater than the middle element: Narrow the search to the right half by setting `low` to `mid + 1`.
- **Repeat:** Continue the process until `low` exceeds `high`. If `low` exceeds `high` and the target has not been found, it means the target is not in the array.

#### Example

Consider the sorted array `[2, 5, 8, 12, 16, 23, 38, 56, 72, 91]` and the target value `23`

- Initial pointers: `low = 0`, `high = 9`

##### First iteration

- Calculate `mid = (0 + 9) / 2 = 4`
- Compare `array[4] = 16` with `23`
- Since`23 > 16`, set `low = 5`

##### Second iteration

- Calculate `mid = (5 + 9) / 2 = 7`
- Compare `array[7] = 56` with `23`
- Since `23 < 56`, set `high = 6`

##### Third iteration

- Calculate mid = `(5 + 6) / 2 = 5`
- Compare `array[5] = 23` with `23`
- Target found at index `5`

#### Time Complexity

Binary search has a time complexity of `O(log n)`, where `(n)` is the number of elements in the array. This logarithmic time complexity makes binary search much more efficient than other search algorithms, especially for large datasets.

#### Implementation
Here is a simple implementation of binary search in Python:

``` py
def binary_search(arr, target):
    low, high = 0, len(arr) - 1
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            low = mid + 1
        else:
            high = mid - 1
    return -1
```

In summary, binary search is a powerful and efficient algorithm for searching in sorted arrays, leveraging the divide and conquer strategy to achieve logarithmic time complexity.

https://www.geeksforgeeks.org/binary-search/
https://www.programiz.com/dsa/binary-search
https://www.freecodecamp.org/news/what-is-binary-search/
https://brilliant.org/wiki/binary-search/

### Linear Search

Linear search, also known as sequential search, is one of the simplest searching algorithms. It works by checking each element of a list one by one until the desired element is found or the list ends. This method is straightforward and easy to implement, making it a good starting point for understanding search algorithms.

#### How Linear Search Works

- **Start at the Beginning:** Begin with the first element of the list.
- **Compare Each Element:** Compare the current element with the target value.
- **Check for Match:**
  - If the current element matches the target, return its index.
  - If it does not match, move to the next element.
- **Repeat:** Continue this process until the target is found or the end of the list is reached.
- **End of List:** If the end of the list is reached without finding the target, return an indication that the target is not present in the list.

#### Example

Consider the list `[10, 50, 30, 70, 80, 20, 90, 40]` and the target value `30`:

- First Element: Compare `10` with `30` (no match).
- Second Element: Compare `50` with `30` (no match).
- Third Element: Compare `30` with `30` (match found).
- The target `30` is found at index `2`.

#### Time Complexity

Linear search has a time complexity of `O(n)`, where `(n)` is the number of elements in the list. This means that in the worst case, the algorithm will have to check every element in the list. The best case occurs when the target is the first element, resulting in a time complexity of `O(1)`.

#### Implementation

Here is a simple implementation of linear search in Python:

```py
def linear_search(arr, target):
    for index, element in enumerate(arr):
        if element == target:
            return index
    return -1
```

https://www.geeksforgeeks.org/linear-search/
https://www.codingdrills.com/tutorial/introduction-to-searching-algorithms/linear-search
https://www.bbc.co.uk/bitesize/guides/zjdkw6f/revision/3


### Comparison

Let’s delve deeper into the comparison between Linear Search and Binary Search, focusing on various aspects such as time complexity, space complexity, use cases, and practical considerations.

#### Time Complexity

##### Linear Search

- **Worst Case:** `O(n)` - The target element is at the end of the list or not present.
- **Best Case:** `O(1)` - The target element is the first element in the list.
- **Average Case:** `O(n)` - On average, half of the elements need to be checked.

##### Binary Search:

- **Worst Case:** `O(log n)` - The target element is found after repeatedly halving the list.
- **Best Case:** `O(1)` - The target element is the middle element on the first check.
- **Average Case:** `O(log n)` - On average, the search space is halved with each step.

#### Space Complexity

##### Linear Search:

- **Space Complexity:** **(O(1))** - Only a constant amount of extra space is needed, regardless of the list size.

##### Binary Search:

- **Space Complexity:** `O(1)` - Similar to linear search, it requires a constant amount of extra space.

#### Use Cases

##### Linear Search:

- **Unsorted Lists:** Can be used on both sorted and unsorted lists.
- **Small Lists:** Efficient for small datasets where the overhead of sorting is not justified.
- **Linked Lists:** Suitable for data structures where random access is not possible.

##### Binary Search:

- **Sorted Lists:** Requires the list to be sorted beforehand.
- **Large Lists**: Much more efficient for large datasets due to its logarithmic time complexity.
- **Random Access:** Best suited for data structures that allow random access, such as arrays.

#### Practical Considerations

##### Linear Search:

- **Simplicity:** Very easy to implement and understand.
- **Versatility:** Can be applied to any list, regardless of whether it is sorted.
- **Performance:** Inefficient for large datasets due to its linear time complexity.

##### Binary Search:

- **Efficiency:** Highly efficient for large, sorted datasets.
- **Pre-sorting Requirement:** The list must be sorted, which can add to the overall time complexity if sorting is needed.
- **Implementation:** Slightly more complex to implement compared to linear search but still straightforward.

#### Example Scenarios

##### Linear Search

- **Finding a Name in an Unsorted List:** If you have a list of names and need to find a specific one, linear search is straightforward and doesn’t require sorting the list first.
- **Checking for Existence:** Useful when you need to check if an element exists in a list without caring about the order.

##### Binary Search

- **Dictionary Lookup:** Efficient for looking up words in a sorted dictionary.
- **Database Indexing:** Often used in databases where data is indexed and sorted, allowing for quick searches.

Linear Search is simple, versatile, and works on any list, but it is inefficient for large datasets. It is best used for small or unsorted lists and when simplicity is a priority.

Binary Search is highly efficient for large, sorted datasets, offering logarithmic time complexity. It requires the list to be sorted, making it less versatile but much faster for large-scale searches.