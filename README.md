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

Python

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

Bubble sort has a worst-case and average-case time complexity of `O(n^2)`, where `(n)` is the number of items being sorted1. This makes it inefficient for large lists. However, it has a best-case time complexity of `O(n)` when the list is already sorted, as it only needs one pass to confirm the order.

Python

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

Minimum 300 words

### Binary Search

Binary search is a search algorithm that works by repeatedly dividing the search space in half.

### Linear Search

Linear search is a search algorithm that works by sequentially comparing each element in the search space.
