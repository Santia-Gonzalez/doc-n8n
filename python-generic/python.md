================================================
File: README.md
================================================
Implementations are for learning purposes only. They may be less efficient than the implementations in the Python standard library. Use them at your discretion.

## Getting Started

Read through our [Contribution Guidelines](CONTRIBUTING.md) before you contribute.

## Community Channels

We are on [Discord](https://the-algorithms.com/discord) and [Gitter](https://gitter.im/TheAlgorithms/community)! Community channels are a great way for you to ask questions and get help. Please join us!

## List of Algorithms

See our [directory](DIRECTORY.md) for easier navigation and a better overview of the project.


================================================
File: data_structures/arrays/equilibrium_index_in_array.py
================================================
"""
Find the Equilibrium Index of an Array.
Reference: https://www.geeksforgeeks.org/equilibrium-index-of-an-array/

Python doctest can be run with the following command:
python -m doctest -v equilibrium_index_in_array.py

Given a sequence arr[] of size n, this function returns
an equilibrium index (if any) or -1 if no equilibrium index exists.

The equilibrium index of an array is an index such that the sum of
elements at lower indexes is equal to the sum of elements at higher indexes.



Example Input:
arr = [-7, 1, 5, 2, -4, 3, 0]
Output: 3

"""


def equilibrium_index(arr: list[int]) -> int:
    """
    Find the equilibrium index of an array.

    Args:
        arr (list[int]): The input array of integers.

    Returns:
        int: The equilibrium index or -1 if no equilibrium index exists.

    Examples:
        >>> equilibrium_index([-7, 1, 5, 2, -4, 3, 0])
        3
        >>> equilibrium_index([1, 2, 3, 4, 5])
        -1
        >>> equilibrium_index([1, 1, 1, 1, 1])
        2
        >>> equilibrium_index([2, 4, 6, 8, 10, 3])
        -1
    """
    total_sum = sum(arr)
    left_sum = 0

    for i, value in enumerate(arr):
        total_sum -= value
        if left_sum == total_sum:
            return i
        left_sum += value

    return -1


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/arrays/find_triplets_with_0_sum.py
================================================
from itertools import combinations


def find_triplets_with_0_sum(nums: list[int]) -> list[list[int]]:
    """
    Given a list of integers, return elements a, b, c such that a + b + c = 0.
    Args:
        nums: list of integers
    Returns:
        list of lists of integers where sum(each_list) == 0
    Examples:
        >>> find_triplets_with_0_sum([-1, 0, 1, 2, -1, -4])
        [[-1, -1, 2], [-1, 0, 1]]
        >>> find_triplets_with_0_sum([])
        []
        >>> find_triplets_with_0_sum([0, 0, 0])
        [[0, 0, 0]]
        >>> find_triplets_with_0_sum([1, 2, 3, 0, -1, -2, -3])
        [[-3, 0, 3], [-3, 1, 2], [-2, -1, 3], [-2, 0, 2], [-1, 0, 1]]
    """
    return [
        list(x)
        for x in sorted({abc for abc in combinations(sorted(nums), 3) if not sum(abc)})
    ]


def find_triplets_with_0_sum_hashing(arr: list[int]) -> list[list[int]]:
    """
    Function for finding the triplets with a given sum in the array using hashing.

    Given a list of integers, return elements a, b, c such that a + b + c = 0.

    Args:
        nums: list of integers
    Returns:
        list of lists of integers where sum(each_list) == 0
    Examples:
        >>> find_triplets_with_0_sum_hashing([-1, 0, 1, 2, -1, -4])
        [[-1, 0, 1], [-1, -1, 2]]
        >>> find_triplets_with_0_sum_hashing([])
        []
        >>> find_triplets_with_0_sum_hashing([0, 0, 0])
        [[0, 0, 0]]
        >>> find_triplets_with_0_sum_hashing([1, 2, 3, 0, -1, -2, -3])
        [[-1, 0, 1], [-3, 1, 2], [-2, 0, 2], [-2, -1, 3], [-3, 0, 3]]

    Time complexity: O(N^2)
    Auxiliary Space: O(N)

    """
    target_sum = 0

    # Initialize the final output array with blank.
    output_arr = []

    # Set the initial element as arr[i].
    for index, item in enumerate(arr[:-2]):
        # to store second elements that can complement the final sum.
        set_initialize = set()

        # current sum needed for reaching the target sum
        current_sum = target_sum - item

        # Traverse the subarray arr[i+1:].
        for other_item in arr[index + 1 :]:
            # required value for the second element
            required_value = current_sum - other_item

            # Verify if the desired value exists in the set.
            if required_value in set_initialize:
                # finding triplet elements combination.
                combination_array = sorted([item, other_item, required_value])
                if combination_array not in output_arr:
                    output_arr.append(combination_array)

            # Include the current element in the set
            # for subsequent complement verification.
            set_initialize.add(other_item)

    # Return all the triplet combinations.
    return output_arr


if __name__ == "__main__":
    from doctest import testmod

    testmod()


================================================
File: data_structures/arrays/index_2d_array_in_1d.py
================================================
"""
Retrieves the value of an 0-indexed 1D index from a 2D array.
There are two ways to retrieve value(s):

1. Index2DArrayIterator(matrix) -> Iterator[int]
This iterator allows you to iterate through a 2D array by passing in the matrix and
calling next(your_iterator). You can also use the iterator in a loop.
Examples:
list(Index2DArrayIterator(matrix))
set(Index2DArrayIterator(matrix))
tuple(Index2DArrayIterator(matrix))
sum(Index2DArrayIterator(matrix))
-5 in Index2DArrayIterator(matrix)

2. index_2d_array_in_1d(array: list[int], index: int) -> int
This function allows you to provide a 2D array and a 0-indexed 1D integer index,
and retrieves the integer value at that index.

Python doctests can be run using this command:
python3 -m doctest -v index_2d_array_in_1d.py
"""

from collections.abc import Iterator
from dataclasses import dataclass


@dataclass
class Index2DArrayIterator:
    matrix: list[list[int]]

    def __iter__(self) -> Iterator[int]:
        """
        >>> tuple(Index2DArrayIterator([[5], [-523], [-1], [34], [0]]))
        (5, -523, -1, 34, 0)
        >>> tuple(Index2DArrayIterator([[5, -523, -1], [34, 0]]))
        (5, -523, -1, 34, 0)
        >>> tuple(Index2DArrayIterator([[5, -523, -1, 34, 0]]))
        (5, -523, -1, 34, 0)
        >>> t = Index2DArrayIterator([[5, 2, 25], [23, 14, 5], [324, -1, 0]])
        >>> tuple(t)
        (5, 2, 25, 23, 14, 5, 324, -1, 0)
        >>> list(t)
        [5, 2, 25, 23, 14, 5, 324, -1, 0]
        >>> sorted(t)
        [-1, 0, 2, 5, 5, 14, 23, 25, 324]
        >>> tuple(t)[3]
        23
        >>> sum(t)
        397
        >>> -1 in t
        True
        >>> t = iter(Index2DArrayIterator([[5], [-523], [-1], [34], [0]]))
        >>> next(t)
        5
        >>> next(t)
        -523
        """
        for row in self.matrix:
            yield from row


def index_2d_array_in_1d(array: list[list[int]], index: int) -> int:
    """
    Retrieves the value of the one-dimensional index from a two-dimensional array.

    Args:
        array: A 2D array of integers where all rows are the same size and all
               columns are the same size.
        index: A 1D index.

    Returns:
        int: The 0-indexed value of the 1D index in the array.

    Examples:
    >>> index_2d_array_in_1d([[0, 1, 2, 3], [4, 5, 6, 7], [8, 9, 10, 11]], 5)
    5
    >>> index_2d_array_in_1d([[0, 1, 2, 3], [4, 5, 6, 7], [8, 9, 10, 11]], -1)
    Traceback (most recent call last):
        ...
    ValueError: index out of range
    >>> index_2d_array_in_1d([[0, 1, 2, 3], [4, 5, 6, 7], [8, 9, 10, 11]], 12)
    Traceback (most recent call last):
        ...
    ValueError: index out of range
    >>> index_2d_array_in_1d([[]], 0)
    Traceback (most recent call last):
        ...
    ValueError: no items in array
    """
    rows = len(array)
    cols = len(array[0])

    if rows == 0 or cols == 0:
        raise ValueError("no items in array")

    if index < 0 or index >= rows * cols:
        raise ValueError("index out of range")

    return array[index // cols][index % cols]


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/arrays/kth_largest_element.py
================================================
"""
Given an array of integers and an integer k, find the kth largest element in the array.

https://stackoverflow.com/questions/251781
"""


def partition(arr: list[int], low: int, high: int) -> int:
    """
    Partitions list based on the pivot element.

    This function rearranges the elements in the input list 'elements' such that
    all elements greater than or equal to the chosen pivot are on the right side
    of the pivot, and all elements smaller than the pivot are on the left side.

    Args:
        arr: The list to be partitioned
        low: The lower index of the list
        high: The higher index of the list

    Returns:
        int: The index of pivot element after partitioning

        Examples:
        >>> partition([3, 1, 4, 5, 9, 2, 6, 5, 3, 5], 0, 9)
        4
        >>> partition([7, 1, 4, 5, 9, 2, 6, 5, 8], 0, 8)
        1
        >>> partition(['apple', 'cherry', 'date', 'banana'], 0, 3)
        2
        >>> partition([3.1, 1.2, 5.6, 4.7], 0, 3)
        1
    """
    pivot = arr[high]
    i = low - 1
    for j in range(low, high):
        if arr[j] >= pivot:
            i += 1
            arr[i], arr[j] = arr[j], arr[i]
    arr[i + 1], arr[high] = arr[high], arr[i + 1]
    return i + 1


def kth_largest_element(arr: list[int], position: int) -> int:
    """
    Finds the kth largest element in a list.
    Should deliver similar results to:
    ```python
    def kth_largest_element(arr, position):
        return sorted(arr)[-position]
    ```

    Args:
        nums: The list of numbers.
        k: The position of the desired kth largest element.

    Returns:
        int: The kth largest element.

    Examples:
        >>> kth_largest_element([3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5], 3)
        5
        >>> kth_largest_element([2, 5, 6, 1, 9, 3, 8, 4, 7, 3, 5], 1)
        9
        >>> kth_largest_element([2, 5, 6, 1, 9, 3, 8, 4, 7, 3, 5], -2)
        Traceback (most recent call last):
        ...
        ValueError: Invalid value of 'position'
        >>> kth_largest_element([9, 1, 3, 6, 7, 9, 8, 4, 2, 4, 9], 110)
        Traceback (most recent call last):
        ...
        ValueError: Invalid value of 'position'
        >>> kth_largest_element([1, 2, 4, 3, 5, 9, 7, 6, 5, 9, 3], 0)
        Traceback (most recent call last):
        ...
        ValueError: Invalid value of 'position'
        >>> kth_largest_element(['apple', 'cherry', 'date', 'banana'], 2)
        'cherry'
        >>> kth_largest_element([3.1, 1.2, 5.6, 4.7,7.9,5,0], 2)
        5.6
        >>> kth_largest_element([-2, -5, -4, -1], 1)
        -1
        >>> kth_largest_element([], 1)
        -1
        >>> kth_largest_element([3.1, 1.2, 5.6, 4.7, 7.9, 5, 0], 1.5)
        Traceback (most recent call last):
        ...
        ValueError: The position should be an integer
        >>> kth_largest_element((4, 6, 1, 2), 4)
        Traceback (most recent call last):
        ...
        TypeError: 'tuple' object does not support item assignment
    """
    if not arr:
        return -1
    if not isinstance(position, int):
        raise ValueError("The position should be an integer")
    if not 1 <= position <= len(arr):
        raise ValueError("Invalid value of 'position'")
    low, high = 0, len(arr) - 1
    while low <= high:
        if low > len(arr) - 1 or high < 0:
            return -1
        pivot_index = partition(arr, low, high)
        if pivot_index == position - 1:
            return arr[pivot_index]
        elif pivot_index > position - 1:
            high = pivot_index - 1
        else:
            low = pivot_index + 1
    return -1


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/arrays/median_two_array.py
================================================
"""
https://www.enjoyalgorithms.com/blog/median-of-two-sorted-arrays
"""


def find_median_sorted_arrays(nums1: list[int], nums2: list[int]) -> float:
    """
    Find the median of two arrays.

    Args:
        nums1: The first array.
        nums2: The second array.

    Returns:
    The median of the two arrays.

    Examples:
        >>> find_median_sorted_arrays([1, 3], [2])
        2.0

        >>> find_median_sorted_arrays([1, 2], [3, 4])
        2.5

        >>> find_median_sorted_arrays([0, 0], [0, 0])
        0.0

        >>> find_median_sorted_arrays([], [])
        Traceback (most recent call last):
            ...
        ValueError: Both input arrays are empty.

        >>> find_median_sorted_arrays([], [1])
        1.0

        >>> find_median_sorted_arrays([-1000], [1000])
        0.0

        >>> find_median_sorted_arrays([-1.1, -2.2], [-3.3, -4.4])
        -2.75
    """
    if not nums1 and not nums2:
        raise ValueError("Both input arrays are empty.")

    # Merge the arrays into a single sorted array.
    merged = sorted(nums1 + nums2)
    total = len(merged)

    if total % 2 == 1:  # If the total number of elements is odd
        return float(merged[total // 2])  # then return the middle element

    # If the total number of elements is even, calculate
    # the average of the two middle elements as the median.
    middle1 = merged[total // 2 - 1]
    middle2 = merged[total // 2]
    return (float(middle1) + float(middle2)) / 2.0


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/arrays/monotonic_array.py
================================================
# https://leetcode.com/problems/monotonic-array/
def is_monotonic(nums: list[int]) -> bool:
    """
    Check if a list is monotonic.

    >>> is_monotonic([1, 2, 2, 3])
    True
    >>> is_monotonic([6, 5, 4, 4])
    True
    >>> is_monotonic([1, 3, 2])
    False
    >>> is_monotonic([1,2,3,4,5,6,5])
    False
    >>> is_monotonic([-3,-2,-1])
    True
    >>> is_monotonic([-5,-6,-7])
    True
    >>> is_monotonic([0,0,0])
    True
    >>> is_monotonic([-100,0,100])
    True
    """
    return all(nums[i] <= nums[i + 1] for i in range(len(nums) - 1)) or all(
        nums[i] >= nums[i + 1] for i in range(len(nums) - 1)
    )


# Test the function with your examples
if __name__ == "__main__":
    # Test the function with your examples
    print(is_monotonic([1, 2, 2, 3]))  # Output: True
    print(is_monotonic([6, 5, 4, 4]))  # Output: True
    print(is_monotonic([1, 3, 2]))  # Output: False

    import doctest

    doctest.testmod()


================================================
File: data_structures/arrays/pairs_with_given_sum.py
================================================
#!/usr/bin/env python3

"""
Given an array of integers and an integer req_sum, find the number of pairs of array
elements whose sum is equal to req_sum.

https://practice.geeksforgeeks.org/problems/count-pairs-with-given-sum5022/0
"""

from itertools import combinations


def pairs_with_sum(arr: list, req_sum: int) -> int:
    """
    Return the no. of pairs with sum "sum"
    >>> pairs_with_sum([1, 5, 7, 1], 6)
    2
    >>> pairs_with_sum([1, 1, 1, 1, 1, 1, 1, 1], 2)
    28
    >>> pairs_with_sum([1, 7, 6, 2, 5, 4, 3, 1, 9, 8], 7)
    4
    """
    return len([1 for a, b in combinations(arr, 2) if a + b == req_sum])


if __name__ == "__main__":
    from doctest import testmod

    testmod()


================================================
File: data_structures/arrays/permutations.py
================================================
def permute_recursive(nums: list[int]) -> list[list[int]]:
    """
    Return all permutations.

    >>> permute_recursive([1, 2, 3])
    [[3, 2, 1], [2, 3, 1], [1, 3, 2], [3, 1, 2], [2, 1, 3], [1, 2, 3]]
    """
    result: list[list[int]] = []
    if len(nums) == 0:
        return [[]]
    for _ in range(len(nums)):
        n = nums.pop(0)
        permutations = permute_recursive(nums.copy())
        for perm in permutations:
            perm.append(n)
        result.extend(permutations)
        nums.append(n)
    return result


def permute_backtrack(nums: list[int]) -> list[list[int]]:
    """
    Return all permutations of the given list.

    >>> permute_backtrack([1, 2, 3])
    [[1, 2, 3], [1, 3, 2], [2, 1, 3], [2, 3, 1], [3, 2, 1], [3, 1, 2]]
    """

    def backtrack(start: int) -> None:
        if start == len(nums) - 1:
            output.append(nums[:])
        else:
            for i in range(start, len(nums)):
                nums[start], nums[i] = nums[i], nums[start]
                backtrack(start + 1)
                nums[start], nums[i] = nums[i], nums[start]  # backtrack

    output: list[list[int]] = []
    backtrack(0)
    return output


if __name__ == "__main__":
    import doctest

    result = permute_backtrack([1, 2, 3])
    print(result)
    doctest.testmod()


================================================
File: data_structures/arrays/prefix_sum.py
================================================
"""
Author  : Alexander Pantyukhin
Date    : November 3, 2022

Implement the class of prefix sum with useful functions based on it.

"""


class PrefixSum:
    def __init__(self, array: list[int]) -> None:
        len_array = len(array)
        self.prefix_sum = [0] * len_array

        if len_array > 0:
            self.prefix_sum[0] = array[0]

        for i in range(1, len_array):
            self.prefix_sum[i] = self.prefix_sum[i - 1] + array[i]

    def get_sum(self, start: int, end: int) -> int:
        """
        The function returns the sum of array from the start to the end indexes.
        Runtime : O(1)
        Space: O(1)

        >>> PrefixSum([1,2,3]).get_sum(0, 2)
        6
        >>> PrefixSum([1,2,3]).get_sum(1, 2)
        5
        >>> PrefixSum([1,2,3]).get_sum(2, 2)
        3
        >>> PrefixSum([1,2,3]).get_sum(2, 3)
        Traceback (most recent call last):
        ...
        IndexError: list index out of range
        """
        if start == 0:
            return self.prefix_sum[end]

        return self.prefix_sum[end] - self.prefix_sum[start - 1]

    def contains_sum(self, target_sum: int) -> bool:
        """
        The function returns True if array contains the target_sum,
        False otherwise.

        Runtime : O(n)
        Space: O(n)

        >>> PrefixSum([1,2,3]).contains_sum(6)
        True
        >>> PrefixSum([1,2,3]).contains_sum(5)
        True
        >>> PrefixSum([1,2,3]).contains_sum(3)
        True
        >>> PrefixSum([1,2,3]).contains_sum(4)
        False
        >>> PrefixSum([1,2,3]).contains_sum(7)
        False
        >>> PrefixSum([1,-2,3]).contains_sum(2)
        True
        """

        sums = {0}
        for sum_item in self.prefix_sum:
            if sum_item - target_sum in sums:
                return True

            sums.add(sum_item)

        return False


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/arrays/product_sum.py
================================================
"""
Calculate the Product Sum from a Special Array.
reference: https://dev.to/sfrasica/algorithms-product-sum-from-an-array-dc6

Python doctests can be run with the following command:
python -m doctest -v product_sum.py

Calculate the product sum of a "special" array which can contain integers or nested
arrays. The product sum is obtained by adding all elements and multiplying by their
respective depths.

For example, in the array [x, y], the product sum is (x + y). In the array [x, [y, z]],
the product sum is x + 2 * (y + z). In the array [x, [y, [z]]],
the product sum is x + 2 * (y + 3z).

Example Input:
[5, 2, [-7, 1], 3, [6, [-13, 8], 4]]
Output: 12

"""


def product_sum(arr: list[int | list], depth: int) -> int:
    """
    Recursively calculates the product sum of an array.

    The product sum of an array is defined as the sum of its elements multiplied by
    their respective depths.  If an element is a list, its product sum is calculated
    recursively by multiplying the sum of its elements with its depth plus one.

    Args:
        arr: The array of integers and nested lists.
        depth: The current depth level.

    Returns:
        int: The product sum of the array.

    Examples:
        >>> product_sum([1, 2, 3], 1)
        6
        >>> product_sum([-1, 2, [-3, 4]], 2)
        8
        >>> product_sum([1, 2, 3], -1)
        -6
        >>> product_sum([1, 2, 3], 0)
        0
        >>> product_sum([1, 2, 3], 7)
        42
        >>> product_sum((1, 2, 3), 7)
        42
        >>> product_sum({1, 2, 3}, 7)
        42
        >>> product_sum([1, -1], 1)
        0
        >>> product_sum([1, -2], 1)
        -1
        >>> product_sum([-3.5, [1, [0.5]]], 1)
        1.5

    """
    total_sum = 0
    for ele in arr:
        total_sum += product_sum(ele, depth + 1) if isinstance(ele, list) else ele
    return total_sum * depth


def product_sum_array(array: list[int | list]) -> int:
    """
    Calculates the product sum of an array.

    Args:
        array (List[Union[int, List]]): The array of integers and nested lists.

    Returns:
        int: The product sum of the array.

    Examples:
        >>> product_sum_array([1, 2, 3])
        6
        >>> product_sum_array([1, [2, 3]])
        11
        >>> product_sum_array([1, [2, [3, 4]]])
        47
        >>> product_sum_array([0])
        0
        >>> product_sum_array([-3.5, [1, [0.5]]])
        1.5
        >>> product_sum_array([1, -2])
        -1

    """
    return product_sum(array, 1)


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/arrays/sparse_table.py
================================================
"""
Sparse table is a data structure that allows answering range queries on
a static number list, i.e. the elements do not change throughout all the queries.

The implementation below will solve the problem of Range Minimum Query:
Finding the minimum value of a subset [L..R] of a static number list.

Overall time complexity: O(nlogn)
Overall space complexity: O(nlogn)

Wikipedia link: https://en.wikipedia.org/wiki/Range_minimum_query
"""

from math import log2


def build_sparse_table(number_list: list[int]) -> list[list[int]]:
    """
    Precompute range minimum queries with power of two length and store the precomputed
    values in a table.

    >>> build_sparse_table([8, 1, 0, 3, 4, 9, 3])
    [[8, 1, 0, 3, 4, 9, 3], [1, 0, 0, 3, 4, 3, 0], [0, 0, 0, 3, 0, 0, 0]]
    >>> build_sparse_table([3, 1, 9])
    [[3, 1, 9], [1, 1, 0]]
    >>> build_sparse_table([])
    Traceback (most recent call last):
    ...
    ValueError: empty number list not allowed
    """
    if not number_list:
        raise ValueError("empty number list not allowed")

    length = len(number_list)
    # Initialise sparse_table -- sparse_table[j][i] represents the minimum value of the
    # subset of length (2 ** j) of number_list, starting from index i.

    # smallest power of 2 subset length that fully covers number_list
    row = int(log2(length)) + 1
    sparse_table = [[0 for i in range(length)] for j in range(row)]

    # minimum of subset of length 1 is that value itself
    for i, value in enumerate(number_list):
        sparse_table[0][i] = value
    j = 1

    # compute the minimum value for all intervals with size (2 ** j)
    while (1 << j) <= length:
        i = 0
        # while subset starting from i still have at least (2 ** j) elements
        while (i + (1 << j) - 1) < length:
            # split range [i, i + 2 ** j] and find minimum of 2 halves
            sparse_table[j][i] = min(
                sparse_table[j - 1][i + (1 << (j - 1))], sparse_table[j - 1][i]
            )
            i += 1
        j += 1
    return sparse_table


def query(sparse_table: list[list[int]], left_bound: int, right_bound: int) -> int:
    """
    >>> query(build_sparse_table([8, 1, 0, 3, 4, 9, 3]), 0, 4)
    0
    >>> query(build_sparse_table([8, 1, 0, 3, 4, 9, 3]), 4, 6)
    3
    >>> query(build_sparse_table([3, 1, 9]), 2, 2)
    9
    >>> query(build_sparse_table([3, 1, 9]), 0, 1)
    1
    >>> query(build_sparse_table([8, 1, 0, 3, 4, 9, 3]), 0, 11)
    Traceback (most recent call last):
    ...
    IndexError: list index out of range
    >>> query(build_sparse_table([]), 0, 0)
    Traceback (most recent call last):
    ...
    ValueError: empty number list not allowed
    """
    if left_bound < 0 or right_bound >= len(sparse_table[0]):
        raise IndexError("list index out of range")

    # highest subset length of power of 2 that is within range [left_bound, right_bound]
    j = int(log2(right_bound - left_bound + 1))

    # minimum of 2 overlapping smaller subsets:
    # [left_bound, left_bound + 2 ** j - 1] and [right_bound - 2 ** j + 1, right_bound]
    return min(sparse_table[j][right_bound - (1 << j) + 1], sparse_table[j][left_bound])


if __name__ == "__main__":
    from doctest import testmod

    testmod()
    print(f"{query(build_sparse_table([3, 1, 9]), 2, 2) = }")


================================================
File: data_structures/arrays/sudoku_solver.py
================================================
"""
Please do not modify this file!  It is published at https://norvig.com/sudoku.html with
only minimal changes to work with modern versions of Python.  If you have improvements,
please make them in a separate file.
"""

import random
import time


def cross(items_a, items_b):
    """
    Cross product of elements in A and elements in B.
    """
    return [a + b for a in items_a for b in items_b]


digits = "123456789"
rows = "ABCDEFGHI"
cols = digits
squares = cross(rows, cols)
unitlist = (
    [cross(rows, c) for c in cols]
    + [cross(r, cols) for r in rows]
    + [cross(rs, cs) for rs in ("ABC", "DEF", "GHI") for cs in ("123", "456", "789")]
)
units = {s: [u for u in unitlist if s in u] for s in squares}
peers = {s: {x for u in units[s] for x in u} - {s} for s in squares}


def test():
    """A set of unit tests."""
    assert len(squares) == 81
    assert len(unitlist) == 27
    assert all(len(units[s]) == 3 for s in squares)
    assert all(len(peers[s]) == 20 for s in squares)
    assert units["C2"] == [
        ["A2", "B2", "C2", "D2", "E2", "F2", "G2", "H2", "I2"],
        ["C1", "C2", "C3", "C4", "C5", "C6", "C7", "C8", "C9"],
        ["A1", "A2", "A3", "B1", "B2", "B3", "C1", "C2", "C3"],
    ]
    # fmt: off
    assert peers["C2"] == {
        "A2", "B2", "D2", "E2", "F2", "G2", "H2", "I2", "C1", "C3",
        "C4", "C5", "C6", "C7", "C8", "C9", "A1", "A3", "B1", "B3"
    }
    # fmt: on
    print("All tests pass.")


def parse_grid(grid):
    """
    Convert grid to a dict of possible values, {square: digits}, or
    return False if a contradiction is detected.
    """
    ## To start, every square can be any digit; then assign values from the grid.
    values = {s: digits for s in squares}
    for s, d in grid_values(grid).items():
        if d in digits and not assign(values, s, d):
            return False  ## (Fail if we can't assign d to square s.)
    return values


def grid_values(grid):
    """
    Convert grid into a dict of {square: char} with '0' or '.' for empties.
    """
    chars = [c for c in grid if c in digits or c in "0."]
    assert len(chars) == 81
    return dict(zip(squares, chars))


def assign(values, s, d):
    """
    Eliminate all the other values (except d) from values[s] and propagate.
    Return values, except return False if a contradiction is detected.
    """
    other_values = values[s].replace(d, "")
    if all(eliminate(values, s, d2) for d2 in other_values):
        return values
    else:
        return False


def eliminate(values, s, d):
    """
    Eliminate d from values[s]; propagate when values or places <= 2.
    Return values, except return False if a contradiction is detected.
    """
    if d not in values[s]:
        return values  ## Already eliminated
    values[s] = values[s].replace(d, "")
    ## (1) If a square s is reduced to one value d2, then eliminate d2 from the peers.
    if len(values[s]) == 0:
        return False  ## Contradiction: removed last value
    elif len(values[s]) == 1:
        d2 = values[s]
        if not all(eliminate(values, s2, d2) for s2 in peers[s]):
            return False
    ## (2) If a unit u is reduced to only one place for a value d, then put it there.
    for u in units[s]:
        dplaces = [s for s in u if d in values[s]]
        if len(dplaces) == 0:
            return False  ## Contradiction: no place for this value
        # d can only be in one place in unit; assign it there
        elif len(dplaces) == 1 and not assign(values, dplaces[0], d):
            return False
    return values


def display(values):
    """
    Display these values as a 2-D grid.
    """
    width = 1 + max(len(values[s]) for s in squares)
    line = "+".join(["-" * (width * 3)] * 3)
    for r in rows:
        print(
            "".join(
                values[r + c].center(width) + ("|" if c in "36" else "") for c in cols
            )
        )
        if r in "CF":
            print(line)
    print()


def solve(grid):
    """
    Solve the grid.
    """
    return search(parse_grid(grid))


def some(seq):
    """Return some element of seq that is true."""
    for e in seq:
        if e:
            return e
    return False


def search(values):
    """
    Using depth-first search and propagation, try all possible values.
    """
    if values is False:
        return False  ## Failed earlier
    if all(len(values[s]) == 1 for s in squares):
        return values  ## Solved!
    ## Chose the unfilled square s with the fewest possibilities
    n, s = min((len(values[s]), s) for s in squares if len(values[s]) > 1)
    return some(search(assign(values.copy(), s, d)) for d in values[s])


def solve_all(grids, name="", showif=0.0):
    """
    Attempt to solve a sequence of grids. Report results.
    When showif is a number of seconds, display puzzles that take longer.
    When showif is None, don't display any puzzles.
    """

    def time_solve(grid):
        start = time.monotonic()
        values = solve(grid)
        t = time.monotonic() - start
        ## Display puzzles that take long enough
        if showif is not None and t > showif:
            display(grid_values(grid))
            if values:
                display(values)
            print(f"({t:.5f} seconds)\n")
        return (t, solved(values))

    times, results = zip(*[time_solve(grid) for grid in grids])
    if (n := len(grids)) > 1:
        print(
            "Solved %d of %d %s puzzles (avg %.2f secs (%d Hz), max %.2f secs)."  # noqa: UP031
            % (sum(results), n, name, sum(times) / n, n / sum(times), max(times))
        )


def solved(values):
    """
    A puzzle is solved if each unit is a permutation of the digits 1 to 9.
    """

    def unitsolved(unit):
        return {values[s] for s in unit} == set(digits)

    return values is not False and all(unitsolved(unit) for unit in unitlist)


def from_file(filename, sep="\n"):
    "Parse a file into a list of strings, separated by sep."
    with open(filename) as file:
        return file.read().strip().split(sep)


def random_puzzle(assignments=17):
    """
    Make a random puzzle with N or more assignments. Restart on contradictions.
    Note the resulting puzzle is not guaranteed to be solvable, but empirically
    about 99.8% of them are solvable. Some have multiple solutions.
    """
    values = {s: digits for s in squares}
    for s in shuffled(squares):
        if not assign(values, s, random.choice(values[s])):
            break
        ds = [values[s] for s in squares if len(values[s]) == 1]
        if len(ds) >= assignments and len(set(ds)) >= 8:
            return "".join(values[s] if len(values[s]) == 1 else "." for s in squares)
    return random_puzzle(assignments)  ## Give up and make a new puzzle


def shuffled(seq):
    """
    Return a randomly shuffled copy of the input sequence.
    """
    seq = list(seq)
    random.shuffle(seq)
    return seq


grid1 = (
    "003020600900305001001806400008102900700000008006708200002609500800203009005010300"
)
grid2 = (
    "4.....8.5.3..........7......2.....6.....8.4......1.......6.3.7.5..2.....1.4......"
)
hard1 = (
    ".....6....59.....82....8....45........3........6..3.54...325..6.................."
)

if __name__ == "__main__":
    test()
    # solve_all(from_file("easy50.txt", '========'), "easy", None)
    # solve_all(from_file("top95.txt"), "hard", None)
    # solve_all(from_file("hardest.txt"), "hardest", None)
    solve_all([random_puzzle() for _ in range(99)], "random", 100.0)
    for puzzle in (grid1, grid2):  # , hard1):  # Takes 22 sec to solve on my M1 Mac.
        display(parse_grid(puzzle))
        start = time.monotonic()
        solve(puzzle)
        t = time.monotonic() - start
        print(f"Solved: {t:.5f} sec")


================================================
File: data_structures/binary_tree/README.md
================================================
# Binary Tree Traversal

## Overview

The combination of binary trees being data structures and traversal being an algorithm relates to classic problems, either directly or indirectly.

> If you can grasp the traversal of binary trees, the traversal of other complicated trees will be easy for you.

The following are some common ways to traverse trees.

- Depth First Traversals (DFS): In-order, Pre-order, Post-order

- Level Order Traversal or Breadth First or Traversal (BFS)

There are applications for both DFS and BFS.

Stack can be used to simplify the process of DFS traversal. Besides, since tree is a recursive data structure, recursion and stack are two key points for DFS.

Graph for DFS:

![binary-tree-traversal-dfs](https://tva1.sinaimg.cn/large/007S8ZIlly1ghluhzhynsg30dw0dw3yl.gif)

The key point of BFS is how to determine whether the traversal of each level has been completed. The answer is to use a variable as a flag to represent the end of the traversal of current level.

## Pre-order Traversal

The traversal order of pre-order traversal is `root-left-right`.

Algorithm Pre-order

1. Visit the root node and push it into a stack.

2. Pop a node from the stack, and push its right and left child node into the stack respectively.

3. Repeat step 2.

Conclusion: This problem involves the classic recursive data structure (i.e. a binary tree), and the algorithm above demonstrates how a simplified solution can be reached by using a stack.

If you look at the bigger picture, you'll find that the process of traversal is as followed. `Visit the left subtrees respectively from top to bottom, and visit the right subtrees respectively from bottom to top`. If we are to implement it from this perspective, things will be somewhat different. For the `top to bottom` part we can simply use recursion, and for the `bottom to top` part we can turn to stack.

## In-order Traversal

The traversal order of in-order traversal is `left-root-right`.

So the root node is not printed first. Things are getting a bit complicated here.

Algorithm In-order

1. Visit the root and push it into a stack.

2. If there is a left child node, push it into the stack. Repeat this process until a leaf node reached.

    > At this point the root node and all the left nodes are in the stack.

3. Start popping nodes from the stack. If a node has a right child node, push the child node into the stack. Repeat step 2.

It's worth pointing out that the in-order traversal of a binary search tree (BST) is a sorted array, which is helpful for coming up simplified solutions for some problems.

## Post-order Traversal

The traversal order of post-order traversal is `left-right-root`.

This one is a bit of a challenge. It deserves the `hard` tag of LeetCode.

In this case, the root node is printed not as the first but the last one. A cunning way to do it is to:

Record whether the current node has been visited. If 1) it's a leaf node or 2) both its left and right subtrees have been traversed, then it can be popped from the stack.

As for `1) it's a leaf node`, you can easily tell whether a node is a leaf if both its left and right are `null`.

As for `2) both its left and right subtrees have been traversed`, we only need a variable to record whether a node has been visited or not. In the worst case, we need to record the status for every single node and the space complexity is `O(n)`. But if you come to think about it, as we are using a stack and start printing the result from the leaf nodes, it makes sense that we only record the status for the current node popping from the stack, reducing the space complexity to `O(1)`.

## Level Order Traversal

The key point of level order traversal is how do we know whether the traversal of each level is done. The answer is that we use a variable as a flag representing the end of the traversal of the current level.

![binary-tree-traversal-bfs](https://tva1.sinaimg.cn/large/007S8ZIlly1ghlui1tpoug30dw0dw3yl.gif)

Algorithm Level-order

1. Visit the root node, put it in a FIFO queue, put in the queue a special flag (we are using `null` here).

2. Dequeue a node.

3. If the node equals `null`, it means that all nodes of the current level have been visited. If the queue is empty, we do nothing. Or else we put in another `null`.

4. If the node is not `null`, meaning the traversal of current level has not finished yet, we enqueue its left subtree and right subtree respectively.

## Bi-color marking

We know that there is a tri-color marking in garbage collection algorithm, which works as described below.

- The white color represents "not visited".

- The gray color represents "not all child nodes visited".

- The black color represents "all child nodes visited".

Enlightened by tri-color marking, a bi-color marking method can be invented to solve all three traversal problems with one solution.

The core idea is as follow.

- Use a color to mark whether a node has been visited or not. Nodes yet to be visited are marked as white and visited nodes are marked as gray.

- If we are visiting a white node, turn it into gray, and push its right child node, itself, and it's left child node into the stack respectively.

- If we are visiting a gray node, print it.

Implementation of pre-order and post-order traversal algorithms can be easily done by changing the order of pushing the child nodes into the stack.

Reference: [LeetCode](https://github.com/azl397985856/leetcode/blob/master/thinkings/binary-tree-traversal.en.md)


================================================
File: data_structures/binary_tree/avl_tree.py
================================================
"""
Implementation of an auto-balanced binary tree!
For doctests run following command:
python3 -m doctest -v avl_tree.py
For testing run:
python avl_tree.py
"""

from __future__ import annotations

import math
import random
from typing import Any


class MyQueue:
    def __init__(self) -> None:
        self.data: list[Any] = []
        self.head: int = 0
        self.tail: int = 0

    def is_empty(self) -> bool:
        return self.head == self.tail

    def push(self, data: Any) -> None:
        self.data.append(data)
        self.tail = self.tail + 1

    def pop(self) -> Any:
        ret = self.data[self.head]
        self.head = self.head + 1
        return ret

    def count(self) -> int:
        return self.tail - self.head

    def print_queue(self) -> None:
        print(self.data)
        print("**************")
        print(self.data[self.head : self.tail])


class MyNode:
    def __init__(self, data: Any) -> None:
        self.data = data
        self.left: MyNode | None = None
        self.right: MyNode | None = None
        self.height: int = 1

    def get_data(self) -> Any:
        return self.data

    def get_left(self) -> MyNode | None:
        return self.left

    def get_right(self) -> MyNode | None:
        return self.right

    def get_height(self) -> int:
        return self.height

    def set_data(self, data: Any) -> None:
        self.data = data

    def set_left(self, node: MyNode | None) -> None:
        self.left = node

    def set_right(self, node: MyNode | None) -> None:
        self.right = node

    def set_height(self, height: int) -> None:
        self.height = height


def get_height(node: MyNode | None) -> int:
    if node is None:
        return 0
    return node.get_height()


def my_max(a: int, b: int) -> int:
    if a > b:
        return a
    return b


def right_rotation(node: MyNode) -> MyNode:
    r"""
            A                      B
           / \                    / \
          B   C                  Bl  A
         / \       -->          /   / \
        Bl  Br                 UB Br  C
       /
     UB
    UB = unbalanced node
    """
    print("left rotation node:", node.get_data())
    ret = node.get_left()
    assert ret is not None
    node.set_left(ret.get_right())
    ret.set_right(node)
    h1 = my_max(get_height(node.get_right()), get_height(node.get_left())) + 1
    node.set_height(h1)
    h2 = my_max(get_height(ret.get_right()), get_height(ret.get_left())) + 1
    ret.set_height(h2)
    return ret


def left_rotation(node: MyNode) -> MyNode:
    """
    a mirror symmetry rotation of the left_rotation
    """
    print("right rotation node:", node.get_data())
    ret = node.get_right()
    assert ret is not None
    node.set_right(ret.get_left())
    ret.set_left(node)
    h1 = my_max(get_height(node.get_right()), get_height(node.get_left())) + 1
    node.set_height(h1)
    h2 = my_max(get_height(ret.get_right()), get_height(ret.get_left())) + 1
    ret.set_height(h2)
    return ret


def lr_rotation(node: MyNode) -> MyNode:
    r"""
            A              A                    Br
           / \            / \                  /  \
          B   C    LR    Br  C       RR       B    A
         / \       -->  /  \         -->    /     / \
        Bl  Br         B   UB              Bl    UB  C
             \        /
             UB     Bl
    RR = right_rotation   LR = left_rotation
    """
    left_child = node.get_left()
    assert left_child is not None
    node.set_left(left_rotation(left_child))
    return right_rotation(node)


def rl_rotation(node: MyNode) -> MyNode:
    right_child = node.get_right()
    assert right_child is not None
    node.set_right(right_rotation(right_child))
    return left_rotation(node)


def insert_node(node: MyNode | None, data: Any) -> MyNode | None:
    if node is None:
        return MyNode(data)
    if data < node.get_data():
        node.set_left(insert_node(node.get_left(), data))
        if (
            get_height(node.get_left()) - get_height(node.get_right()) == 2
        ):  # an unbalance detected
            left_child = node.get_left()
            assert left_child is not None
            if (
                data < left_child.get_data()
            ):  # new node is the left child of the left child
                node = right_rotation(node)
            else:
                node = lr_rotation(node)
    else:
        node.set_right(insert_node(node.get_right(), data))
        if get_height(node.get_right()) - get_height(node.get_left()) == 2:
            right_child = node.get_right()
            assert right_child is not None
            if data < right_child.get_data():
                node = rl_rotation(node)
            else:
                node = left_rotation(node)
    h1 = my_max(get_height(node.get_right()), get_height(node.get_left())) + 1
    node.set_height(h1)
    return node


def get_right_most(root: MyNode) -> Any:
    while True:
        right_child = root.get_right()
        if right_child is None:
            break
        root = right_child
    return root.get_data()


def get_left_most(root: MyNode) -> Any:
    while True:
        left_child = root.get_left()
        if left_child is None:
            break
        root = left_child
    return root.get_data()


def del_node(root: MyNode, data: Any) -> MyNode | None:
    left_child = root.get_left()
    right_child = root.get_right()
    if root.get_data() == data:
        if left_child is not None and right_child is not None:
            temp_data = get_left_most(right_child)
            root.set_data(temp_data)
            root.set_right(del_node(right_child, temp_data))
        elif left_child is not None:
            root = left_child
        elif right_child is not None:
            root = right_child
        else:
            return None
    elif root.get_data() > data:
        if left_child is None:
            print("No such data")
            return root
        else:
            root.set_left(del_node(left_child, data))
    # root.get_data() < data
    elif right_child is None:
        return root
    else:
        root.set_right(del_node(right_child, data))

    # Re-fetch left_child and right_child references
    left_child = root.get_left()
    right_child = root.get_right()

    if get_height(right_child) - get_height(left_child) == 2:
        assert right_child is not None
        if get_height(right_child.get_right()) > get_height(right_child.get_left()):
            root = left_rotation(root)
        else:
            root = rl_rotation(root)
    elif get_height(right_child) - get_height(left_child) == -2:
        assert left_child is not None
        if get_height(left_child.get_left()) > get_height(left_child.get_right()):
            root = right_rotation(root)
        else:
            root = lr_rotation(root)
    height = my_max(get_height(root.get_right()), get_height(root.get_left())) + 1
    root.set_height(height)
    return root


class AVLtree:
    """
    An AVL tree doctest
    Examples:
    >>> t = AVLtree()
    >>> t.insert(4)
    insert:4
    >>> print(str(t).replace(" \\n","\\n"))
     4
    *************************************
    >>> t.insert(2)
    insert:2
    >>> print(str(t).replace(" \\n","\\n").replace(" \\n","\\n"))
      4
     2  *
    *************************************
    >>> t.insert(3)
    insert:3
    right rotation node: 2
    left rotation node: 4
    >>> print(str(t).replace(" \\n","\\n").replace(" \\n","\\n"))
      3
     2  4
    *************************************
    >>> t.get_height()
    2
    >>> t.del_node(3)
    delete:3
    >>> print(str(t).replace(" \\n","\\n").replace(" \\n","\\n"))
      4
     2  *
    *************************************
    """

    def __init__(self) -> None:
        self.root: MyNode | None = None

    def get_height(self) -> int:
        return get_height(self.root)

    def insert(self, data: Any) -> None:
        print("insert:" + str(data))
        self.root = insert_node(self.root, data)

    def del_node(self, data: Any) -> None:
        print("delete:" + str(data))
        if self.root is None:
            print("Tree is empty!")
            return
        self.root = del_node(self.root, data)

    def __str__(
        self,
    ) -> str:  # a level traversale, gives a more intuitive look on the tree
        output = ""
        q = MyQueue()
        q.push(self.root)
        layer = self.get_height()
        if layer == 0:
            return output
        cnt = 0
        while not q.is_empty():
            node = q.pop()
            space = " " * int(math.pow(2, layer - 1))
            output += space
            if node is None:
                output += "*"
                q.push(None)
                q.push(None)
            else:
                output += str(node.get_data())
                q.push(node.get_left())
                q.push(node.get_right())
            output += space
            cnt = cnt + 1
            for i in range(100):
                if cnt == math.pow(2, i) - 1:
                    layer = layer - 1
                    if layer == 0:
                        output += "\n*************************************"
                        return output
                    output += "\n"
                    break
        output += "\n*************************************"
        return output


def _test() -> None:
    import doctest

    doctest.testmod()


if __name__ == "__main__":
    _test()
    t = AVLtree()
    lst = list(range(10))
    random.shuffle(lst)
    for i in lst:
        t.insert(i)
        print(str(t))
    random.shuffle(lst)
    for i in lst:
        t.del_node(i)
        print(str(t))


================================================
File: data_structures/binary_tree/basic_binary_tree.py
================================================
from __future__ import annotations

from collections.abc import Iterator
from dataclasses import dataclass


@dataclass
class Node:
    data: int
    left: Node | None = None
    right: Node | None = None

    def __iter__(self) -> Iterator[int]:
        if self.left:
            yield from self.left
        yield self.data
        if self.right:
            yield from self.right

    def __len__(self) -> int:
        return sum(1 for _ in self)

    def is_full(self) -> bool:
        if not self or (not self.left and not self.right):
            return True
        if self.left and self.right:
            return self.left.is_full() and self.right.is_full()
        return False


@dataclass
class BinaryTree:
    root: Node

    def __iter__(self) -> Iterator[int]:
        return iter(self.root)

    def __len__(self) -> int:
        return len(self.root)

    @classmethod
    def small_tree(cls) -> BinaryTree:
        """
        Return a small binary tree with 3 nodes.
        >>> binary_tree = BinaryTree.small_tree()
        >>> len(binary_tree)
        3
        >>> list(binary_tree)
        [1, 2, 3]
        """
        binary_tree = BinaryTree(Node(2))
        binary_tree.root.left = Node(1)
        binary_tree.root.right = Node(3)
        return binary_tree

    @classmethod
    def medium_tree(cls) -> BinaryTree:
        """
        Return a medium binary tree with 3 nodes.
        >>> binary_tree = BinaryTree.medium_tree()
        >>> len(binary_tree)
        7
        >>> list(binary_tree)
        [1, 2, 3, 4, 5, 6, 7]
        """
        binary_tree = BinaryTree(Node(4))
        binary_tree.root.left = two = Node(2)
        two.left = Node(1)
        two.right = Node(3)
        binary_tree.root.right = five = Node(5)
        five.right = six = Node(6)
        six.right = Node(7)
        return binary_tree

    def depth(self) -> int:
        """
        Returns the depth of the tree

        >>> BinaryTree(Node(1)).depth()
        1
        >>> BinaryTree.small_tree().depth()
        2
        >>> BinaryTree.medium_tree().depth()
        4
        """
        return self._depth(self.root)

    def _depth(self, node: Node | None) -> int:
        if not node:
            return 0
        return 1 + max(self._depth(node.left), self._depth(node.right))

    def is_full(self) -> bool:
        """
        Returns True if the tree is full

        >>> BinaryTree(Node(1)).is_full()
        True
        >>> BinaryTree.small_tree().is_full()
        True
        >>> BinaryTree.medium_tree().is_full()
        False
        """
        return self.root.is_full()


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/binary_tree/binary_search_tree.py
================================================
r"""
A binary search Tree

Example
              8
             / \
            3   10
           / \    \
          1   6    14
             / \   /
            4   7 13

>>> t = BinarySearchTree().insert(8, 3, 6, 1, 10, 14, 13, 4, 7)
>>> print(" ".join(repr(i.value) for i in t.traversal_tree()))
8 3 1 6 4 7 10 14 13

>>> tuple(i.value for i in t.traversal_tree(inorder))
(1, 3, 4, 6, 7, 8, 10, 13, 14)
>>> tuple(t)
(1, 3, 4, 6, 7, 8, 10, 13, 14)
>>> t.find_kth_smallest(3, t.root)
4
>>> tuple(t)[3-1]
4

>>> print(" ".join(repr(i.value) for i in t.traversal_tree(postorder)))
1 4 7 6 3 13 14 10 8
>>> t.remove(20)
Traceback (most recent call last):
    ...
ValueError: Value 20 not found
>>> BinarySearchTree().search(6)
Traceback (most recent call last):
    ...
IndexError: Warning: Tree is empty! please use another.

Other example:

>>> testlist = (8, 3, 6, 1, 10, 14, 13, 4, 7)
>>> t = BinarySearchTree()
>>> for i in testlist:
...     t.insert(i)  # doctest: +ELLIPSIS
BinarySearchTree(root=8)
BinarySearchTree(root={'8': (3, None)})
BinarySearchTree(root={'8': ({'3': (None, 6)}, None)})
BinarySearchTree(root={'8': ({'3': (1, 6)}, None)})
BinarySearchTree(root={'8': ({'3': (1, 6)}, 10)})
BinarySearchTree(root={'8': ({'3': (1, 6)}, {'10': (None, 14)})})
BinarySearchTree(root={'8': ({'3': (1, 6)}, {'10': (None, {'14': (13, None)})})})
BinarySearchTree(root={'8': ({'3': (1, {'6': (4, None)})}, {'10': (None, {'14': ...
BinarySearchTree(root={'8': ({'3': (1, {'6': (4, 7)})}, {'10': (None, {'14': (13, ...

Prints all the elements of the list in order traversal
>>> print(t)
{'8': ({'3': (1, {'6': (4, 7)})}, {'10': (None, {'14': (13, None)})})}

Test existence
>>> t.search(6) is not None
True
>>> 6 in t
True
>>> t.search(-1) is not None
False
>>> -1 in t
False

>>> t.search(6).is_right
True
>>> t.search(1).is_right
False

>>> t.get_max().value
14
>>> max(t)
14
>>> t.get_min().value
1
>>> min(t)
1
>>> t.empty()
False
>>> not t
False
>>> for i in testlist:
...     t.remove(i)
>>> t.empty()
True
>>> not t
True
"""

from __future__ import annotations

from collections.abc import Iterable, Iterator
from dataclasses import dataclass
from typing import Any, Self


@dataclass
class Node:
    value: int
    left: Node | None = None
    right: Node | None = None
    parent: Node | None = None  # Added in order to delete a node easier

    def __iter__(self) -> Iterator[int]:
        """
        >>> list(Node(0))
        [0]
        >>> list(Node(0, Node(-1), Node(1), None))
        [-1, 0, 1]
        """
        yield from self.left or []
        yield self.value
        yield from self.right or []

    def __repr__(self) -> str:
        from pprint import pformat

        if self.left is None and self.right is None:
            return str(self.value)
        return pformat({f"{self.value}": (self.left, self.right)}, indent=1)

    @property
    def is_right(self) -> bool:
        return bool(self.parent and self is self.parent.right)


@dataclass
class BinarySearchTree:
    root: Node | None = None

    def __bool__(self) -> bool:
        return bool(self.root)

    def __iter__(self) -> Iterator[int]:
        yield from self.root or []

    def __str__(self) -> str:
        """
        Return a string of all the Nodes using in order traversal
        """
        return str(self.root)

    def __reassign_nodes(self, node: Node, new_children: Node | None) -> None:
        if new_children is not None:  # reset its kids
            new_children.parent = node.parent
        if node.parent is not None:  # reset its parent
            if node.is_right:  # If it is the right child
                node.parent.right = new_children
            else:
                node.parent.left = new_children
        else:
            self.root = new_children

    def empty(self) -> bool:
        """
        Returns True if the tree does not have any element(s).
        False if the tree has element(s).

        >>> BinarySearchTree().empty()
        True
        >>> BinarySearchTree().insert(1).empty()
        False
        >>> BinarySearchTree().insert(8, 3, 6, 1, 10, 14, 13, 4, 7).empty()
        False
        """
        return not self.root

    def __insert(self, value) -> None:
        """
        Insert a new node in Binary Search Tree with value label
        """
        new_node = Node(value)  # create a new Node
        if self.empty():  # if Tree is empty
            self.root = new_node  # set its root
        else:  # Tree is not empty
            parent_node = self.root  # from root
            if parent_node is None:
                return
            while True:  # While we don't get to a leaf
                if value < parent_node.value:  # We go left
                    if parent_node.left is None:
                        parent_node.left = new_node  # We insert the new node in a leaf
                        break
                    else:
                        parent_node = parent_node.left
                elif parent_node.right is None:
                    parent_node.right = new_node
                    break
                else:
                    parent_node = parent_node.right
            new_node.parent = parent_node

    def insert(self, *values) -> Self:
        for value in values:
            self.__insert(value)
        return self

    def search(self, value) -> Node | None:
        """
        >>> tree = BinarySearchTree().insert(10, 20, 30, 40, 50)
        >>> tree.search(10)
        {'10': (None, {'20': (None, {'30': (None, {'40': (None, 50)})})})}
        >>> tree.search(20)
        {'20': (None, {'30': (None, {'40': (None, 50)})})}
        >>> tree.search(30)
        {'30': (None, {'40': (None, 50)})}
        >>> tree.search(40)
        {'40': (None, 50)}
        >>> tree.search(50)
        50
        >>> tree.search(5) is None  # element not present
        True
        >>> tree.search(0) is None  # element not present
        True
        >>> tree.search(-5) is None  # element not present
        True
        >>> BinarySearchTree().search(10)
        Traceback (most recent call last):
            ...
        IndexError: Warning: Tree is empty! please use another.
        """

        if self.empty():
            raise IndexError("Warning: Tree is empty! please use another.")
        else:
            node = self.root
            # use lazy evaluation here to avoid NoneType Attribute error
            while node is not None and node.value is not value:
                node = node.left if value < node.value else node.right
            return node

    def get_max(self, node: Node | None = None) -> Node | None:
        """
        We go deep on the right branch

        >>> BinarySearchTree().insert(10, 20, 30, 40, 50).get_max()
        50
        >>> BinarySearchTree().insert(-5, -1, 0.1, -0.3, -4.5).get_max()
        {'0.1': (-0.3, None)}
        >>> BinarySearchTree().insert(1, 78.3, 30, 74.0, 1).get_max()
        {'78.3': ({'30': (1, 74.0)}, None)}
        >>> BinarySearchTree().insert(1, 783, 30, 740, 1).get_max()
        {'783': ({'30': (1, 740)}, None)}
        """
        if node is None:
            if self.root is None:
                return None
            node = self.root

        if not self.empty():
            while node.right is not None:
                node = node.right
        return node

    def get_min(self, node: Node | None = None) -> Node | None:
        """
        We go deep on the left branch

        >>> BinarySearchTree().insert(10, 20, 30, 40, 50).get_min()
        {'10': (None, {'20': (None, {'30': (None, {'40': (None, 50)})})})}
        >>> BinarySearchTree().insert(-5, -1, 0, -0.3, -4.5).get_min()
        {'-5': (None, {'-1': (-4.5, {'0': (-0.3, None)})})}
        >>> BinarySearchTree().insert(1, 78.3, 30, 74.0, 1).get_min()
        {'1': (None, {'78.3': ({'30': (1, 74.0)}, None)})}
        >>> BinarySearchTree().insert(1, 783, 30, 740, 1).get_min()
        {'1': (None, {'783': ({'30': (1, 740)}, None)})}
        """
        if node is None:
            node = self.root
        if self.root is None:
            return None
        if not self.empty():
            node = self.root
            while node.left is not None:
                node = node.left
        return node

    def remove(self, value: int) -> None:
        # Look for the node with that label
        node = self.search(value)
        if node is None:
            msg = f"Value {value} not found"
            raise ValueError(msg)

        if node.left is None and node.right is None:  # If it has no children
            self.__reassign_nodes(node, None)
        elif node.left is None:  # Has only right children
            self.__reassign_nodes(node, node.right)
        elif node.right is None:  # Has only left children
            self.__reassign_nodes(node, node.left)
        else:
            predecessor = self.get_max(
                node.left
            )  # Gets the max value of the left branch
            self.remove(predecessor.value)  # type: ignore[union-attr]
            node.value = (
                predecessor.value  # type: ignore[union-attr]
            )  # Assigns the value to the node to delete and keep tree structure

    def preorder_traverse(self, node: Node | None) -> Iterable:
        if node is not None:
            yield node  # Preorder Traversal
            yield from self.preorder_traverse(node.left)
            yield from self.preorder_traverse(node.right)

    def traversal_tree(self, traversal_function=None) -> Any:
        """
        This function traversal the tree.
        You can pass a function to traversal the tree as needed by client code
        """
        if traversal_function is None:
            return self.preorder_traverse(self.root)
        else:
            return traversal_function(self.root)

    def inorder(self, arr: list, node: Node | None) -> None:
        """Perform an inorder traversal and append values of the nodes to
        a list named arr"""
        if node:
            self.inorder(arr, node.left)
            arr.append(node.value)
            self.inorder(arr, node.right)

    def find_kth_smallest(self, k: int, node: Node) -> int:
        """Return the kth smallest element in a binary search tree"""
        arr: list[int] = []
        self.inorder(arr, node)  # append all values to list using inorder traversal
        return arr[k - 1]


def inorder(curr_node: Node | None) -> list[Node]:
    """
    inorder (left, self, right)
    """
    node_list = []
    if curr_node is not None:
        node_list = [*inorder(curr_node.left), curr_node, *inorder(curr_node.right)]
    return node_list


def postorder(curr_node: Node | None) -> list[Node]:
    """
    postOrder (left, right, self)
    """
    node_list = []
    if curr_node is not None:
        node_list = postorder(curr_node.left) + postorder(curr_node.right) + [curr_node]
    return node_list


if __name__ == "__main__":
    import doctest

    doctest.testmod(verbose=True)


================================================
File: data_structures/binary_tree/binary_search_tree_recursive.py
================================================
"""
This is a python3 implementation of binary search tree using recursion

To run tests:
python -m unittest binary_search_tree_recursive.py

To run an example:
python binary_search_tree_recursive.py
"""

from __future__ import annotations

import unittest
from collections.abc import Iterator

import pytest


class Node:
    def __init__(self, label: int, parent: Node | None) -> None:
        self.label = label
        self.parent = parent
        self.left: Node | None = None
        self.right: Node | None = None


class BinarySearchTree:
    def __init__(self) -> None:
        self.root: Node | None = None

    def empty(self) -> None:
        """
        Empties the tree

        >>> t = BinarySearchTree()
        >>> assert t.root is None
        >>> t.put(8)
        >>> assert t.root is not None
        """
        self.root = None

    def is_empty(self) -> bool:
        """
        Checks if the tree is empty

        >>> t = BinarySearchTree()
        >>> t.is_empty()
        True
        >>> t.put(8)
        >>> t.is_empty()
        False
        """
        return self.root is None

    def put(self, label: int) -> None:
        """
        Put a new node in the tree

        >>> t = BinarySearchTree()
        >>> t.put(8)
        >>> assert t.root.parent is None
        >>> assert t.root.label == 8

        >>> t.put(10)
        >>> assert t.root.right.parent == t.root
        >>> assert t.root.right.label == 10

        >>> t.put(3)
        >>> assert t.root.left.parent == t.root
        >>> assert t.root.left.label == 3
        """
        self.root = self._put(self.root, label)

    def _put(self, node: Node | None, label: int, parent: Node | None = None) -> Node:
        if node is None:
            node = Node(label, parent)
        elif label < node.label:
            node.left = self._put(node.left, label, node)
        elif label > node.label:
            node.right = self._put(node.right, label, node)
        else:
            msg = f"Node with label {label} already exists"
            raise ValueError(msg)

        return node

    def search(self, label: int) -> Node:
        """
        Searches a node in the tree

        >>> t = BinarySearchTree()
        >>> t.put(8)
        >>> t.put(10)
        >>> node = t.search(8)
        >>> assert node.label == 8

        >>> node = t.search(3)
        Traceback (most recent call last):
            ...
        ValueError: Node with label 3 does not exist
        """
        return self._search(self.root, label)

    def _search(self, node: Node | None, label: int) -> Node:
        if node is None:
            msg = f"Node with label {label} does not exist"
            raise ValueError(msg)
        elif label < node.label:
            node = self._search(node.left, label)
        elif label > node.label:
            node = self._search(node.right, label)

        return node

    def remove(self, label: int) -> None:
        """
        Removes a node in the tree

        >>> t = BinarySearchTree()
        >>> t.put(8)
        >>> t.put(10)
        >>> t.remove(8)
        >>> assert t.root.label == 10

        >>> t.remove(3)
        Traceback (most recent call last):
            ...
        ValueError: Node with label 3 does not exist
        """
        node = self.search(label)
        if node.right and node.left:
            lowest_node = self._get_lowest_node(node.right)
            lowest_node.left = node.left
            lowest_node.right = node.right
            node.left.parent = lowest_node
            if node.right:
                node.right.parent = lowest_node
            self._reassign_nodes(node, lowest_node)
        elif not node.right and node.left:
            self._reassign_nodes(node, node.left)
        elif node.right and not node.left:
            self._reassign_nodes(node, node.right)
        else:
            self._reassign_nodes(node, None)

    def _reassign_nodes(self, node: Node, new_children: Node | None) -> None:
        if new_children:
            new_children.parent = node.parent

        if node.parent:
            if node.parent.right == node:
                node.parent.right = new_children
            else:
                node.parent.left = new_children
        else:
            self.root = new_children

    def _get_lowest_node(self, node: Node) -> Node:
        if node.left:
            lowest_node = self._get_lowest_node(node.left)
        else:
            lowest_node = node
            self._reassign_nodes(node, node.right)

        return lowest_node

    def exists(self, label: int) -> bool:
        """
        Checks if a node exists in the tree

        >>> t = BinarySearchTree()
        >>> t.put(8)
        >>> t.put(10)
        >>> t.exists(8)
        True

        >>> t.exists(3)
        False
        """
        try:
            self.search(label)
            return True
        except ValueError:
            return False

    def get_max_label(self) -> int:
        """
        Gets the max label inserted in the tree

        >>> t = BinarySearchTree()
        >>> t.get_max_label()
        Traceback (most recent call last):
            ...
        ValueError: Binary search tree is empty

        >>> t.put(8)
        >>> t.put(10)
        >>> t.get_max_label()
        10
        """
        if self.root is None:
            raise ValueError("Binary search tree is empty")

        node = self.root
        while node.right is not None:
            node = node.right

        return node.label

    def get_min_label(self) -> int:
        """
        Gets the min label inserted in the tree

        >>> t = BinarySearchTree()
        >>> t.get_min_label()
        Traceback (most recent call last):
            ...
        ValueError: Binary search tree is empty

        >>> t.put(8)
        >>> t.put(10)
        >>> t.get_min_label()
        8
        """
        if self.root is None:
            raise ValueError("Binary search tree is empty")

        node = self.root
        while node.left is not None:
            node = node.left

        return node.label

    def inorder_traversal(self) -> Iterator[Node]:
        """
        Return the inorder traversal of the tree

        >>> t = BinarySearchTree()
        >>> [i.label for i in t.inorder_traversal()]
        []

        >>> t.put(8)
        >>> t.put(10)
        >>> t.put(9)
        >>> [i.label for i in t.inorder_traversal()]
        [8, 9, 10]
        """
        return self._inorder_traversal(self.root)

    def _inorder_traversal(self, node: Node | None) -> Iterator[Node]:
        if node is not None:
            yield from self._inorder_traversal(node.left)
            yield node
            yield from self._inorder_traversal(node.right)

    def preorder_traversal(self) -> Iterator[Node]:
        """
        Return the preorder traversal of the tree

        >>> t = BinarySearchTree()
        >>> [i.label for i in t.preorder_traversal()]
        []

        >>> t.put(8)
        >>> t.put(10)
        >>> t.put(9)
        >>> [i.label for i in t.preorder_traversal()]
        [8, 10, 9]
        """
        return self._preorder_traversal(self.root)

    def _preorder_traversal(self, node: Node | None) -> Iterator[Node]:
        if node is not None:
            yield node
            yield from self._preorder_traversal(node.left)
            yield from self._preorder_traversal(node.right)


class BinarySearchTreeTest(unittest.TestCase):
    @staticmethod
    def _get_binary_search_tree() -> BinarySearchTree:
        r"""
              8
             / \
            3   10
           / \    \
          1   6    14
             / \   /
            4   7 13
             \
              5
        """
        t = BinarySearchTree()
        t.put(8)
        t.put(3)
        t.put(6)
        t.put(1)
        t.put(10)
        t.put(14)
        t.put(13)
        t.put(4)
        t.put(7)
        t.put(5)

        return t

    def test_put(self) -> None:
        t = BinarySearchTree()
        assert t.is_empty()

        t.put(8)
        r"""
              8
        """
        assert t.root is not None
        assert t.root.parent is None
        assert t.root.label == 8

        t.put(10)
        r"""
              8
               \
                10
        """
        assert t.root.right is not None
        assert t.root.right.parent == t.root
        assert t.root.right.label == 10

        t.put(3)
        r"""
              8
             / \
            3   10
        """
        assert t.root.left is not None
        assert t.root.left.parent == t.root
        assert t.root.left.label == 3

        t.put(6)
        r"""
              8
             / \
            3   10
             \
              6
        """
        assert t.root.left.right is not None
        assert t.root.left.right.parent == t.root.left
        assert t.root.left.right.label == 6

        t.put(1)
        r"""
              8
             / \
            3   10
           / \
          1   6
        """
        assert t.root.left.left is not None
        assert t.root.left.left.parent == t.root.left
        assert t.root.left.left.label == 1

        with pytest.raises(ValueError):
            t.put(1)

    def test_search(self) -> None:
        t = self._get_binary_search_tree()

        node = t.search(6)
        assert node.label == 6

        node = t.search(13)
        assert node.label == 13

        with pytest.raises(ValueError):
            t.search(2)

    def test_remove(self) -> None:
        t = self._get_binary_search_tree()

        t.remove(13)
        r"""
              8
             / \
            3   10
           / \    \
          1   6    14
             / \
            4   7
             \
              5
        """
        assert t.root is not None
        assert t.root.right is not None
        assert t.root.right.right is not None
        assert t.root.right.right.right is None
        assert t.root.right.right.left is None

        t.remove(7)
        r"""
              8
             / \
            3   10
           / \    \
          1   6    14
             /
            4
             \
              5
        """
        assert t.root.left is not None
        assert t.root.left.right is not None
        assert t.root.left.right.left is not None
        assert t.root.left.right.right is None
        assert t.root.left.right.left.label == 4

        t.remove(6)
        r"""
              8
             / \
            3   10
           / \    \
          1   4    14
               \
                5
        """
        assert t.root.left.left is not None
        assert t.root.left.right.right is not None
        assert t.root.left.left.label == 1
        assert t.root.left.right.label == 4
        assert t.root.left.right.right.label == 5
        assert t.root.left.right.left is None
        assert t.root.left.left.parent == t.root.left
        assert t.root.left.right.parent == t.root.left

        t.remove(3)
        r"""
              8
             / \
            4   10
           / \    \
          1   5    14
        """
        assert t.root is not None
        assert t.root.left.label == 4
        assert t.root.left.right.label == 5
        assert t.root.left.left.label == 1
        assert t.root.left.parent == t.root
        assert t.root.left.left.parent == t.root.left
        assert t.root.left.right.parent == t.root.left

        t.remove(4)
        r"""
              8
             / \
            5   10
           /      \
          1        14
        """
        assert t.root.left is not None
        assert t.root.left.left is not None
        assert t.root.left.label == 5
        assert t.root.left.right is None
        assert t.root.left.left.label == 1
        assert t.root.left.parent == t.root
        assert t.root.left.left.parent == t.root.left

    def test_remove_2(self) -> None:
        t = self._get_binary_search_tree()

        t.remove(3)
        r"""
              8
             / \
            4   10
           / \    \
          1   6    14
             / \   /
            5   7 13
        """
        assert t.root is not None
        assert t.root.left is not None
        assert t.root.left.left is not None
        assert t.root.left.right is not None
        assert t.root.left.right.left is not None
        assert t.root.left.right.right is not None
        assert t.root.left.label == 4
        assert t.root.left.right.label == 6
        assert t.root.left.left.label == 1
        assert t.root.left.right.right.label == 7
        assert t.root.left.right.left.label == 5
        assert t.root.left.parent == t.root
        assert t.root.left.right.parent == t.root.left
        assert t.root.left.left.parent == t.root.left
        assert t.root.left.right.left.parent == t.root.left.right

    def test_empty(self) -> None:
        t = self._get_binary_search_tree()
        t.empty()
        assert t.root is None

    def test_is_empty(self) -> None:
        t = self._get_binary_search_tree()
        assert not t.is_empty()

        t.empty()
        assert t.is_empty()

    def test_exists(self) -> None:
        t = self._get_binary_search_tree()

        assert t.exists(6)
        assert not t.exists(-1)

    def test_get_max_label(self) -> None:
        t = self._get_binary_search_tree()

        assert t.get_max_label() == 14

        t.empty()
        with pytest.raises(ValueError):
            t.get_max_label()

    def test_get_min_label(self) -> None:
        t = self._get_binary_search_tree()

        assert t.get_min_label() == 1

        t.empty()
        with pytest.raises(ValueError):
            t.get_min_label()

    def test_inorder_traversal(self) -> None:
        t = self._get_binary_search_tree()

        inorder_traversal_nodes = [i.label for i in t.inorder_traversal()]
        assert inorder_traversal_nodes == [1, 3, 4, 5, 6, 7, 8, 10, 13, 14]

    def test_preorder_traversal(self) -> None:
        t = self._get_binary_search_tree()

        preorder_traversal_nodes = [i.label for i in t.preorder_traversal()]
        assert preorder_traversal_nodes == [8, 3, 1, 6, 4, 5, 7, 10, 14, 13]


def binary_search_tree_example() -> None:
    r"""
    Example
                  8
                 / \
                3   10
               / \    \
              1   6    14
                 / \   /
                4   7 13
                \
                5

    Example After Deletion
                  4
                 / \
                1   7
                     \
                      5

    """

    t = BinarySearchTree()
    t.put(8)
    t.put(3)
    t.put(6)
    t.put(1)
    t.put(10)
    t.put(14)
    t.put(13)
    t.put(4)
    t.put(7)
    t.put(5)

    print(
        """
            8
           / \\
          3   10
         / \\    \\
        1   6    14
           / \\   /
          4   7 13
           \\
            5
        """
    )

    print("Label 6 exists:", t.exists(6))
    print("Label 13 exists:", t.exists(13))
    print("Label -1 exists:", t.exists(-1))
    print("Label 12 exists:", t.exists(12))

    # Prints all the elements of the list in inorder traversal
    inorder_traversal_nodes = [i.label for i in t.inorder_traversal()]
    print("Inorder traversal:", inorder_traversal_nodes)

    # Prints all the elements of the list in preorder traversal
    preorder_traversal_nodes = [i.label for i in t.preorder_traversal()]
    print("Preorder traversal:", preorder_traversal_nodes)

    print("Max. label:", t.get_max_label())
    print("Min. label:", t.get_min_label())

    # Delete elements
    print("\nDeleting elements 13, 10, 8, 3, 6, 14")
    print(
        """
          4
         / \\
        1   7
             \\
              5
        """
    )
    t.remove(13)
    t.remove(10)
    t.remove(8)
    t.remove(3)
    t.remove(6)
    t.remove(14)

    # Prints all the elements of the list in inorder traversal after delete
    inorder_traversal_nodes = [i.label for i in t.inorder_traversal()]
    print("Inorder traversal after delete:", inorder_traversal_nodes)

    # Prints all the elements of the list in preorder traversal after delete
    preorder_traversal_nodes = [i.label for i in t.preorder_traversal()]
    print("Preorder traversal after delete:", preorder_traversal_nodes)

    print("Max. label:", t.get_max_label())
    print("Min. label:", t.get_min_label())


if __name__ == "__main__":
    binary_search_tree_example()


================================================
File: data_structures/binary_tree/binary_tree_mirror.py
================================================
"""
Problem Description:
Given a binary tree, return its mirror.
"""


def binary_tree_mirror_dict(binary_tree_mirror_dictionary: dict, root: int):
    if not root or root not in binary_tree_mirror_dictionary:
        return
    left_child, right_child = binary_tree_mirror_dictionary[root][:2]
    binary_tree_mirror_dictionary[root] = [right_child, left_child]
    binary_tree_mirror_dict(binary_tree_mirror_dictionary, left_child)
    binary_tree_mirror_dict(binary_tree_mirror_dictionary, right_child)


def binary_tree_mirror(binary_tree: dict, root: int = 1) -> dict:
    """
    >>> binary_tree_mirror({ 1: [2,3], 2: [4,5], 3: [6,7], 7: [8,9]}, 1)
    {1: [3, 2], 2: [5, 4], 3: [7, 6], 7: [9, 8]}
    >>> binary_tree_mirror({ 1: [2,3], 2: [4,5], 3: [6,7], 4: [10,11]}, 1)
    {1: [3, 2], 2: [5, 4], 3: [7, 6], 4: [11, 10]}
    >>> binary_tree_mirror({ 1: [2,3], 2: [4,5], 3: [6,7], 4: [10,11]}, 5)
    Traceback (most recent call last):
        ...
    ValueError: root 5 is not present in the binary_tree
    >>> binary_tree_mirror({}, 5)
    Traceback (most recent call last):
        ...
    ValueError: binary tree cannot be empty
    """
    if not binary_tree:
        raise ValueError("binary tree cannot be empty")
    if root not in binary_tree:
        msg = f"root {root} is not present in the binary_tree"
        raise ValueError(msg)
    binary_tree_mirror_dictionary = dict(binary_tree)
    binary_tree_mirror_dict(binary_tree_mirror_dictionary, root)
    return binary_tree_mirror_dictionary


if __name__ == "__main__":
    binary_tree = {1: [2, 3], 2: [4, 5], 3: [6, 7], 7: [8, 9]}
    print(f"Binary tree: {binary_tree}")
    binary_tree_mirror_dictionary = binary_tree_mirror(binary_tree, 5)
    print(f"Binary tree mirror: {binary_tree_mirror_dictionary}")


================================================
File: data_structures/binary_tree/binary_tree_node_sum.py
================================================
"""
Sum of all nodes in a binary tree.

Python implementation:
    O(n) time complexity - Recurses through :meth:`depth_first_search`
                            with each element.
    O(n) space complexity - At any point in time maximum number of stack
                            frames that could be in memory is `n`
"""

from __future__ import annotations

from collections.abc import Iterator


class Node:
    """
    A Node has a value variable and pointers to Nodes to its left and right.
    """

    def __init__(self, value: int) -> None:
        self.value = value
        self.left: Node | None = None
        self.right: Node | None = None


class BinaryTreeNodeSum:
    r"""
    The below tree looks like this
        10
       /  \
      5   -3
     /    / \
    12   8  0

    >>> tree = Node(10)
    >>> sum(BinaryTreeNodeSum(tree))
    10

    >>> tree.left = Node(5)
    >>> sum(BinaryTreeNodeSum(tree))
    15

    >>> tree.right = Node(-3)
    >>> sum(BinaryTreeNodeSum(tree))
    12

    >>> tree.left.left = Node(12)
    >>> sum(BinaryTreeNodeSum(tree))
    24

    >>> tree.right.left = Node(8)
    >>> tree.right.right = Node(0)
    >>> sum(BinaryTreeNodeSum(tree))
    32
    """

    def __init__(self, tree: Node) -> None:
        self.tree = tree

    def depth_first_search(self, node: Node | None) -> int:
        if node is None:
            return 0
        return node.value + (
            self.depth_first_search(node.left) + self.depth_first_search(node.right)
        )

    def __iter__(self) -> Iterator[int]:
        yield self.depth_first_search(self.tree)


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/binary_tree/binary_tree_path_sum.py
================================================
"""
Given the root of a binary tree and an integer target,
find the number of paths where the sum of the values
along the path equals target.


Leetcode reference: https://leetcode.com/problems/path-sum-iii/
"""

from __future__ import annotations


class Node:
    """
    A Node has value variable and pointers to Nodes to its left and right.
    """

    def __init__(self, value: int) -> None:
        self.value = value
        self.left: Node | None = None
        self.right: Node | None = None


class BinaryTreePathSum:
    r"""
    The below tree looks like this
          10
         /  \
        5   -3
       / \    \
      3   2    11
     / \   \
    3  -2   1


    >>> tree = Node(10)
    >>> tree.left = Node(5)
    >>> tree.right = Node(-3)
    >>> tree.left.left = Node(3)
    >>> tree.left.right = Node(2)
    >>> tree.right.right = Node(11)
    >>> tree.left.left.left = Node(3)
    >>> tree.left.left.right = Node(-2)
    >>> tree.left.right.right = Node(1)

    >>> BinaryTreePathSum().path_sum(tree, 8)
    3
    >>> BinaryTreePathSum().path_sum(tree, 7)
    2
    >>> tree.right.right = Node(10)
    >>> BinaryTreePathSum().path_sum(tree, 8)
    2
    """

    target: int

    def __init__(self) -> None:
        self.paths = 0

    def depth_first_search(self, node: Node | None, path_sum: int) -> None:
        if node is None:
            return

        if path_sum == self.target:
            self.paths += 1

        if node.left:
            self.depth_first_search(node.left, path_sum + node.left.value)
        if node.right:
            self.depth_first_search(node.right, path_sum + node.right.value)

    def path_sum(self, node: Node | None, target: int | None = None) -> int:
        if node is None:
            return 0
        if target is not None:
            self.target = target

        self.depth_first_search(node, node.value)
        self.path_sum(node.left)
        self.path_sum(node.right)

        return self.paths


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/binary_tree/binary_tree_traversals.py
================================================
from __future__ import annotations

from collections import deque
from collections.abc import Generator
from dataclasses import dataclass


# https://en.wikipedia.org/wiki/Tree_traversal
@dataclass
class Node:
    data: int
    left: Node | None = None
    right: Node | None = None


def make_tree() -> Node | None:
    r"""
    The below tree
        1
       / \
      2   3
     / \
    4   5
    """
    tree = Node(1)
    tree.left = Node(2)
    tree.right = Node(3)
    tree.left.left = Node(4)
    tree.left.right = Node(5)
    return tree


def preorder(root: Node | None) -> Generator[int]:
    """
    Pre-order traversal visits root node, left subtree, right subtree.
    >>> list(preorder(make_tree()))
    [1, 2, 4, 5, 3]
    """
    if not root:
        return
    yield root.data
    yield from preorder(root.left)
    yield from preorder(root.right)


def postorder(root: Node | None) -> Generator[int]:
    """
    Post-order traversal visits left subtree, right subtree, root node.
    >>> list(postorder(make_tree()))
    [4, 5, 2, 3, 1]
    """
    if not root:
        return
    yield from postorder(root.left)
    yield from postorder(root.right)
    yield root.data


def inorder(root: Node | None) -> Generator[int]:
    """
    In-order traversal visits left subtree, root node, right subtree.
    >>> list(inorder(make_tree()))
    [4, 2, 5, 1, 3]
    """
    if not root:
        return
    yield from inorder(root.left)
    yield root.data
    yield from inorder(root.right)


def reverse_inorder(root: Node | None) -> Generator[int]:
    """
    Reverse in-order traversal visits right subtree, root node, left subtree.
    >>> list(reverse_inorder(make_tree()))
    [3, 1, 5, 2, 4]
    """
    if not root:
        return
    yield from reverse_inorder(root.right)
    yield root.data
    yield from reverse_inorder(root.left)


def height(root: Node | None) -> int:
    """
    Recursive function for calculating the height of the binary tree.
    >>> height(None)
    0
    >>> height(make_tree())
    3
    """
    return (max(height(root.left), height(root.right)) + 1) if root else 0


def level_order(root: Node | None) -> Generator[int]:
    """
    Returns a list of nodes value from a whole binary tree in Level Order Traverse.
    Level Order traverse: Visit nodes of the tree level-by-level.
    >>> list(level_order(make_tree()))
    [1, 2, 3, 4, 5]
    """

    if root is None:
        return

    process_queue = deque([root])

    while process_queue:
        node = process_queue.popleft()
        yield node.data

        if node.left:
            process_queue.append(node.left)
        if node.right:
            process_queue.append(node.right)


def get_nodes_from_left_to_right(root: Node | None, level: int) -> Generator[int]:
    """
    Returns a list of nodes value from a particular level:
    Left to right direction of the binary tree.
    >>> list(get_nodes_from_left_to_right(make_tree(), 1))
    [1]
    >>> list(get_nodes_from_left_to_right(make_tree(), 2))
    [2, 3]
    """

    def populate_output(root: Node | None, level: int) -> Generator[int]:
        if not root:
            return
        if level == 1:
            yield root.data
        elif level > 1:
            yield from populate_output(root.left, level - 1)
            yield from populate_output(root.right, level - 1)

    yield from populate_output(root, level)


def get_nodes_from_right_to_left(root: Node | None, level: int) -> Generator[int]:
    """
    Returns a list of nodes value from a particular level:
    Right to left direction of the binary tree.
    >>> list(get_nodes_from_right_to_left(make_tree(), 1))
    [1]
    >>> list(get_nodes_from_right_to_left(make_tree(), 2))
    [3, 2]
    """

    def populate_output(root: Node | None, level: int) -> Generator[int]:
        if not root:
            return
        if level == 1:
            yield root.data
        elif level > 1:
            yield from populate_output(root.right, level - 1)
            yield from populate_output(root.left, level - 1)

    yield from populate_output(root, level)


def zigzag(root: Node | None) -> Generator[int]:
    """
    ZigZag traverse:
    Returns a list of nodes value from left to right and right to left, alternatively.
    >>> list(zigzag(make_tree()))
    [1, 3, 2, 4, 5]
    """
    if root is None:
        return

    flag = 0
    height_tree = height(root)

    for h in range(1, height_tree + 1):
        if not flag:
            yield from get_nodes_from_left_to_right(root, h)
            flag = 1
        else:
            yield from get_nodes_from_right_to_left(root, h)
            flag = 0


def main() -> None:  # Main function for testing.
    # Create binary tree.
    root = make_tree()

    # All Traversals of the binary are as follows:
    print(f"In-order Traversal: {list(inorder(root))}")
    print(f"Reverse In-order Traversal: {list(reverse_inorder(root))}")
    print(f"Pre-order Traversal: {list(preorder(root))}")
    print(f"Post-order Traversal: {list(postorder(root))}", "\n")

    print(f"Height of Tree: {height(root)}", "\n")

    print("Complete Level Order Traversal: ")
    print(f"{list(level_order(root))} \n")

    print("Level-wise order Traversal: ")

    for level in range(1, height(root) + 1):
        print(f"Level {level}:", list(get_nodes_from_left_to_right(root, level=level)))

    print("\nZigZag order Traversal: ")
    print(f"{list(zigzag(root))}")


if __name__ == "__main__":
    import doctest

    doctest.testmod()
    main()


================================================
File: data_structures/binary_tree/diameter_of_binary_tree.py
================================================
"""
The diameter/width of a tree is defined as the number of nodes on the longest path
between two end nodes.
"""

from __future__ import annotations

from dataclasses import dataclass


@dataclass
class Node:
    data: int
    left: Node | None = None
    right: Node | None = None

    def depth(self) -> int:
        """
        >>> root = Node(1)
        >>> root.depth()
        1
        >>> root.left = Node(2)
        >>> root.depth()
        2
        >>> root.left.depth()
        1
        >>> root.right = Node(3)
        >>> root.depth()
        2
        """
        left_depth = self.left.depth() if self.left else 0
        right_depth = self.right.depth() if self.right else 0
        return max(left_depth, right_depth) + 1

    def diameter(self) -> int:
        """
        >>> root = Node(1)
        >>> root.diameter()
        1
        >>> root.left = Node(2)
        >>> root.diameter()
        2
        >>> root.left.diameter()
        1
        >>> root.right = Node(3)
        >>> root.diameter()
        3
        """
        left_depth = self.left.depth() if self.left else 0
        right_depth = self.right.depth() if self.right else 0
        return left_depth + right_depth + 1


if __name__ == "__main__":
    from doctest import testmod

    testmod()
    root = Node(1)
    root.left = Node(2)
    root.right = Node(3)
    root.left.left = Node(4)
    root.left.right = Node(5)
    r"""
    Constructed binary tree is
        1
       / \
      2	  3
     / \
    4	 5
    """
    print(f"{root.diameter() = }")  # 4
    print(f"{root.left.diameter() = }")  # 3
    print(f"{root.right.diameter() = }")  # 1


================================================
File: data_structures/binary_tree/diff_views_of_binary_tree.py
================================================
r"""
Problem: Given root of a binary tree, return the:
1. binary-tree-right-side-view
2. binary-tree-left-side-view
3. binary-tree-top-side-view
4. binary-tree-bottom-side-view
"""

from __future__ import annotations

from collections import defaultdict
from dataclasses import dataclass


@dataclass
class TreeNode:
    val: int
    left: TreeNode | None = None
    right: TreeNode | None = None


def make_tree() -> TreeNode:
    """
    >>> make_tree().val
    3
    """
    return TreeNode(3, TreeNode(9), TreeNode(20, TreeNode(15), TreeNode(7)))


def binary_tree_right_side_view(root: TreeNode) -> list[int]:
    r"""
    Function returns the right side view of binary tree.

       3       <-  3
     / \
    9   20    <-  20
       /  \
      15   7  <-  7

    >>> binary_tree_right_side_view(make_tree())
    [3, 20, 7]
    >>> binary_tree_right_side_view(None)
    []
    """

    def depth_first_search(
        root: TreeNode | None, depth: int, right_view: list[int]
    ) -> None:
        """
        A depth first search preorder traversal to append the values at
        right side of tree.
        """
        if not root:
            return

        if depth == len(right_view):
            right_view.append(root.val)

        depth_first_search(root.right, depth + 1, right_view)
        depth_first_search(root.left, depth + 1, right_view)

    right_view: list = []
    if not root:
        return right_view

    depth_first_search(root, 0, right_view)
    return right_view


def binary_tree_left_side_view(root: TreeNode) -> list[int]:
    r"""
    Function returns the left side view of binary tree.

    3  ->    3
            / \
    9  ->  9   20
              /  \
    15 ->    15   7

    >>> binary_tree_left_side_view(make_tree())
    [3, 9, 15]
    >>> binary_tree_left_side_view(None)
    []
    """

    def depth_first_search(
        root: TreeNode | None, depth: int, left_view: list[int]
    ) -> None:
        """
        A depth first search preorder traversal to append the values
        at left side of tree.
        """
        if not root:
            return

        if depth == len(left_view):
            left_view.append(root.val)

        depth_first_search(root.left, depth + 1, left_view)
        depth_first_search(root.right, depth + 1, left_view)

    left_view: list = []
    if not root:
        return left_view

    depth_first_search(root, 0, left_view)
    return left_view


def binary_tree_top_side_view(root: TreeNode) -> list[int]:
    r"""
    Function returns the top side view of binary tree.

    9 3 20 7
    ⬇ ⬇ ⬇  ⬇

      3
     / \
    9   20
       /  \
      15   7

    >>> binary_tree_top_side_view(make_tree())
    [9, 3, 20, 7]
    >>> binary_tree_top_side_view(None)
    []
    """

    def breadth_first_search(root: TreeNode, top_view: list[int]) -> None:
        """
        A breadth first search traversal with defaultdict ds to append
        the values of tree from top view
        """
        queue = [(root, 0)]
        lookup = defaultdict(list)

        while queue:
            first = queue.pop(0)
            node, hd = first

            lookup[hd].append(node.val)

            if node.left:
                queue.append((node.left, hd - 1))
            if node.right:
                queue.append((node.right, hd + 1))

        for pair in sorted(lookup.items(), key=lambda each: each[0]):
            top_view.append(pair[1][0])

    top_view: list = []
    if not root:
        return top_view

    breadth_first_search(root, top_view)
    return top_view


def binary_tree_bottom_side_view(root: TreeNode) -> list[int]:
    r"""
    Function returns the bottom side view of binary tree

      3
     / \
    9   20
       /  \
      15   7
    ↑  ↑ ↑  ↑
    9 15 20 7

    >>> binary_tree_bottom_side_view(make_tree())
    [9, 15, 20, 7]
    >>> binary_tree_bottom_side_view(None)
    []
    """
    from collections import defaultdict

    def breadth_first_search(root: TreeNode, bottom_view: list[int]) -> None:
        """
        A breadth first search traversal with defaultdict ds to append
        the values of tree from bottom view
        """
        queue = [(root, 0)]
        lookup = defaultdict(list)

        while queue:
            first = queue.pop(0)
            node, hd = first
            lookup[hd].append(node.val)

            if node.left:
                queue.append((node.left, hd - 1))
            if node.right:
                queue.append((node.right, hd + 1))

        for pair in sorted(lookup.items(), key=lambda each: each[0]):
            bottom_view.append(pair[1][-1])

    bottom_view: list = []
    if not root:
        return bottom_view

    breadth_first_search(root, bottom_view)
    return bottom_view


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/binary_tree/distribute_coins.py
================================================
"""
Author  : Alexander Pantyukhin
Date    : November 7, 2022

Task:
You are given a tree root of a binary tree with n nodes, where each node has
node.data coins. There are exactly n coins in whole tree.

In one move, we may choose two adjacent nodes and move one coin from one node
to another. A move may be from parent to child, or from child to parent.

Return the minimum number of moves required to make every node have exactly one coin.

Example 1:

   3
  / \
 0   0

Result: 2

Example 2:

   0
  / \
 3   0

Result 3

leetcode: https://leetcode.com/problems/distribute-coins-in-binary-tree/

Implementation notes:
User depth-first search approach.

Let n is the number of nodes in tree
Runtime: O(n)
Space: O(1)
"""

from __future__ import annotations

from dataclasses import dataclass
from typing import NamedTuple


@dataclass
class TreeNode:
    data: int
    left: TreeNode | None = None
    right: TreeNode | None = None


class CoinsDistribResult(NamedTuple):
    moves: int
    excess: int


def distribute_coins(root: TreeNode | None) -> int:
    """
    >>> distribute_coins(TreeNode(3, TreeNode(0), TreeNode(0)))
    2
    >>> distribute_coins(TreeNode(0, TreeNode(3), TreeNode(0)))
    3
    >>> distribute_coins(TreeNode(0, TreeNode(0), TreeNode(3)))
    3
    >>> distribute_coins(None)
    0
    >>> distribute_coins(TreeNode(0, TreeNode(0), TreeNode(0)))
    Traceback (most recent call last):
     ...
    ValueError: The nodes number should be same as the number of coins
    >>> distribute_coins(TreeNode(0, TreeNode(1), TreeNode(1)))
    Traceback (most recent call last):
     ...
    ValueError: The nodes number should be same as the number of coins
    """

    if root is None:
        return 0

    # Validation
    def count_nodes(node: TreeNode | None) -> int:
        """
        >>> count_nodes(None)
        0
        """
        if node is None:
            return 0

        return count_nodes(node.left) + count_nodes(node.right) + 1

    def count_coins(node: TreeNode | None) -> int:
        """
        >>> count_coins(None)
        0
        """
        if node is None:
            return 0

        return count_coins(node.left) + count_coins(node.right) + node.data

    if count_nodes(root) != count_coins(root):
        raise ValueError("The nodes number should be same as the number of coins")

    # Main calculation
    def get_distrib(node: TreeNode | None) -> CoinsDistribResult:
        """
        >>> get_distrib(None)
        namedtuple("CoinsDistribResult", "0 2")
        """

        if node is None:
            return CoinsDistribResult(0, 1)

        left_distrib_moves, left_distrib_excess = get_distrib(node.left)
        right_distrib_moves, right_distrib_excess = get_distrib(node.right)

        coins_to_left = 1 - left_distrib_excess
        coins_to_right = 1 - right_distrib_excess

        result_moves = (
            left_distrib_moves
            + right_distrib_moves
            + abs(coins_to_left)
            + abs(coins_to_right)
        )
        result_excess = node.data - coins_to_left - coins_to_right

        return CoinsDistribResult(result_moves, result_excess)

    return get_distrib(root)[0]


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/binary_tree/fenwick_tree.py
================================================
from copy import deepcopy


class FenwickTree:
    """
    Fenwick Tree

    More info: https://en.wikipedia.org/wiki/Fenwick_tree
    """

    def __init__(self, arr: list[int] | None = None, size: int | None = None) -> None:
        """
        Constructor for the Fenwick tree

        Parameters:
            arr (list): list of elements to initialize the tree with (optional)
            size (int): size of the Fenwick tree (if arr is None)
        """

        if arr is None and size is not None:
            self.size = size
            self.tree = [0] * size
        elif arr is not None:
            self.init(arr)
        else:
            raise ValueError("Either arr or size must be specified")

    def init(self, arr: list[int]) -> None:
        """
        Initialize the Fenwick tree with arr in O(N)

        Parameters:
            arr (list): list of elements to initialize the tree with

        Returns:
            None

        >>> a = [1, 2, 3, 4, 5]
        >>> f1 = FenwickTree(a)
        >>> f2 = FenwickTree(size=len(a))
        >>> for index, value in enumerate(a):
        ...     f2.add(index, value)
        >>> f1.tree == f2.tree
        True
        """
        self.size = len(arr)
        self.tree = deepcopy(arr)
        for i in range(1, self.size):
            j = self.next_(i)
            if j < self.size:
                self.tree[j] += self.tree[i]

    def get_array(self) -> list[int]:
        """
        Get the Normal Array of the Fenwick tree in O(N)

        Returns:
            list: Normal Array of the Fenwick tree

        >>> a = [i for i in range(128)]
        >>> f = FenwickTree(a)
        >>> f.get_array() == a
        True
        """
        arr = self.tree[:]
        for i in range(self.size - 1, 0, -1):
            j = self.next_(i)
            if j < self.size:
                arr[j] -= arr[i]
        return arr

    @staticmethod
    def next_(index: int) -> int:
        return index + (index & (-index))

    @staticmethod
    def prev(index: int) -> int:
        return index - (index & (-index))

    def add(self, index: int, value: int) -> None:
        """
        Add a value to index in O(lg N)

        Parameters:
            index (int): index to add value to
            value (int): value to add to index

        Returns:
            None

        >>> f = FenwickTree([1, 2, 3, 4, 5])
        >>> f.add(0, 1)
        >>> f.add(1, 2)
        >>> f.add(2, 3)
        >>> f.add(3, 4)
        >>> f.add(4, 5)
        >>> f.get_array()
        [2, 4, 6, 8, 10]
        """
        if index == 0:
            self.tree[0] += value
            return
        while index < self.size:
            self.tree[index] += value
            index = self.next_(index)

    def update(self, index: int, value: int) -> None:
        """
        Set the value of index in O(lg N)

        Parameters:
            index (int): index to set value to
            value (int): value to set in index

        Returns:
            None

        >>> f = FenwickTree([5, 4, 3, 2, 1])
        >>> f.update(0, 1)
        >>> f.update(1, 2)
        >>> f.update(2, 3)
        >>> f.update(3, 4)
        >>> f.update(4, 5)
        >>> f.get_array()
        [1, 2, 3, 4, 5]
        """
        self.add(index, value - self.get(index))

    def prefix(self, right: int) -> int:
        """
        Prefix sum of all elements in [0, right) in O(lg N)

        Parameters:
            right (int): right bound of the query (exclusive)

        Returns:
            int: sum of all elements in [0, right)

        >>> a = [i for i in range(128)]
        >>> f = FenwickTree(a)
        >>> res = True
        >>> for i in range(len(a)):
        ...     res = res and f.prefix(i) == sum(a[:i])
        >>> res
        True
        """
        if right == 0:
            return 0
        result = self.tree[0]
        right -= 1  # make right inclusive
        while right > 0:
            result += self.tree[right]
            right = self.prev(right)
        return result

    def query(self, left: int, right: int) -> int:
        """
        Query the sum of all elements in [left, right) in O(lg N)

        Parameters:
            left (int): left bound of the query (inclusive)
            right (int): right bound of the query (exclusive)

        Returns:
            int: sum of all elements in [left, right)

        >>> a = [i for i in range(128)]
        >>> f = FenwickTree(a)
        >>> res = True
        >>> for i in range(len(a)):
        ...     for j in range(i + 1, len(a)):
        ...         res = res and f.query(i, j) == sum(a[i:j])
        >>> res
        True
        """
        return self.prefix(right) - self.prefix(left)

    def get(self, index: int) -> int:
        """
        Get value at index in O(lg N)

        Parameters:
            index (int): index to get the value

        Returns:
            int: Value of element at index

        >>> a = [i for i in range(128)]
        >>> f = FenwickTree(a)
        >>> res = True
        >>> for i in range(len(a)):
        ...     res = res and f.get(i) == a[i]
        >>> res
        True
        """
        return self.query(index, index + 1)

    def rank_query(self, value: int) -> int:
        """
        Find the largest index with prefix(i) <= value in O(lg N)
        NOTE: Requires that all values are non-negative!

        Parameters:
            value (int): value to find the largest index of

        Returns:
            -1: if value is smaller than all elements in prefix sum
            int: largest index with prefix(i) <= value

        >>> f = FenwickTree([1, 2, 0, 3, 0, 5])
        >>> f.rank_query(0)
        -1
        >>> f.rank_query(2)
        0
        >>> f.rank_query(1)
        0
        >>> f.rank_query(3)
        2
        >>> f.rank_query(5)
        2
        >>> f.rank_query(6)
        4
        >>> f.rank_query(11)
        5
        """
        value -= self.tree[0]
        if value < 0:
            return -1

        j = 1  # Largest power of 2 <= size
        while j * 2 < self.size:
            j *= 2

        i = 0

        while j > 0:
            if i + j < self.size and self.tree[i + j] <= value:
                value -= self.tree[i + j]
                i += j
            j //= 2
        return i


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/binary_tree/flatten_binarytree_to_linkedlist.py
================================================
"""
Binary Tree Flattening Algorithm

This code defines an algorithm to flatten a binary tree into a linked list
represented using the right pointers of the tree nodes. It uses in-place
flattening and demonstrates the flattening process along with a display
function to visualize the flattened linked list.
https://www.geeksforgeeks.org/flatten-a-binary-tree-into-linked-list

Author: Arunkumar A
Date: 04/09/2023
"""

from __future__ import annotations


class TreeNode:
    """
    A TreeNode has data variable and pointers to TreeNode objects
    for its left and right children.
    """

    def __init__(self, data: int) -> None:
        self.data = data
        self.left: TreeNode | None = None
        self.right: TreeNode | None = None


def build_tree() -> TreeNode:
    """
    Build and return a sample binary tree.

    Returns:
        TreeNode: The root of the binary tree.

    Examples:
        >>> root = build_tree()
        >>> root.data
        1
        >>> root.left.data
        2
        >>> root.right.data
        5
        >>> root.left.left.data
        3
        >>> root.left.right.data
        4
        >>> root.right.right.data
        6
    """
    root = TreeNode(1)
    root.left = TreeNode(2)
    root.right = TreeNode(5)
    root.left.left = TreeNode(3)
    root.left.right = TreeNode(4)
    root.right.right = TreeNode(6)
    return root


def flatten(root: TreeNode | None) -> None:
    """
    Flatten a binary tree into a linked list in-place, where the linked list is
    represented using the right pointers of the tree nodes.

    Args:
        root (TreeNode): The root of the binary tree to be flattened.

    Examples:
        >>> root = TreeNode(1)
        >>> root.left = TreeNode(2)
        >>> root.right = TreeNode(5)
        >>> root.left.left = TreeNode(3)
        >>> root.left.right = TreeNode(4)
        >>> root.right.right = TreeNode(6)
        >>> flatten(root)
        >>> root.data
        1
        >>> root.right.right is None
        False
        >>> root.right.right = TreeNode(3)
        >>> root.right.right.right is None
        True
    """
    if not root:
        return

    # Flatten the left subtree
    flatten(root.left)

    # Save the right subtree
    right_subtree = root.right

    # Make the left subtree the new right subtree
    root.right = root.left
    root.left = None

    # Find the end of the new right subtree
    current = root
    while current.right:
        current = current.right

    # Append the original right subtree to the end
    current.right = right_subtree

    # Flatten the updated right subtree
    flatten(right_subtree)


def display_linked_list(root: TreeNode | None) -> None:
    """
    Display the flattened linked list.

    Args:
        root (TreeNode | None): The root of the flattened linked list.

    Examples:
        >>> root = TreeNode(1)
        >>> root.right = TreeNode(2)
        >>> root.right.right = TreeNode(3)
        >>> display_linked_list(root)
        1 2 3
        >>> root = None
        >>> display_linked_list(root)

    """
    current = root
    while current:
        if current.right is None:
            print(current.data, end="")
            break
        print(current.data, end=" ")
        current = current.right


if __name__ == "__main__":
    print("Flattened Linked List:")
    root = build_tree()
    flatten(root)
    display_linked_list(root)


================================================
File: data_structures/binary_tree/floor_and_ceiling.py
================================================
"""
In a binary search tree (BST):
* The floor of key 'k' is the maximum value that is smaller than or equal to 'k'.
* The ceiling of key 'k' is the minimum value that is greater than or equal to 'k'.

Reference:
https://bit.ly/46uB0a2

Author : Arunkumar
Date : 14th October 2023
"""

from __future__ import annotations

from collections.abc import Iterator
from dataclasses import dataclass


@dataclass
class Node:
    key: int
    left: Node | None = None
    right: Node | None = None

    def __iter__(self) -> Iterator[int]:
        if self.left:
            yield from self.left
        yield self.key
        if self.right:
            yield from self.right

    def __len__(self) -> int:
        return sum(1 for _ in self)


def floor_ceiling(root: Node | None, key: int) -> tuple[int | None, int | None]:
    """
    Find the floor and ceiling values for a given key in a Binary Search Tree (BST).

    Args:
        root: The root of the binary search tree.
        key: The key for which to find the floor and ceiling.

    Returns:
        A tuple containing the floor and ceiling values, respectively.

    Examples:
        >>> root = Node(10)
        >>> root.left = Node(5)
        >>> root.right = Node(20)
        >>> root.left.left = Node(3)
        >>> root.left.right = Node(7)
        >>> root.right.left = Node(15)
        >>> root.right.right = Node(25)
        >>> tuple(root)
        (3, 5, 7, 10, 15, 20, 25)
        >>> floor_ceiling(root, 8)
        (7, 10)
        >>> floor_ceiling(root, 14)
        (10, 15)
        >>> floor_ceiling(root, -1)
        (None, 3)
        >>> floor_ceiling(root, 30)
        (25, None)
    """
    floor_val = None
    ceiling_val = None

    while root:
        if root.key == key:
            floor_val = root.key
            ceiling_val = root.key
            break

        if key < root.key:
            ceiling_val = root.key
            root = root.left
        else:
            floor_val = root.key
            root = root.right

    return floor_val, ceiling_val


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/binary_tree/inorder_tree_traversal_2022.py
================================================
"""
Illustrate how to implement inorder traversal in binary search tree.
Author: Gurneet Singh
https://www.geeksforgeeks.org/tree-traversals-inorder-preorder-and-postorder/
"""


class BinaryTreeNode:
    """Defining the structure of BinaryTreeNode"""

    def __init__(self, data: int) -> None:
        self.data = data
        self.left_child: BinaryTreeNode | None = None
        self.right_child: BinaryTreeNode | None = None


def insert(node: BinaryTreeNode | None, new_value: int) -> BinaryTreeNode | None:
    """
    If the binary search tree is empty, make a new node and declare it as root.
    >>> node_a = BinaryTreeNode(12345)
    >>> node_b = insert(node_a, 67890)
    >>> node_a.left_child == node_b.left_child
    True
    >>> node_a.right_child == node_b.right_child
    True
    >>> node_a.data == node_b.data
    True
    """
    if node is None:
        node = BinaryTreeNode(new_value)
        return node

    # binary search tree is not empty,
    # so we will insert it into the tree
    # if new_value is less than value of data in node,
    #  add it to left subtree and proceed recursively
    if new_value < node.data:
        node.left_child = insert(node.left_child, new_value)
    else:
        # if new_value is greater than value of data in node,
        #  add it to right subtree and proceed recursively
        node.right_child = insert(node.right_child, new_value)
    return node


def inorder(node: None | BinaryTreeNode) -> list[int]:  # if node is None,return
    """
    >>> inorder(make_tree())
    [6, 10, 14, 15, 20, 25, 60]
    """
    if node:
        inorder_array = inorder(node.left_child)
        inorder_array = [*inorder_array, node.data]
        inorder_array = inorder_array + inorder(node.right_child)
    else:
        inorder_array = []
    return inorder_array


def make_tree() -> BinaryTreeNode | None:
    root = insert(None, 15)
    insert(root, 10)
    insert(root, 25)
    insert(root, 6)
    insert(root, 14)
    insert(root, 20)
    insert(root, 60)
    return root


def main() -> None:
    # main function
    root = make_tree()
    print("Printing values of binary search tree in Inorder Traversal.")
    inorder(root)


if __name__ == "__main__":
    import doctest

    doctest.testmod()
    main()


================================================
File: data_structures/binary_tree/is_sorted.py
================================================
"""
Given the root of a binary tree, determine if it is a valid binary search tree (BST).

A valid binary search tree is defined as follows:
- The left subtree of a node contains only nodes with keys less than the node's key.
- The right subtree of a node contains only nodes with keys greater than the node's key.
- Both the left and right subtrees must also be binary search trees.

In effect, a binary tree is a valid BST if its nodes are sorted in ascending order.
leetcode: https://leetcode.com/problems/validate-binary-search-tree/

If n is the number of nodes in the tree then:
Runtime: O(n)
Space: O(1)
"""

from __future__ import annotations

from collections.abc import Iterator
from dataclasses import dataclass


@dataclass
class Node:
    data: float
    left: Node | None = None
    right: Node | None = None

    def __iter__(self) -> Iterator[float]:
        """
        >>> root = Node(data=2.1)
        >>> list(root)
        [2.1]
        >>> root.left=Node(data=2.0)
        >>> list(root)
        [2.0, 2.1]
        >>> root.right=Node(data=2.2)
        >>> list(root)
        [2.0, 2.1, 2.2]
        """
        if self.left:
            yield from self.left
        yield self.data
        if self.right:
            yield from self.right

    @property
    def is_sorted(self) -> bool:
        """
        >>> Node(data='abc').is_sorted
        True
        >>> Node(data=2,
        ...      left=Node(data=1.999),
        ...      right=Node(data=3)).is_sorted
        True
        >>> Node(data=0,
        ...      left=Node(data=0),
        ...      right=Node(data=0)).is_sorted
        True
        >>> Node(data=0,
        ...      left=Node(data=-11),
        ...      right=Node(data=3)).is_sorted
        True
        >>> Node(data=5,
        ...      left=Node(data=1),
        ...      right=Node(data=4, left=Node(data=3))).is_sorted
        False
        >>> Node(data='a',
        ...      left=Node(data=1),
        ...      right=Node(data=4, left=Node(data=3))).is_sorted
        Traceback (most recent call last):
            ...
        TypeError: '<' not supported between instances of 'str' and 'int'
        >>> Node(data=2,
        ...      left=Node([]),
        ...      right=Node(data=4, left=Node(data=3))).is_sorted
        Traceback (most recent call last):
            ...
        TypeError: '<' not supported between instances of 'int' and 'list'
        """
        if self.left and (self.data < self.left.data or not self.left.is_sorted):
            return False
        return not (
            self.right and (self.data > self.right.data or not self.right.is_sorted)
        )


if __name__ == "__main__":
    import doctest

    doctest.testmod()
    tree = Node(data=2.1, left=Node(data=2.0), right=Node(data=2.2))
    print(f"Tree {list(tree)} is sorted: {tree.is_sorted = }.")
    assert tree.right
    tree.right.data = 2.0
    print(f"Tree {list(tree)} is sorted: {tree.is_sorted = }.")
    tree.right.data = 2.1
    print(f"Tree {list(tree)} is sorted: {tree.is_sorted = }.")


================================================
File: data_structures/binary_tree/is_sum_tree.py
================================================
"""
Is a binary tree a sum tree where the value of every non-leaf node is equal to the sum
of the values of its left and right subtrees?
https://www.geeksforgeeks.org/check-if-a-given-binary-tree-is-sumtree
"""

from __future__ import annotations

from collections.abc import Iterator
from dataclasses import dataclass


@dataclass
class Node:
    data: int
    left: Node | None = None
    right: Node | None = None

    def __iter__(self) -> Iterator[int]:
        """
        >>> root = Node(2)
        >>> list(root)
        [2]
        >>> root.left = Node(1)
        >>> tuple(root)
        (1, 2)
        """
        if self.left:
            yield from self.left
        yield self.data
        if self.right:
            yield from self.right

    def __len__(self) -> int:
        """
        >>> root = Node(2)
        >>> len(root)
        1
        >>> root.left = Node(1)
        >>> len(root)
        2
        """
        return sum(1 for _ in self)

    @property
    def is_sum_node(self) -> bool:
        """
        >>> root = Node(3)
        >>> root.is_sum_node
        True
        >>> root.left = Node(1)
        >>> root.is_sum_node
        False
        >>> root.right = Node(2)
        >>> root.is_sum_node
        True
        """
        if not self.left and not self.right:
            return True  # leaf nodes are considered sum nodes
        left_sum = sum(self.left) if self.left else 0
        right_sum = sum(self.right) if self.right else 0
        return all(
            (
                self.data == left_sum + right_sum,
                self.left.is_sum_node if self.left else True,
                self.right.is_sum_node if self.right else True,
            )
        )


@dataclass
class BinaryTree:
    root: Node

    def __iter__(self) -> Iterator[int]:
        """
        >>> list(BinaryTree.build_a_tree())
        [1, 2, 7, 11, 15, 29, 35, 40]
        """
        return iter(self.root)

    def __len__(self) -> int:
        """
        >>> len(BinaryTree.build_a_tree())
        8
        """
        return len(self.root)

    def __str__(self) -> str:
        """
        Returns a string representation of the inorder traversal of the binary tree.

        >>> str(list(BinaryTree.build_a_tree()))
        '[1, 2, 7, 11, 15, 29, 35, 40]'
        """
        return str(list(self))

    @property
    def is_sum_tree(self) -> bool:
        """
        >>> BinaryTree.build_a_tree().is_sum_tree
        False
        >>> BinaryTree.build_a_sum_tree().is_sum_tree
        True
        """
        return self.root.is_sum_node

    @classmethod
    def build_a_tree(cls) -> BinaryTree:
        r"""
        Create a binary tree with the specified structure:
              11
           /     \
          2       29
         / \     /  \
        1   7  15    40
                       \
                        35
        >>> list(BinaryTree.build_a_tree())
        [1, 2, 7, 11, 15, 29, 35, 40]
        """
        tree = BinaryTree(Node(11))
        root = tree.root
        root.left = Node(2)
        root.right = Node(29)
        root.left.left = Node(1)
        root.left.right = Node(7)
        root.right.left = Node(15)
        root.right.right = Node(40)
        root.right.right.left = Node(35)
        return tree

    @classmethod
    def build_a_sum_tree(cls) -> BinaryTree:
        r"""
        Create a binary tree with the specified structure:
             26
            /  \
          10    3
         /  \    \
        4    6    3
        >>> list(BinaryTree.build_a_sum_tree())
        [4, 10, 6, 26, 3, 3]
        """
        tree = BinaryTree(Node(26))
        root = tree.root
        root.left = Node(10)
        root.right = Node(3)
        root.left.left = Node(4)
        root.left.right = Node(6)
        root.right.right = Node(3)
        return tree


if __name__ == "__main__":
    from doctest import testmod

    testmod()
    tree = BinaryTree.build_a_tree()
    print(f"{tree} has {len(tree)} nodes and {tree.is_sum_tree = }.")
    tree = BinaryTree.build_a_sum_tree()
    print(f"{tree} has {len(tree)} nodes and {tree.is_sum_tree = }.")


================================================
File: data_structures/binary_tree/lazy_segment_tree.py
================================================
from __future__ import annotations

import math


class SegmentTree:
    def __init__(self, size: int) -> None:
        self.size = size
        # approximate the overall size of segment tree with given value
        self.segment_tree = [0 for i in range(4 * size)]
        # create array to store lazy update
        self.lazy = [0 for i in range(4 * size)]
        self.flag = [0 for i in range(4 * size)]  # flag for lazy update

    def left(self, idx: int) -> int:
        """
        >>> segment_tree = SegmentTree(15)
        >>> segment_tree.left(1)
        2
        >>> segment_tree.left(2)
        4
        >>> segment_tree.left(12)
        24
        """
        return idx * 2

    def right(self, idx: int) -> int:
        """
        >>> segment_tree = SegmentTree(15)
        >>> segment_tree.right(1)
        3
        >>> segment_tree.right(2)
        5
        >>> segment_tree.right(12)
        25
        """
        return idx * 2 + 1

    def build(
        self, idx: int, left_element: int, right_element: int, a: list[int]
    ) -> None:
        if left_element == right_element:
            self.segment_tree[idx] = a[left_element - 1]
        else:
            mid = (left_element + right_element) // 2
            self.build(self.left(idx), left_element, mid, a)
            self.build(self.right(idx), mid + 1, right_element, a)
            self.segment_tree[idx] = max(
                self.segment_tree[self.left(idx)], self.segment_tree[self.right(idx)]
            )

    def update(
        self, idx: int, left_element: int, right_element: int, a: int, b: int, val: int
    ) -> bool:
        """
        update with O(lg n) (Normal segment tree without lazy update will take O(nlg n)
        for each update)

        update(1, 1, size, a, b, v) for update val v to [a,b]
        """
        if self.flag[idx] is True:
            self.segment_tree[idx] = self.lazy[idx]
            self.flag[idx] = False
            if left_element != right_element:
                self.lazy[self.left(idx)] = self.lazy[idx]
                self.lazy[self.right(idx)] = self.lazy[idx]
                self.flag[self.left(idx)] = True
                self.flag[self.right(idx)] = True

        if right_element < a or left_element > b:
            return True
        if left_element >= a and right_element <= b:
            self.segment_tree[idx] = val
            if left_element != right_element:
                self.lazy[self.left(idx)] = val
                self.lazy[self.right(idx)] = val
                self.flag[self.left(idx)] = True
                self.flag[self.right(idx)] = True
            return True
        mid = (left_element + right_element) // 2
        self.update(self.left(idx), left_element, mid, a, b, val)
        self.update(self.right(idx), mid + 1, right_element, a, b, val)
        self.segment_tree[idx] = max(
            self.segment_tree[self.left(idx)], self.segment_tree[self.right(idx)]
        )
        return True

    # query with O(lg n)
    def query(
        self, idx: int, left_element: int, right_element: int, a: int, b: int
    ) -> int | float:
        """
        query(1, 1, size, a, b) for query max of [a,b]
        >>> A = [1, 2, -4, 7, 3, -5, 6, 11, -20, 9, 14, 15, 5, 2, -8]
        >>> segment_tree = SegmentTree(15)
        >>> segment_tree.build(1, 1, 15, A)
        >>> segment_tree.query(1, 1, 15, 4, 6)
        7
        >>> segment_tree.query(1, 1, 15, 7, 11)
        14
        >>> segment_tree.query(1, 1, 15, 7, 12)
        15
        """
        if self.flag[idx] is True:
            self.segment_tree[idx] = self.lazy[idx]
            self.flag[idx] = False
            if left_element != right_element:
                self.lazy[self.left(idx)] = self.lazy[idx]
                self.lazy[self.right(idx)] = self.lazy[idx]
                self.flag[self.left(idx)] = True
                self.flag[self.right(idx)] = True
        if right_element < a or left_element > b:
            return -math.inf
        if left_element >= a and right_element <= b:
            return self.segment_tree[idx]
        mid = (left_element + right_element) // 2
        q1 = self.query(self.left(idx), left_element, mid, a, b)
        q2 = self.query(self.right(idx), mid + 1, right_element, a, b)
        return max(q1, q2)

    def __str__(self) -> str:
        return str([self.query(1, 1, self.size, i, i) for i in range(1, self.size + 1)])


if __name__ == "__main__":
    A = [1, 2, -4, 7, 3, -5, 6, 11, -20, 9, 14, 15, 5, 2, -8]
    size = 15
    segt = SegmentTree(size)
    segt.build(1, 1, size, A)
    print(segt.query(1, 1, size, 4, 6))
    print(segt.query(1, 1, size, 7, 11))
    print(segt.query(1, 1, size, 7, 12))
    segt.update(1, 1, size, 1, 3, 111)
    print(segt.query(1, 1, size, 1, 15))
    segt.update(1, 1, size, 7, 8, 235)
    print(segt)


================================================
File: data_structures/binary_tree/lowest_common_ancestor.py
================================================
# https://en.wikipedia.org/wiki/Lowest_common_ancestor
# https://en.wikipedia.org/wiki/Breadth-first_search

from __future__ import annotations

from queue import Queue


def swap(a: int, b: int) -> tuple[int, int]:
    """
    Return a tuple (b, a) when given two integers a and b
    >>> swap(2,3)
    (3, 2)
    >>> swap(3,4)
    (4, 3)
    >>> swap(67, 12)
    (12, 67)
    """
    a ^= b
    b ^= a
    a ^= b
    return a, b


def create_sparse(max_node: int, parent: list[list[int]]) -> list[list[int]]:
    """
    creating sparse table which saves each nodes 2^i-th parent
    """
    j = 1
    while (1 << j) < max_node:
        for i in range(1, max_node + 1):
            parent[j][i] = parent[j - 1][parent[j - 1][i]]
        j += 1
    return parent


# returns lca of node u,v
def lowest_common_ancestor(
    u: int, v: int, level: list[int], parent: list[list[int]]
) -> int:
    # u must be deeper in the tree than v
    if level[u] < level[v]:
        u, v = swap(u, v)
    # making depth of u same as depth of v
    for i in range(18, -1, -1):
        if level[u] - (1 << i) >= level[v]:
            u = parent[i][u]
    # at the same depth if u==v that mean lca is found
    if u == v:
        return u
    # moving both nodes upwards till lca in found
    for i in range(18, -1, -1):
        if parent[i][u] not in [0, parent[i][v]]:
            u, v = parent[i][u], parent[i][v]
    # returning longest common ancestor of u,v
    return parent[0][u]


# runs a breadth first search from root node of the tree
def breadth_first_search(
    level: list[int],
    parent: list[list[int]],
    max_node: int,
    graph: dict[int, list[int]],
    root: int = 1,
) -> tuple[list[int], list[list[int]]]:
    """
    sets every nodes direct parent
    parent of root node is set to 0
    calculates depth of each node from root node
    """
    level[root] = 0
    q: Queue[int] = Queue(maxsize=max_node)
    q.put(root)
    while q.qsize() != 0:
        u = q.get()
        for v in graph[u]:
            if level[v] == -1:
                level[v] = level[u] + 1
                q.put(v)
                parent[0][v] = u
    return level, parent


def main() -> None:
    max_node = 13
    # initializing with 0
    parent = [[0 for _ in range(max_node + 10)] for _ in range(20)]
    # initializing with -1 which means every node is unvisited
    level = [-1 for _ in range(max_node + 10)]
    graph: dict[int, list[int]] = {
        1: [2, 3, 4],
        2: [5],
        3: [6, 7],
        4: [8],
        5: [9, 10],
        6: [11],
        7: [],
        8: [12, 13],
        9: [],
        10: [],
        11: [],
        12: [],
        13: [],
    }
    level, parent = breadth_first_search(level, parent, max_node, graph, 1)
    parent = create_sparse(max_node, parent)
    print("LCA of node 1 and 3 is: ", lowest_common_ancestor(1, 3, level, parent))
    print("LCA of node 5 and 6 is: ", lowest_common_ancestor(5, 6, level, parent))
    print("LCA of node 7 and 11 is: ", lowest_common_ancestor(7, 11, level, parent))
    print("LCA of node 6 and 7 is: ", lowest_common_ancestor(6, 7, level, parent))
    print("LCA of node 4 and 12 is: ", lowest_common_ancestor(4, 12, level, parent))
    print("LCA of node 8 and 8 is: ", lowest_common_ancestor(8, 8, level, parent))


if __name__ == "__main__":
    main()


================================================
File: data_structures/binary_tree/maximum_fenwick_tree.py
================================================
class MaxFenwickTree:
    """
    Maximum Fenwick Tree

    More info: https://cp-algorithms.com/data_structures/fenwick.html
    ---------
    >>> ft = MaxFenwickTree(5)
    >>> ft.query(0, 5)
    0
    >>> ft.update(4, 100)
    >>> ft.query(0, 5)
    100
    >>> ft.update(4, 0)
    >>> ft.update(2, 20)
    >>> ft.query(0, 5)
    20
    >>> ft.update(4, 10)
    >>> ft.query(2, 5)
    20
    >>> ft.query(1, 5)
    20
    >>> ft.update(2, 0)
    >>> ft.query(0, 5)
    10
    >>> ft = MaxFenwickTree(10000)
    >>> ft.update(255, 30)
    >>> ft.query(0, 10000)
    30
    >>> ft = MaxFenwickTree(6)
    >>> ft.update(5, 1)
    >>> ft.query(5, 6)
    1
    >>> ft = MaxFenwickTree(6)
    >>> ft.update(0, 1000)
    >>> ft.query(0, 1)
    1000
    """

    def __init__(self, size: int) -> None:
        """
        Create empty Maximum Fenwick Tree with specified size

        Parameters:
            size: size of Array

        Returns:
            None
        """
        self.size = size
        self.arr = [0] * size
        self.tree = [0] * size

    @staticmethod
    def get_next(index: int) -> int:
        """
        Get next index in O(1)
        """
        return index | (index + 1)

    @staticmethod
    def get_prev(index: int) -> int:
        """
        Get previous index in O(1)
        """
        return (index & (index + 1)) - 1

    def update(self, index: int, value: int) -> None:
        """
        Set index to value in O(lg^2 N)

        Parameters:
            index: index to update
            value: value to set

        Returns:
            None
        """
        self.arr[index] = value
        while index < self.size:
            current_left_border = self.get_prev(index) + 1
            if current_left_border == index:
                self.tree[index] = value
            else:
                self.tree[index] = max(value, current_left_border, index)
            index = self.get_next(index)

    def query(self, left: int, right: int) -> int:
        """
        Answer the query of maximum range [l, r) in O(lg^2 N)

        Parameters:
            left: left index of query range (inclusive)
            right: right index of query range (exclusive)

        Returns:
            Maximum value of range [left, right)
        """
        right -= 1  # Because of right is exclusive
        result = 0
        while left <= right:
            current_left = self.get_prev(right)
            if left <= current_left:
                result = max(result, self.tree[right])
                right = current_left
            else:
                result = max(result, self.arr[right])
                right -= 1
        return result


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/binary_tree/maximum_sum_bst.py
================================================
from __future__ import annotations

import sys
from dataclasses import dataclass

INT_MIN = -sys.maxsize + 1
INT_MAX = sys.maxsize - 1


@dataclass
class TreeNode:
    val: int = 0
    left: TreeNode | None = None
    right: TreeNode | None = None


def max_sum_bst(root: TreeNode | None) -> int:
    """
    The solution traverses a binary tree to find the maximum sum of
    keys in any subtree that is a Binary Search Tree (BST). It uses
    recursion to validate BST properties and calculates sums, returning
    the highest sum found among all valid BST subtrees.

    >>> t1 = TreeNode(4)
    >>> t1.left = TreeNode(3)
    >>> t1.left.left = TreeNode(1)
    >>> t1.left.right = TreeNode(2)
    >>> print(max_sum_bst(t1))
    2
    >>> t2 = TreeNode(-4)
    >>> t2.left = TreeNode(-2)
    >>> t2.right = TreeNode(-5)
    >>> print(max_sum_bst(t2))
    0
    >>> t3 = TreeNode(1)
    >>> t3.left = TreeNode(4)
    >>> t3.left.left = TreeNode(2)
    >>> t3.left.right = TreeNode(4)
    >>> t3.right = TreeNode(3)
    >>> t3.right.left = TreeNode(2)
    >>> t3.right.right = TreeNode(5)
    >>> t3.right.right.left = TreeNode(4)
    >>> t3.right.right.right = TreeNode(6)
    >>> print(max_sum_bst(t3))
    20
    """
    ans: int = 0

    def solver(node: TreeNode | None) -> tuple[bool, int, int, int]:
        """
        Returns the maximum sum by making recursive calls
        >>> t1 = TreeNode(1)
        >>> print(solver(t1))
        1
        """
        nonlocal ans

        if not node:
            return True, INT_MAX, INT_MIN, 0  # Valid BST, min, max, sum

        is_left_valid, min_left, max_left, sum_left = solver(node.left)
        is_right_valid, min_right, max_right, sum_right = solver(node.right)

        if is_left_valid and is_right_valid and max_left < node.val < min_right:
            total_sum = sum_left + sum_right + node.val
            ans = max(ans, total_sum)
            return True, min(min_left, node.val), max(max_right, node.val), total_sum

        return False, -1, -1, -1  # Not a valid BST

    solver(root)
    return ans


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/binary_tree/merge_two_binary_trees.py
================================================
#!/usr/local/bin/python3
"""
Problem Description: Given two binary tree, return the merged tree.
The rule for merging is that if two nodes overlap, then put the value sum of
both nodes to the new value of the merged node. Otherwise, the NOT null node
will be used as the node of new tree.
"""

from __future__ import annotations


class Node:
    """
    A binary node has value variable and pointers to its left and right node.
    """

    def __init__(self, value: int = 0) -> None:
        self.value = value
        self.left: Node | None = None
        self.right: Node | None = None


def merge_two_binary_trees(tree1: Node | None, tree2: Node | None) -> Node | None:
    """
    Returns root node of the merged tree.

    >>> tree1 = Node(5)
    >>> tree1.left = Node(6)
    >>> tree1.right = Node(7)
    >>> tree1.left.left = Node(2)
    >>> tree2 = Node(4)
    >>> tree2.left = Node(5)
    >>> tree2.right = Node(8)
    >>> tree2.left.right = Node(1)
    >>> tree2.right.right = Node(4)
    >>> merged_tree = merge_two_binary_trees(tree1, tree2)
    >>> print_preorder(merged_tree)
    9
    11
    2
    1
    15
    4
    """
    if tree1 is None:
        return tree2
    if tree2 is None:
        return tree1

    tree1.value = tree1.value + tree2.value
    tree1.left = merge_two_binary_trees(tree1.left, tree2.left)
    tree1.right = merge_two_binary_trees(tree1.right, tree2.right)
    return tree1


def print_preorder(root: Node | None) -> None:
    """
    Print pre-order traversal of the tree.

    >>> root = Node(1)
    >>> root.left = Node(2)
    >>> root.right = Node(3)
    >>> print_preorder(root)
    1
    2
    3
    >>> print_preorder(root.right)
    3
    """
    if root:
        print(root.value)
        print_preorder(root.left)
        print_preorder(root.right)


if __name__ == "__main__":
    tree1 = Node(1)
    tree1.left = Node(2)
    tree1.right = Node(3)
    tree1.left.left = Node(4)

    tree2 = Node(2)
    tree2.left = Node(4)
    tree2.right = Node(6)
    tree2.left.right = Node(9)
    tree2.right.right = Node(5)

    print("Tree1 is: ")
    print_preorder(tree1)
    print("Tree2 is: ")
    print_preorder(tree2)
    merged_tree = merge_two_binary_trees(tree1, tree2)
    print("Merged Tree is: ")
    print_preorder(merged_tree)


================================================
File: data_structures/binary_tree/mirror_binary_tree.py
================================================
"""
Given the root of a binary tree, mirror the tree, and return its root.

Leetcode problem reference: https://leetcode.com/problems/mirror-binary-tree/
"""

from __future__ import annotations

from collections.abc import Iterator
from dataclasses import dataclass


@dataclass
class Node:
    """
    A Node has value variable and pointers to Nodes to its left and right.
    """

    value: int
    left: Node | None = None
    right: Node | None = None

    def __iter__(self) -> Iterator[int]:
        if self.left:
            yield from self.left
        yield self.value
        if self.right:
            yield from self.right

    def __len__(self) -> int:
        return sum(1 for _ in self)

    def mirror(self) -> Node:
        """
        Mirror the binary tree rooted at this node by swapping left and right children.

        >>> tree = Node(0)
        >>> list(tree)
        [0]
        >>> list(tree.mirror())
        [0]
        >>> tree = Node(1, Node(0), Node(3, Node(2), Node(4, None, Node(5))))
        >>> tuple(tree)
        (0, 1, 2, 3, 4, 5)
        >>> tuple(tree.mirror())
        (5, 4, 3, 2, 1, 0)
        """
        self.left, self.right = self.right, self.left
        if self.left:
            self.left.mirror()
        if self.right:
            self.right.mirror()
        return self


def make_tree_seven() -> Node:
    r"""
    Return a binary tree with 7 nodes that looks like this:
    ::

           1
         /   \
        2     3
       / \   / \
      4   5 6   7

    >>> tree_seven = make_tree_seven()
    >>> len(tree_seven)
    7
    >>> list(tree_seven)
    [4, 2, 5, 1, 6, 3, 7]
    """
    tree = Node(1)
    tree.left = Node(2)
    tree.right = Node(3)
    tree.left.left = Node(4)
    tree.left.right = Node(5)
    tree.right.left = Node(6)
    tree.right.right = Node(7)
    return tree


def make_tree_nine() -> Node:
    r"""
    Return a binary tree with 9 nodes that looks like this:
    ::

            1
           / \
          2   3
         / \   \
        4   5   6
       / \   \
      7   8   9

    >>> tree_nine = make_tree_nine()
    >>> len(tree_nine)
    9
    >>> list(tree_nine)
    [7, 4, 8, 2, 5, 9, 1, 3, 6]
    """
    tree = Node(1)
    tree.left = Node(2)
    tree.right = Node(3)
    tree.left.left = Node(4)
    tree.left.right = Node(5)
    tree.right.right = Node(6)
    tree.left.left.left = Node(7)
    tree.left.left.right = Node(8)
    tree.left.right.right = Node(9)
    return tree


def main() -> None:
    r"""
    Mirror binary trees with the given root and returns the root

    >>> tree = make_tree_nine()
    >>> tuple(tree)
    (7, 4, 8, 2, 5, 9, 1, 3, 6)
    >>> tuple(tree.mirror())
    (6, 3, 1, 9, 5, 2, 8, 4, 7)

    nine_tree::

            1
           / \
          2   3
         / \   \
        4   5   6
       / \   \
      7   8   9

    The mirrored tree looks like this::

          1
         / \
        3   2
       /   / \
      6   5   4
         /   / \
        9   8   7
    """
    trees = {"zero": Node(0), "seven": make_tree_seven(), "nine": make_tree_nine()}
    for name, tree in trees.items():
        print(f"      The {name} tree: {tuple(tree)}")
        # (0,)
        # (4, 2, 5, 1, 6, 3, 7)
        # (7, 4, 8, 2, 5, 9, 1, 3, 6)
        print(f"Mirror of {name} tree: {tuple(tree.mirror())}")
        # (0,)
        # (7, 3, 6, 1, 5, 2, 4)
        # (6, 3, 1, 9, 5, 2, 8, 4, 7)


if __name__ == "__main__":
    import doctest

    doctest.testmod()
    main()


================================================
File: data_structures/binary_tree/non_recursive_segment_tree.py
================================================
"""
A non-recursive Segment Tree implementation with range query and single element update,
works virtually with any list of the same type of elements with a "commutative"
combiner.

Explanation:
https://www.geeksforgeeks.org/iterative-segment-tree-range-minimum-query/
https://www.geeksforgeeks.org/segment-tree-efficient-implementation/

>>> SegmentTree([1, 2, 3], lambda a, b: a + b).query(0, 2)
6
>>> SegmentTree([3, 1, 2], min).query(0, 2)
1
>>> SegmentTree([2, 3, 1], max).query(0, 2)
3
>>> st = SegmentTree([1, 5, 7, -1, 6], lambda a, b: a + b)
>>> st.update(1, -1)
>>> st.update(2, 3)
>>> st.query(1, 2)
2
>>> st.query(1, 1)
-1
>>> st.update(4, 1)
>>> st.query(3, 4)
0
>>> st = SegmentTree([[1, 2, 3], [3, 2, 1], [1, 1, 1]], lambda a, b: [a[i] + b[i] for i
...                                                                   in range(len(a))])
>>> st.query(0, 1)
[4, 4, 4]
>>> st.query(1, 2)
[4, 3, 2]
>>> st.update(1, [-1, -1, -1])
>>> st.query(1, 2)
[0, 0, 0]
>>> st.query(0, 2)
[1, 2, 3]
"""

from __future__ import annotations

from collections.abc import Callable
from typing import Any, Generic, TypeVar

T = TypeVar("T")


class SegmentTree(Generic[T]):
    def __init__(self, arr: list[T], fnc: Callable[[T, T], T]) -> None:
        """
        Segment Tree constructor, it works just with commutative combiner.
        :param arr: list of elements for the segment tree
        :param fnc: commutative function for combine two elements

        >>> SegmentTree(['a', 'b', 'c'], lambda a, b: f'{a}{b}').query(0, 2)
        'abc'
        >>> SegmentTree([(1, 2), (2, 3), (3, 4)],
        ...             lambda a, b: (a[0] + b[0], a[1] + b[1])).query(0, 2)
        (6, 9)
        """
        any_type: Any | T = None

        self.N: int = len(arr)
        self.st: list[T] = [any_type for _ in range(self.N)] + arr
        self.fn = fnc
        self.build()

    def build(self) -> None:
        for p in range(self.N - 1, 0, -1):
            self.st[p] = self.fn(self.st[p * 2], self.st[p * 2 + 1])

    def update(self, p: int, v: T) -> None:
        """
        Update an element in log(N) time
        :param p: position to be update
        :param v: new value

        >>> st = SegmentTree([3, 1, 2, 4], min)
        >>> st.query(0, 3)
        1
        >>> st.update(2, -1)
        >>> st.query(0, 3)
        -1
        """
        p += self.N
        self.st[p] = v
        while p > 1:
            p = p // 2
            self.st[p] = self.fn(self.st[p * 2], self.st[p * 2 + 1])

    def query(self, left: int, right: int) -> T | None:
        """
        Get range query value in log(N) time
        :param left: left element index
        :param right: right element index
        :return: element combined in the range [left, right]

        >>> st = SegmentTree([1, 2, 3, 4], lambda a, b: a + b)
        >>> st.query(0, 2)
        6
        >>> st.query(1, 2)
        5
        >>> st.query(0, 3)
        10
        >>> st.query(2, 3)
        7
        """
        left, right = left + self.N, right + self.N

        res: T | None = None
        while left <= right:
            if left % 2 == 1:
                res = self.st[left] if res is None else self.fn(res, self.st[left])
            if right % 2 == 0:
                res = self.st[right] if res is None else self.fn(res, self.st[right])
            left, right = (left + 1) // 2, (right - 1) // 2
        return res


if __name__ == "__main__":
    from functools import reduce

    test_array = [1, 10, -2, 9, -3, 8, 4, -7, 5, 6, 11, -12]

    test_updates = {
        0: 7,
        1: 2,
        2: 6,
        3: -14,
        4: 5,
        5: 4,
        6: 7,
        7: -10,
        8: 9,
        9: 10,
        10: 12,
        11: 1,
    }

    min_segment_tree = SegmentTree(test_array, min)
    max_segment_tree = SegmentTree(test_array, max)
    sum_segment_tree = SegmentTree(test_array, lambda a, b: a + b)

    def test_all_segments() -> None:
        """
        Test all possible segments
        """
        for i in range(len(test_array)):
            for j in range(i, len(test_array)):
                min_range = reduce(min, test_array[i : j + 1])
                max_range = reduce(max, test_array[i : j + 1])
                sum_range = reduce(lambda a, b: a + b, test_array[i : j + 1])
                assert min_range == min_segment_tree.query(i, j)
                assert max_range == max_segment_tree.query(i, j)
                assert sum_range == sum_segment_tree.query(i, j)

    test_all_segments()

    for index, value in test_updates.items():
        test_array[index] = value
        min_segment_tree.update(index, value)
        max_segment_tree.update(index, value)
        sum_segment_tree.update(index, value)
        test_all_segments()


================================================
File: data_structures/binary_tree/number_of_possible_binary_trees.py
================================================
"""
Hey, we are going to find an exciting number called Catalan number which is use to find
the number of possible binary search trees from tree of a given number of nodes.

We will use the formula: t(n) = SUMMATION(i = 1 to n)t(i-1)t(n-i)

Further details at Wikipedia: https://en.wikipedia.org/wiki/Catalan_number
"""

"""
Our Contribution:
Basically we Create the 2 function:
    1. catalan_number(node_count: int) -> int
        Returns the number of possible binary search trees for n nodes.
    2. binary_tree_count(node_count: int) -> int
        Returns the number of possible binary trees for n nodes.
"""


def binomial_coefficient(n: int, k: int) -> int:
    """
    Since Here we Find the Binomial Coefficient:
    https://en.wikipedia.org/wiki/Binomial_coefficient
    C(n,k) = n! / k!(n-k)!
    :param n: 2 times of Number of nodes
    :param k: Number of nodes
    :return:  Integer Value

    >>> binomial_coefficient(4, 2)
    6
    """
    result = 1  # To kept the Calculated Value
    # Since C(n, k) = C(n, n-k)
    k = min(k, n - k)
    # Calculate C(n,k)
    for i in range(k):
        result *= n - i
        result //= i + 1
    return result


def catalan_number(node_count: int) -> int:
    """
    We can find Catalan number many ways but here we use Binomial Coefficient because it
    does the job in O(n)

    return the Catalan number of n using 2nCn/(n+1).
    :param n: number of nodes
    :return: Catalan number of n nodes

    >>> catalan_number(5)
    42
    >>> catalan_number(6)
    132
    """
    return binomial_coefficient(2 * node_count, node_count) // (node_count + 1)


def factorial(n: int) -> int:
    """
    Return the factorial of a number.
    :param n: Number to find the Factorial of.
    :return: Factorial of n.

    >>> import math
    >>> all(factorial(i) == math.factorial(i) for i in range(10))
    True
    >>> factorial(-5)  # doctest: +ELLIPSIS
    Traceback (most recent call last):
        ...
    ValueError: factorial() not defined for negative values
    """
    if n < 0:
        raise ValueError("factorial() not defined for negative values")
    result = 1
    for i in range(1, n + 1):
        result *= i
    return result


def binary_tree_count(node_count: int) -> int:
    """
    Return the number of possible of binary trees.
    :param n: number of nodes
    :return: Number of possible binary trees

    >>> binary_tree_count(5)
    5040
    >>> binary_tree_count(6)
    95040
    """
    return catalan_number(node_count) * factorial(node_count)


if __name__ == "__main__":
    node_count = int(input("Enter the number of nodes: ").strip() or 0)
    if node_count <= 0:
        raise ValueError("We need some nodes to work with.")
    print(
        f"Given {node_count} nodes, there are {binary_tree_count(node_count)} "
        f"binary trees and {catalan_number(node_count)} binary search trees."
    )


================================================
File: data_structures/binary_tree/red_black_tree.py
================================================
from __future__ import annotations

from collections.abc import Iterator


class RedBlackTree:
    """
    A Red-Black tree, which is a self-balancing BST (binary search
    tree).
    This tree has similar performance to AVL trees, but the balancing is
    less strict, so it will perform faster for writing/deleting nodes
    and slower for reading in the average case, though, because they're
    both balanced binary search trees, both will get the same asymptotic
    performance.
    To read more about them, https://en.wikipedia.org/wiki/Red-black_tree
    Unless otherwise specified, all asymptotic runtimes are specified in
    terms of the size of the tree.
    """

    def __init__(
        self,
        label: int | None = None,
        color: int = 0,
        parent: RedBlackTree | None = None,
        left: RedBlackTree | None = None,
        right: RedBlackTree | None = None,
    ) -> None:
        """Initialize a new Red-Black Tree node with the given values:
        label: The value associated with this node
        color: 0 if black, 1 if red
        parent: The parent to this node
        left: This node's left child
        right: This node's right child
        """
        self.label = label
        self.parent = parent
        self.left = left
        self.right = right
        self.color = color

    # Here are functions which are specific to red-black trees

    def rotate_left(self) -> RedBlackTree:
        """Rotate the subtree rooted at this node to the left and
        returns the new root to this subtree.
        Performing one rotation can be done in O(1).
        """
        parent = self.parent
        right = self.right
        if right is None:
            return self
        self.right = right.left
        if self.right:
            self.right.parent = self
        self.parent = right
        right.left = self
        if parent is not None:
            if parent.left == self:
                parent.left = right
            else:
                parent.right = right
        right.parent = parent
        return right

    def rotate_right(self) -> RedBlackTree:
        """Rotate the subtree rooted at this node to the right and
        returns the new root to this subtree.
        Performing one rotation can be done in O(1).
        """
        if self.left is None:
            return self
        parent = self.parent
        left = self.left
        self.left = left.right
        if self.left:
            self.left.parent = self
        self.parent = left
        left.right = self
        if parent is not None:
            if parent.right is self:
                parent.right = left
            else:
                parent.left = left
        left.parent = parent
        return left

    def insert(self, label: int) -> RedBlackTree:
        """Inserts label into the subtree rooted at self, performs any
        rotations necessary to maintain balance, and then returns the
        new root to this subtree (likely self).
        This is guaranteed to run in O(log(n)) time.
        """
        if self.label is None:
            # Only possible with an empty tree
            self.label = label
            return self
        if self.label == label:
            return self
        elif self.label > label:
            if self.left:
                self.left.insert(label)
            else:
                self.left = RedBlackTree(label, 1, self)
                self.left._insert_repair()
        elif self.right:
            self.right.insert(label)
        else:
            self.right = RedBlackTree(label, 1, self)
            self.right._insert_repair()
        return self.parent or self

    def _insert_repair(self) -> None:
        """Repair the coloring from inserting into a tree."""
        if self.parent is None:
            # This node is the root, so it just needs to be black
            self.color = 0
        elif color(self.parent) == 0:
            # If the parent is black, then it just needs to be red
            self.color = 1
        else:
            uncle = self.parent.sibling
            if color(uncle) == 0:
                if self.is_left() and self.parent.is_right():
                    self.parent.rotate_right()
                    if self.right:
                        self.right._insert_repair()
                elif self.is_right() and self.parent.is_left():
                    self.parent.rotate_left()
                    if self.left:
                        self.left._insert_repair()
                elif self.is_left():
                    if self.grandparent:
                        self.grandparent.rotate_right()
                        self.parent.color = 0
                    if self.parent.right:
                        self.parent.right.color = 1
                else:
                    if self.grandparent:
                        self.grandparent.rotate_left()
                        self.parent.color = 0
                    if self.parent.left:
                        self.parent.left.color = 1
            else:
                self.parent.color = 0
                if uncle and self.grandparent:
                    uncle.color = 0
                    self.grandparent.color = 1
                    self.grandparent._insert_repair()

    def remove(self, label: int) -> RedBlackTree:
        """Remove label from this tree."""
        if self.label == label:
            if self.left and self.right:
                # It's easier to balance a node with at most one child,
                # so we replace this node with the greatest one less than
                # it and remove that.
                value = self.left.get_max()
                if value is not None:
                    self.label = value
                    self.left.remove(value)
            else:
                # This node has at most one non-None child, so we don't
                # need to replace
                child = self.left or self.right
                if self.color == 1:
                    # This node is red, and its child is black
                    # The only way this happens to a node with one child
                    # is if both children are None leaves.
                    # We can just remove this node and call it a day.
                    if self.parent:
                        if self.is_left():
                            self.parent.left = None
                        else:
                            self.parent.right = None
                # The node is black
                elif child is None:
                    # This node and its child are black
                    if self.parent is None:
                        # The tree is now empty
                        return RedBlackTree(None)
                    else:
                        self._remove_repair()
                        if self.is_left():
                            self.parent.left = None
                        else:
                            self.parent.right = None
                        self.parent = None
                else:
                    # This node is black and its child is red
                    # Move the child node here and make it black
                    self.label = child.label
                    self.left = child.left
                    self.right = child.right
                    if self.left:
                        self.left.parent = self
                    if self.right:
                        self.right.parent = self
        elif self.label is not None and self.label > label:
            if self.left:
                self.left.remove(label)
        elif self.right:
            self.right.remove(label)
        return self.parent or self

    def _remove_repair(self) -> None:
        """Repair the coloring of the tree that may have been messed up."""
        if (
            self.parent is None
            or self.sibling is None
            or self.parent.sibling is None
            or self.grandparent is None
        ):
            return
        if color(self.sibling) == 1:
            self.sibling.color = 0
            self.parent.color = 1
            if self.is_left():
                self.parent.rotate_left()
            else:
                self.parent.rotate_right()
        if (
            color(self.parent) == 0
            and color(self.sibling) == 0
            and color(self.sibling.left) == 0
            and color(self.sibling.right) == 0
        ):
            self.sibling.color = 1
            self.parent._remove_repair()
            return
        if (
            color(self.parent) == 1
            and color(self.sibling) == 0
            and color(self.sibling.left) == 0
            and color(self.sibling.right) == 0
        ):
            self.sibling.color = 1
            self.parent.color = 0
            return
        if (
            self.is_left()
            and color(self.sibling) == 0
            and color(self.sibling.right) == 0
            and color(self.sibling.left) == 1
        ):
            self.sibling.rotate_right()
            self.sibling.color = 0
            if self.sibling.right:
                self.sibling.right.color = 1
        if (
            self.is_right()
            and color(self.sibling) == 0
            and color(self.sibling.right) == 1
            and color(self.sibling.left) == 0
        ):
            self.sibling.rotate_left()
            self.sibling.color = 0
            if self.sibling.left:
                self.sibling.left.color = 1
        if (
            self.is_left()
            and color(self.sibling) == 0
            and color(self.sibling.right) == 1
        ):
            self.parent.rotate_left()
            self.grandparent.color = self.parent.color
            self.parent.color = 0
            self.parent.sibling.color = 0
        if (
            self.is_right()
            and color(self.sibling) == 0
            and color(self.sibling.left) == 1
        ):
            self.parent.rotate_right()
            self.grandparent.color = self.parent.color
            self.parent.color = 0
            self.parent.sibling.color = 0

    def check_color_properties(self) -> bool:
        """Check the coloring of the tree, and return True iff the tree
        is colored in a way which matches these five properties:
        (wording stolen from wikipedia article)
         1. Each node is either red or black.
         2. The root node is black.
         3. All leaves are black.
         4. If a node is red, then both its children are black.
         5. Every path from any node to all of its descendent NIL nodes
            has the same number of black nodes.
        This function runs in O(n) time, because properties 4 and 5 take
        that long to check.
        """
        # I assume property 1 to hold because there is nothing that can
        # make the color be anything other than 0 or 1.
        # Property 2
        if self.color:
            # The root was red
            print("Property 2")
            return False
        # Property 3 does not need to be checked, because None is assumed
        # to be black and is all the leaves.
        # Property 4
        if not self.check_coloring():
            print("Property 4")
            return False
        # Property 5
        if self.black_height() is None:
            print("Property 5")
            return False
        # All properties were met
        return True

    def check_coloring(self) -> bool:
        """A helper function to recursively check Property 4 of a
        Red-Black Tree. See check_color_properties for more info.
        """
        if self.color == 1 and 1 in (color(self.left), color(self.right)):
            return False
        if self.left and not self.left.check_coloring():
            return False
        return not (self.right and not self.right.check_coloring())

    def black_height(self) -> int | None:
        """Returns the number of black nodes from this node to the
        leaves of the tree, or None if there isn't one such value (the
        tree is color incorrectly).
        """
        if self is None or self.left is None or self.right is None:
            # If we're already at a leaf, there is no path
            return 1
        left = RedBlackTree.black_height(self.left)
        right = RedBlackTree.black_height(self.right)
        if left is None or right is None:
            # There are issues with coloring below children nodes
            return None
        if left != right:
            # The two children have unequal depths
            return None
        # Return the black depth of children, plus one if this node is
        # black
        return left + (1 - self.color)

    # Here are functions which are general to all binary search trees

    def __contains__(self, label: int) -> bool:
        """Search through the tree for label, returning True iff it is
        found somewhere in the tree.
        Guaranteed to run in O(log(n)) time.
        """
        return self.search(label) is not None

    def search(self, label: int) -> RedBlackTree | None:
        """Search through the tree for label, returning its node if
        it's found, and None otherwise.
        This method is guaranteed to run in O(log(n)) time.
        """
        if self.label == label:
            return self
        elif self.label is not None and label > self.label:
            if self.right is None:
                return None
            else:
                return self.right.search(label)
        elif self.left is None:
            return None
        else:
            return self.left.search(label)

    def floor(self, label: int) -> int | None:
        """Returns the largest element in this tree which is at most label.
        This method is guaranteed to run in O(log(n)) time."""
        if self.label == label:
            return self.label
        elif self.label is not None and self.label > label:
            if self.left:
                return self.left.floor(label)
            else:
                return None
        else:
            if self.right:
                attempt = self.right.floor(label)
                if attempt is not None:
                    return attempt
            return self.label

    def ceil(self, label: int) -> int | None:
        """Returns the smallest element in this tree which is at least label.
        This method is guaranteed to run in O(log(n)) time.
        """
        if self.label == label:
            return self.label
        elif self.label is not None and self.label < label:
            if self.right:
                return self.right.ceil(label)
            else:
                return None
        else:
            if self.left:
                attempt = self.left.ceil(label)
                if attempt is not None:
                    return attempt
            return self.label

    def get_max(self) -> int | None:
        """Returns the largest element in this tree.
        This method is guaranteed to run in O(log(n)) time.
        """
        if self.right:
            # Go as far right as possible
            return self.right.get_max()
        else:
            return self.label

    def get_min(self) -> int | None:
        """Returns the smallest element in this tree.
        This method is guaranteed to run in O(log(n)) time.
        """
        if self.left:
            # Go as far left as possible
            return self.left.get_min()
        else:
            return self.label

    @property
    def grandparent(self) -> RedBlackTree | None:
        """Get the current node's grandparent, or None if it doesn't exist."""
        if self.parent is None:
            return None
        else:
            return self.parent.parent

    @property
    def sibling(self) -> RedBlackTree | None:
        """Get the current node's sibling, or None if it doesn't exist."""
        if self.parent is None:
            return None
        elif self.parent.left is self:
            return self.parent.right
        else:
            return self.parent.left

    def is_left(self) -> bool:
        """Returns true iff this node is the left child of its parent."""
        if self.parent is None:
            return False
        return self.parent.left is self

    def is_right(self) -> bool:
        """Returns true iff this node is the right child of its parent."""
        if self.parent is None:
            return False
        return self.parent.right is self

    def __bool__(self) -> bool:
        return True

    def __len__(self) -> int:
        """
        Return the number of nodes in this tree.
        """
        ln = 1
        if self.left:
            ln += len(self.left)
        if self.right:
            ln += len(self.right)
        return ln

    def preorder_traverse(self) -> Iterator[int | None]:
        yield self.label
        if self.left:
            yield from self.left.preorder_traverse()
        if self.right:
            yield from self.right.preorder_traverse()

    def inorder_traverse(self) -> Iterator[int | None]:
        if self.left:
            yield from self.left.inorder_traverse()
        yield self.label
        if self.right:
            yield from self.right.inorder_traverse()

    def postorder_traverse(self) -> Iterator[int | None]:
        if self.left:
            yield from self.left.postorder_traverse()
        if self.right:
            yield from self.right.postorder_traverse()
        yield self.label

    def __repr__(self) -> str:
        from pprint import pformat

        if self.left is None and self.right is None:
            return f"'{self.label} {(self.color and 'red') or 'blk'}'"
        return pformat(
            {
                f"{self.label} {(self.color and 'red') or 'blk'}": (
                    self.left,
                    self.right,
                )
            },
            indent=1,
        )

    def __eq__(self, other: object) -> bool:
        """Test if two trees are equal."""
        if not isinstance(other, RedBlackTree):
            return NotImplemented
        if self.label == other.label:
            return self.left == other.left and self.right == other.right
        else:
            return False


def color(node: RedBlackTree | None) -> int:
    """Returns the color of a node, allowing for None leaves."""
    if node is None:
        return 0
    else:
        return node.color


"""
Code for testing the various
functions of the red-black tree.
"""


def test_rotations() -> bool:
    """Test that the rotate_left and rotate_right functions work."""
    # Make a tree to test on
    tree = RedBlackTree(0)
    tree.left = RedBlackTree(-10, parent=tree)
    tree.right = RedBlackTree(10, parent=tree)
    tree.left.left = RedBlackTree(-20, parent=tree.left)
    tree.left.right = RedBlackTree(-5, parent=tree.left)
    tree.right.left = RedBlackTree(5, parent=tree.right)
    tree.right.right = RedBlackTree(20, parent=tree.right)
    # Make the right rotation
    left_rot = RedBlackTree(10)
    left_rot.left = RedBlackTree(0, parent=left_rot)
    left_rot.left.left = RedBlackTree(-10, parent=left_rot.left)
    left_rot.left.right = RedBlackTree(5, parent=left_rot.left)
    left_rot.left.left.left = RedBlackTree(-20, parent=left_rot.left.left)
    left_rot.left.left.right = RedBlackTree(-5, parent=left_rot.left.left)
    left_rot.right = RedBlackTree(20, parent=left_rot)
    tree = tree.rotate_left()
    if tree != left_rot:
        return False
    tree = tree.rotate_right()
    tree = tree.rotate_right()
    # Make the left rotation
    right_rot = RedBlackTree(-10)
    right_rot.left = RedBlackTree(-20, parent=right_rot)
    right_rot.right = RedBlackTree(0, parent=right_rot)
    right_rot.right.left = RedBlackTree(-5, parent=right_rot.right)
    right_rot.right.right = RedBlackTree(10, parent=right_rot.right)
    right_rot.right.right.left = RedBlackTree(5, parent=right_rot.right.right)
    right_rot.right.right.right = RedBlackTree(20, parent=right_rot.right.right)
    return tree == right_rot


def test_insertion_speed() -> bool:
    """Test that the tree balances inserts to O(log(n)) by doing a lot
    of them.
    """
    tree = RedBlackTree(-1)
    for i in range(300000):
        tree = tree.insert(i)
    return True


def test_insert() -> bool:
    """Test the insert() method of the tree correctly balances, colors,
    and inserts.
    """
    tree = RedBlackTree(0)
    tree.insert(8)
    tree.insert(-8)
    tree.insert(4)
    tree.insert(12)
    tree.insert(10)
    tree.insert(11)
    ans = RedBlackTree(0, 0)
    ans.left = RedBlackTree(-8, 0, ans)
    ans.right = RedBlackTree(8, 1, ans)
    ans.right.left = RedBlackTree(4, 0, ans.right)
    ans.right.right = RedBlackTree(11, 0, ans.right)
    ans.right.right.left = RedBlackTree(10, 1, ans.right.right)
    ans.right.right.right = RedBlackTree(12, 1, ans.right.right)
    return tree == ans


def test_insert_and_search() -> bool:
    """Tests searching through the tree for values."""
    tree = RedBlackTree(0)
    tree.insert(8)
    tree.insert(-8)
    tree.insert(4)
    tree.insert(12)
    tree.insert(10)
    tree.insert(11)
    if any(i in tree for i in (5, -6, -10, 13)):
        # Found something not in there
        return False
    # Find all these things in there
    return all(i in tree for i in (11, 12, -8, 0))


def test_insert_delete() -> bool:
    """Test the insert() and delete() method of the tree, verifying the
    insertion and removal of elements, and the balancing of the tree.
    """
    tree = RedBlackTree(0)
    tree = tree.insert(-12)
    tree = tree.insert(8)
    tree = tree.insert(-8)
    tree = tree.insert(15)
    tree = tree.insert(4)
    tree = tree.insert(12)
    tree = tree.insert(10)
    tree = tree.insert(9)
    tree = tree.insert(11)
    tree = tree.remove(15)
    tree = tree.remove(-12)
    tree = tree.remove(9)
    if not tree.check_color_properties():
        return False
    return list(tree.inorder_traverse()) == [-8, 0, 4, 8, 10, 11, 12]


def test_floor_ceil() -> bool:
    """Tests the floor and ceiling functions in the tree."""
    tree = RedBlackTree(0)
    tree.insert(-16)
    tree.insert(16)
    tree.insert(8)
    tree.insert(24)
    tree.insert(20)
    tree.insert(22)
    tuples = [(-20, None, -16), (-10, -16, 0), (8, 8, 8), (50, 24, None)]
    for val, floor, ceil in tuples:
        if tree.floor(val) != floor or tree.ceil(val) != ceil:
            return False
    return True


def test_min_max() -> bool:
    """Tests the min and max functions in the tree."""
    tree = RedBlackTree(0)
    tree.insert(-16)
    tree.insert(16)
    tree.insert(8)
    tree.insert(24)
    tree.insert(20)
    tree.insert(22)
    return not (tree.get_max() != 22 or tree.get_min() != -16)


def test_tree_traversal() -> bool:
    """Tests the three different tree traversal functions."""
    tree = RedBlackTree(0)
    tree = tree.insert(-16)
    tree.insert(16)
    tree.insert(8)
    tree.insert(24)
    tree.insert(20)
    tree.insert(22)
    if list(tree.inorder_traverse()) != [-16, 0, 8, 16, 20, 22, 24]:
        return False
    if list(tree.preorder_traverse()) != [0, -16, 16, 8, 22, 20, 24]:
        return False
    return list(tree.postorder_traverse()) == [-16, 8, 20, 24, 22, 16, 0]


def test_tree_chaining() -> bool:
    """Tests the three different tree chaining functions."""
    tree = RedBlackTree(0)
    tree = tree.insert(-16).insert(16).insert(8).insert(24).insert(20).insert(22)
    if list(tree.inorder_traverse()) != [-16, 0, 8, 16, 20, 22, 24]:
        return False
    if list(tree.preorder_traverse()) != [0, -16, 16, 8, 22, 20, 24]:
        return False
    return list(tree.postorder_traverse()) == [-16, 8, 20, 24, 22, 16, 0]


def print_results(msg: str, passes: bool) -> None:
    print(str(msg), "works!" if passes else "doesn't work :(")


def pytests() -> None:
    assert test_rotations()
    assert test_insert()
    assert test_insert_and_search()
    assert test_insert_delete()
    assert test_floor_ceil()
    assert test_tree_traversal()
    assert test_tree_chaining()


def main() -> None:
    """
    >>> pytests()
    """
    print_results("Rotating right and left", test_rotations())
    print_results("Inserting", test_insert())
    print_results("Searching", test_insert_and_search())
    print_results("Deleting", test_insert_delete())
    print_results("Floor and ceil", test_floor_ceil())
    print_results("Tree traversal", test_tree_traversal())
    print_results("Tree traversal", test_tree_chaining())
    print("Testing tree balancing...")
    print("This should only be a few seconds.")
    test_insertion_speed()
    print("Done!")


if __name__ == "__main__":
    main()


================================================
File: data_structures/binary_tree/segment_tree.py
================================================
import math


class SegmentTree:
    def __init__(self, a):
        self.A = a
        self.N = len(self.A)
        self.st = [0] * (
            4 * self.N
        )  # approximate the overall size of segment tree with array N
        if self.N:
            self.build(1, 0, self.N - 1)

    def left(self, idx):
        """
        Returns the left child index for a given index in a binary tree.

        >>> s = SegmentTree([1, 2, 3])
        >>> s.left(1)
        2
        >>> s.left(2)
        4
        """
        return idx * 2

    def right(self, idx):
        """
        Returns the right child index for a given index in a binary tree.

        >>> s = SegmentTree([1, 2, 3])
        >>> s.right(1)
        3
        >>> s.right(2)
        5
        """
        return idx * 2 + 1

    def build(self, idx, left, right):
        if left == right:
            self.st[idx] = self.A[left]
        else:
            mid = (left + right) // 2
            self.build(self.left(idx), left, mid)
            self.build(self.right(idx), mid + 1, right)
            self.st[idx] = max(self.st[self.left(idx)], self.st[self.right(idx)])

    def update(self, a, b, val):
        """
        Update the values in the segment tree in the range [a,b] with the given value.

        >>> s = SegmentTree([1, 2, 3, 4, 5])
        >>> s.update(2, 4, 10)
        True
        >>> s.query(1, 5)
        10
        """
        return self.update_recursive(1, 0, self.N - 1, a - 1, b - 1, val)

    def update_recursive(self, idx, left, right, a, b, val):
        """
        update(1, 1, N, a, b, v) for update val v to [a,b]
        """
        if right < a or left > b:
            return True
        if left == right:
            self.st[idx] = val
            return True
        mid = (left + right) // 2
        self.update_recursive(self.left(idx), left, mid, a, b, val)
        self.update_recursive(self.right(idx), mid + 1, right, a, b, val)
        self.st[idx] = max(self.st[self.left(idx)], self.st[self.right(idx)])
        return True

    def query(self, a, b):
        """
        Query the maximum value in the range [a,b].

        >>> s = SegmentTree([1, 2, 3, 4, 5])
        >>> s.query(1, 3)
        3
        >>> s.query(1, 5)
        5
        """
        return self.query_recursive(1, 0, self.N - 1, a - 1, b - 1)

    def query_recursive(self, idx, left, right, a, b):
        """
        query(1, 1, N, a, b) for query max of [a,b]
        """
        if right < a or left > b:
            return -math.inf
        if left >= a and right <= b:
            return self.st[idx]
        mid = (left + right) // 2
        q1 = self.query_recursive(self.left(idx), left, mid, a, b)
        q2 = self.query_recursive(self.right(idx), mid + 1, right, a, b)
        return max(q1, q2)

    def show_data(self):
        show_list = []
        for i in range(1, self.N + 1):
            show_list += [self.query(i, i)]
        print(show_list)


if __name__ == "__main__":
    A = [1, 2, -4, 7, 3, -5, 6, 11, -20, 9, 14, 15, 5, 2, -8]
    N = 15
    segt = SegmentTree(A)
    print(segt.query(4, 6))
    print(segt.query(7, 11))
    print(segt.query(7, 12))
    segt.update(1, 3, 111)
    print(segt.query(1, 15))
    segt.update(7, 8, 235)
    segt.show_data()


================================================
File: data_structures/binary_tree/segment_tree_other.py
================================================
"""
Segment_tree creates a segment tree with a given array and function,
allowing queries to be done later in log(N) time
function takes 2 values and returns a same type value
"""

from collections.abc import Sequence
from queue import Queue


class SegmentTreeNode:
    def __init__(self, start, end, val, left=None, right=None):
        self.start = start
        self.end = end
        self.val = val
        self.mid = (start + end) // 2
        self.left = left
        self.right = right

    def __repr__(self):
        return f"SegmentTreeNode(start={self.start}, end={self.end}, val={self.val})"


class SegmentTree:
    """
    >>> import operator
    >>> num_arr = SegmentTree([2, 1, 5, 3, 4], operator.add)
    >>> tuple(num_arr.traverse())  # doctest: +NORMALIZE_WHITESPACE
    (SegmentTreeNode(start=0, end=4, val=15),
        SegmentTreeNode(start=0, end=2, val=8),
        SegmentTreeNode(start=3, end=4, val=7),
        SegmentTreeNode(start=0, end=1, val=3),
        SegmentTreeNode(start=2, end=2, val=5),
        SegmentTreeNode(start=3, end=3, val=3),
        SegmentTreeNode(start=4, end=4, val=4),
        SegmentTreeNode(start=0, end=0, val=2),
        SegmentTreeNode(start=1, end=1, val=1))
    >>>
    >>> num_arr.update(1, 5)
    >>> tuple(num_arr.traverse())  # doctest: +NORMALIZE_WHITESPACE
    (SegmentTreeNode(start=0, end=4, val=19),
        SegmentTreeNode(start=0, end=2, val=12),
        SegmentTreeNode(start=3, end=4, val=7),
        SegmentTreeNode(start=0, end=1, val=7),
        SegmentTreeNode(start=2, end=2, val=5),
        SegmentTreeNode(start=3, end=3, val=3),
        SegmentTreeNode(start=4, end=4, val=4),
        SegmentTreeNode(start=0, end=0, val=2),
        SegmentTreeNode(start=1, end=1, val=5))
    >>>
    >>> num_arr.query_range(3, 4)
    7
    >>> num_arr.query_range(2, 2)
    5
    >>> num_arr.query_range(1, 3)
    13
    >>>
    >>> max_arr = SegmentTree([2, 1, 5, 3, 4], max)
    >>> for node in max_arr.traverse():
    ...     print(node)
    ...
    SegmentTreeNode(start=0, end=4, val=5)
    SegmentTreeNode(start=0, end=2, val=5)
    SegmentTreeNode(start=3, end=4, val=4)
    SegmentTreeNode(start=0, end=1, val=2)
    SegmentTreeNode(start=2, end=2, val=5)
    SegmentTreeNode(start=3, end=3, val=3)
    SegmentTreeNode(start=4, end=4, val=4)
    SegmentTreeNode(start=0, end=0, val=2)
    SegmentTreeNode(start=1, end=1, val=1)
    >>>
    >>> max_arr.update(1, 5)
    >>> for node in max_arr.traverse():
    ...     print(node)
    ...
    SegmentTreeNode(start=0, end=4, val=5)
    SegmentTreeNode(start=0, end=2, val=5)
    SegmentTreeNode(start=3, end=4, val=4)
    SegmentTreeNode(start=0, end=1, val=5)
    SegmentTreeNode(start=2, end=2, val=5)
    SegmentTreeNode(start=3, end=3, val=3)
    SegmentTreeNode(start=4, end=4, val=4)
    SegmentTreeNode(start=0, end=0, val=2)
    SegmentTreeNode(start=1, end=1, val=5)
    >>>
    >>> max_arr.query_range(3, 4)
    4
    >>> max_arr.query_range(2, 2)
    5
    >>> max_arr.query_range(1, 3)
    5
    >>>
    >>> min_arr = SegmentTree([2, 1, 5, 3, 4], min)
    >>> for node in min_arr.traverse():
    ...     print(node)
    ...
    SegmentTreeNode(start=0, end=4, val=1)
    SegmentTreeNode(start=0, end=2, val=1)
    SegmentTreeNode(start=3, end=4, val=3)
    SegmentTreeNode(start=0, end=1, val=1)
    SegmentTreeNode(start=2, end=2, val=5)
    SegmentTreeNode(start=3, end=3, val=3)
    SegmentTreeNode(start=4, end=4, val=4)
    SegmentTreeNode(start=0, end=0, val=2)
    SegmentTreeNode(start=1, end=1, val=1)
    >>>
    >>> min_arr.update(1, 5)
    >>> for node in min_arr.traverse():
    ...     print(node)
    ...
    SegmentTreeNode(start=0, end=4, val=2)
    SegmentTreeNode(start=0, end=2, val=2)
    SegmentTreeNode(start=3, end=4, val=3)
    SegmentTreeNode(start=0, end=1, val=2)
    SegmentTreeNode(start=2, end=2, val=5)
    SegmentTreeNode(start=3, end=3, val=3)
    SegmentTreeNode(start=4, end=4, val=4)
    SegmentTreeNode(start=0, end=0, val=2)
    SegmentTreeNode(start=1, end=1, val=5)
    >>>
    >>> min_arr.query_range(3, 4)
    3
    >>> min_arr.query_range(2, 2)
    5
    >>> min_arr.query_range(1, 3)
    3
    >>>
    """

    def __init__(self, collection: Sequence, function):
        self.collection = collection
        self.fn = function
        if self.collection:
            self.root = self._build_tree(0, len(collection) - 1)

    def update(self, i, val):
        """
        Update an element in log(N) time
        :param i: position to be update
        :param val: new value
        >>> import operator
        >>> num_arr = SegmentTree([2, 1, 5, 3, 4], operator.add)
        >>> num_arr.update(1, 5)
        >>> num_arr.query_range(1, 3)
        13
        """
        self._update_tree(self.root, i, val)

    def query_range(self, i, j):
        """
        Get range query value in log(N) time
        :param i: left element index
        :param j: right element index
        :return: element combined in the range [i, j]
        >>> import operator
        >>> num_arr = SegmentTree([2, 1, 5, 3, 4], operator.add)
        >>> num_arr.update(1, 5)
        >>> num_arr.query_range(3, 4)
        7
        >>> num_arr.query_range(2, 2)
        5
        >>> num_arr.query_range(1, 3)
        13
        >>>
        """
        return self._query_range(self.root, i, j)

    def _build_tree(self, start, end):
        if start == end:
            return SegmentTreeNode(start, end, self.collection[start])
        mid = (start + end) // 2
        left = self._build_tree(start, mid)
        right = self._build_tree(mid + 1, end)
        return SegmentTreeNode(start, end, self.fn(left.val, right.val), left, right)

    def _update_tree(self, node, i, val):
        if node.start == i and node.end == i:
            node.val = val
            return
        if i <= node.mid:
            self._update_tree(node.left, i, val)
        else:
            self._update_tree(node.right, i, val)
        node.val = self.fn(node.left.val, node.right.val)

    def _query_range(self, node, i, j):
        if node.start == i and node.end == j:
            return node.val

        if i <= node.mid:
            if j <= node.mid:
                # range in left child tree
                return self._query_range(node.left, i, j)
            else:
                # range in left child tree and right child tree
                return self.fn(
                    self._query_range(node.left, i, node.mid),
                    self._query_range(node.right, node.mid + 1, j),
                )
        else:
            # range in right child tree
            return self._query_range(node.right, i, j)

    def traverse(self):
        if self.root is not None:
            queue = Queue()
            queue.put(self.root)
            while not queue.empty():
                node = queue.get()
                yield node

                if node.left is not None:
                    queue.put(node.left)

                if node.right is not None:
                    queue.put(node.right)


if __name__ == "__main__":
    import operator

    for fn in [operator.add, max, min]:
        print("*" * 50)
        arr = SegmentTree([2, 1, 5, 3, 4], fn)
        for node in arr.traverse():
            print(node)
        print()

        arr.update(1, 5)
        for node in arr.traverse():
            print(node)
        print()

        print(arr.query_range(3, 4))  # 7
        print(arr.query_range(2, 2))  # 5
        print(arr.query_range(1, 3))  # 13
        print()


================================================
File: data_structures/binary_tree/serialize_deserialize_binary_tree.py
================================================
from __future__ import annotations

from collections.abc import Iterator
from dataclasses import dataclass


@dataclass
class TreeNode:
    """
    A binary tree node has a value, left child, and right child.

    Props:
        value: The value of the node.
        left: The left child of the node.
        right: The right child of the node.
    """

    value: int = 0
    left: TreeNode | None = None
    right: TreeNode | None = None

    def __post_init__(self):
        if not isinstance(self.value, int):
            raise TypeError("Value must be an integer.")

    def __iter__(self) -> Iterator[TreeNode]:
        """
        Iterate through the tree in preorder.

        Returns:
            An iterator of the tree nodes.

        >>> list(TreeNode(1))
        [1,null,null]
        >>> tuple(TreeNode(1, TreeNode(2), TreeNode(3)))
        (1,2,null,null,3,null,null, 2,null,null, 3,null,null)
        """
        yield self
        yield from self.left or ()
        yield from self.right or ()

    def __len__(self) -> int:
        """
        Count the number of nodes in the tree.

        Returns:
            The number of nodes in the tree.

        >>> len(TreeNode(1))
        1
        >>> len(TreeNode(1, TreeNode(2), TreeNode(3)))
        3
        """
        return sum(1 for _ in self)

    def __repr__(self) -> str:
        """
        Represent the tree as a string.

        Returns:
            A string representation of the tree.

        >>> repr(TreeNode(1))
        '1,null,null'
        >>> repr(TreeNode(1, TreeNode(2), TreeNode(3)))
        '1,2,null,null,3,null,null'
        >>> repr(TreeNode(1, TreeNode(2), TreeNode(3, TreeNode(4), TreeNode(5))))
        '1,2,null,null,3,4,null,null,5,null,null'
        """
        return f"{self.value},{self.left!r},{self.right!r}".replace("None", "null")

    @classmethod
    def five_tree(cls) -> TreeNode:
        """
        >>> repr(TreeNode.five_tree())
        '1,2,null,null,3,4,null,null,5,null,null'
        """
        root = TreeNode(1)
        root.left = TreeNode(2)
        root.right = TreeNode(3)
        root.right.left = TreeNode(4)
        root.right.right = TreeNode(5)
        return root


def deserialize(data: str) -> TreeNode | None:
    """
    Deserialize a string to a binary tree.

    Args:
        data(str): The serialized string.

    Returns:
        The root of the binary tree.

    >>> root = TreeNode.five_tree()
    >>> serialzed_data = repr(root)
    >>> deserialized = deserialize(serialzed_data)
    >>> root == deserialized
    True
    >>> root is deserialized  # two separate trees
    False
    >>> root.right.right.value = 6
    >>> root == deserialized
    False
    >>> serialzed_data = repr(root)
    >>> deserialized = deserialize(serialzed_data)
    >>> root == deserialized
    True
    >>> deserialize("")
    Traceback (most recent call last):
        ...
    ValueError: Data cannot be empty.
    """

    if not data:
        raise ValueError("Data cannot be empty.")

    # Split the serialized string by a comma to get node values
    nodes = data.split(",")

    def build_tree() -> TreeNode | None:
        # Get the next value from the list
        value = nodes.pop(0)

        if value == "null":
            return None

        node = TreeNode(int(value))
        node.left = build_tree()  # Recursively build left subtree
        node.right = build_tree()  # Recursively build right subtree
        return node

    return build_tree()


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/binary_tree/symmetric_tree.py
================================================
"""
Given the root of a binary tree, check whether it is a mirror of itself
(i.e., symmetric around its center).

Leetcode reference: https://leetcode.com/problems/symmetric-tree/
"""

from __future__ import annotations

from dataclasses import dataclass


@dataclass
class Node:
    """
    A Node represents an element of a binary tree, which contains:

    Attributes:
    data: The value stored in the node (int).
    left: Pointer to the left child node (Node or None).
    right: Pointer to the right child node (Node or None).

    Example:
    >>> node = Node(1, Node(2), Node(3))
    >>> node.data
    1
    >>> node.left.data
    2
    >>> node.right.data
    3
    """

    data: int
    left: Node | None = None
    right: Node | None = None


def make_symmetric_tree() -> Node:
    r"""
    Create a symmetric tree for testing.

    The tree looks like this:
           1
         /   \
        2     2
      / \    / \
     3   4   4  3

    Returns:
    Node: Root node of a symmetric tree.

    Example:
    >>> tree = make_symmetric_tree()
    >>> tree.data
    1
    >>> tree.left.data == tree.right.data
    True
    >>> tree.left.left.data == tree.right.right.data
    True
    """
    root = Node(1)
    root.left = Node(2)
    root.right = Node(2)
    root.left.left = Node(3)
    root.left.right = Node(4)
    root.right.left = Node(4)
    root.right.right = Node(3)
    return root


def make_asymmetric_tree() -> Node:
    r"""
    Create an asymmetric tree for testing.

    The tree looks like this:
           1
         /   \
        2     2
      / \    / \
     3   4   3  4

    Returns:
    Node: Root node of an asymmetric tree.

    Example:
    >>> tree = make_asymmetric_tree()
    >>> tree.data
    1
    >>> tree.left.data == tree.right.data
    True
    >>> tree.left.left.data == tree.right.right.data
    False
    """
    root = Node(1)
    root.left = Node(2)
    root.right = Node(2)
    root.left.left = Node(3)
    root.left.right = Node(4)
    root.right.left = Node(3)
    root.right.right = Node(4)
    return root


def is_symmetric_tree(tree: Node) -> bool:
    """
    Check if a binary tree is symmetric (i.e., a mirror of itself).

    Parameters:
    tree: The root node of the binary tree.

    Returns:
    bool: True if the tree is symmetric, False otherwise.

    Example:
    >>> is_symmetric_tree(make_symmetric_tree())
    True
    >>> is_symmetric_tree(make_asymmetric_tree())
    False
    """
    if tree:
        return is_mirror(tree.left, tree.right)
    return True  # An empty tree is considered symmetric.


def is_mirror(left: Node | None, right: Node | None) -> bool:
    """
    Check if two subtrees are mirror images of each other.

    Parameters:
    left: The root node of the left subtree.
    right: The root node of the right subtree.

    Returns:
    bool: True if the two subtrees are mirrors of each other, False otherwise.

    Example:
    >>> tree1 = make_symmetric_tree()
    >>> is_mirror(tree1.left, tree1.right)
    True
    >>> tree2 = make_asymmetric_tree()
    >>> is_mirror(tree2.left, tree2.right)
    False
    """
    if left is None and right is None:
        # Both sides are empty, which is symmetric.
        return True
    if left is None or right is None:
        # One side is empty while the other is not, which is not symmetric.
        return False
    if left.data == right.data:
        # The values match, so check the subtrees recursively.
        return is_mirror(left.left, right.right) and is_mirror(left.right, right.left)
    return False


if __name__ == "__main__":
    from doctest import testmod

    testmod()


================================================
File: data_structures/binary_tree/treap.py
================================================
from __future__ import annotations

from random import random


class Node:
    """
    Treap's node
    Treap is a binary tree by value and heap by priority
    """

    def __init__(self, value: int | None = None):
        self.value = value
        self.prior = random()
        self.left: Node | None = None
        self.right: Node | None = None

    def __repr__(self) -> str:
        from pprint import pformat

        if self.left is None and self.right is None:
            return f"'{self.value}: {self.prior:.5}'"
        else:
            return pformat(
                {f"{self.value}: {self.prior:.5}": (self.left, self.right)}, indent=1
            )

    def __str__(self) -> str:
        value = str(self.value) + " "
        left = str(self.left or "")
        right = str(self.right or "")
        return value + left + right


def split(root: Node | None, value: int) -> tuple[Node | None, Node | None]:
    """
    We split current tree into 2 trees with value:

    Left tree contains all values less than split value.
    Right tree contains all values greater or equal, than split value
    """
    if root is None or root.value is None:  # None tree is split into 2 Nones
        return None, None
    elif value < root.value:
        """
        Right tree's root will be current node.
        Now we split(with the same value) current node's left son
        Left tree: left part of that split
        Right tree's left son: right part of that split
        """
        left, root.left = split(root.left, value)
        return left, root
    else:
        """
        Just symmetric to previous case
        """
        root.right, right = split(root.right, value)
        return root, right


def merge(left: Node | None, right: Node | None) -> Node | None:
    """
    We merge 2 trees into one.
    Note: all left tree's values must be less than all right tree's
    """
    if (not left) or (not right):  # If one node is None, return the other
        return left or right
    elif left.prior < right.prior:
        """
        Left will be root because it has more priority
        Now we need to merge left's right son and right tree
        """
        left.right = merge(left.right, right)
        return left
    else:
        """
        Symmetric as well
        """
        right.left = merge(left, right.left)
        return right


def insert(root: Node | None, value: int) -> Node | None:
    """
    Insert element

    Split current tree with a value into left, right,
    Insert new node into the middle
    Merge left, node, right into root
    """
    node = Node(value)
    left, right = split(root, value)
    return merge(merge(left, node), right)


def erase(root: Node | None, value: int) -> Node | None:
    """
    Erase element

    Split all nodes with values less into left,
    Split all nodes with values greater into right.
    Merge left, right
    """
    left, right = split(root, value - 1)
    _, right = split(right, value)
    return merge(left, right)


def inorder(root: Node | None) -> None:
    """
    Just recursive print of a tree
    """
    if not root:  # None
        return
    else:
        inorder(root.left)
        print(root.value, end=",")
        inorder(root.right)


def interact_treap(root: Node | None, args: str) -> Node | None:
    """
    Commands:
    + value to add value into treap
    - value to erase all nodes with value

        >>> root = interact_treap(None, "+1")
        >>> inorder(root)
        1,
        >>> root = interact_treap(root, "+3 +5 +17 +19 +2 +16 +4 +0")
        >>> inorder(root)
        0,1,2,3,4,5,16,17,19,
        >>> root = interact_treap(root, "+4 +4 +4")
        >>> inorder(root)
        0,1,2,3,4,4,4,4,5,16,17,19,
        >>> root = interact_treap(root, "-0")
        >>> inorder(root)
        1,2,3,4,4,4,4,5,16,17,19,
        >>> root = interact_treap(root, "-4")
        >>> inorder(root)
        1,2,3,5,16,17,19,
        >>> root = interact_treap(root, "=0")
        Unknown command
    """
    for arg in args.split():
        if arg[0] == "+":
            root = insert(root, int(arg[1:]))

        elif arg[0] == "-":
            root = erase(root, int(arg[1:]))

        else:
            print("Unknown command")

    return root


def main() -> None:
    """After each command, program prints treap"""
    root = None
    print(
        "enter numbers to create a tree, + value to add value into treap, "
        "- value to erase all nodes with value. 'q' to quit. "
    )

    args = input()
    while args != "q":
        root = interact_treap(root, args)
        print(root)
        args = input()

    print("good by!")


if __name__ == "__main__":
    import doctest

    doctest.testmod()
    main()


================================================
File: data_structures/binary_tree/wavelet_tree.py
================================================
"""
Wavelet tree is a data-structure designed to efficiently answer various range queries
for arrays. Wavelets trees are different from other binary trees in the sense that
the nodes are split based on the actual values of the elements and not on indices,
such as the with segment trees or fenwick trees. You can read more about them here:
1. https://users.dcc.uchile.cl/~jperez/papers/ioiconf16.pdf
2. https://www.youtube.com/watch?v=4aSv9PcecDw&t=811s
3. https://www.youtube.com/watch?v=CybAgVF-MMc&t=1178s
"""

from __future__ import annotations

test_array = [2, 1, 4, 5, 6, 0, 8, 9, 1, 2, 0, 6, 4, 2, 0, 6, 5, 3, 2, 7]


class Node:
    def __init__(self, length: int) -> None:
        self.minn: int = -1
        self.maxx: int = -1
        self.map_left: list[int] = [-1] * length
        self.left: Node | None = None
        self.right: Node | None = None

    def __repr__(self) -> str:
        """
        >>> node = Node(length=27)
        >>> repr(node)
        'Node(min_value=-1 max_value=-1)'
        >>> repr(node) == str(node)
        True
        """
        return f"Node(min_value={self.minn} max_value={self.maxx})"


def build_tree(arr: list[int]) -> Node | None:
    """
    Builds the tree for arr and returns the root
    of the constructed tree

    >>> build_tree(test_array)
    Node(min_value=0 max_value=9)
    """
    root = Node(len(arr))
    root.minn, root.maxx = min(arr), max(arr)
    # Leaf node case where the node contains only one unique value
    if root.minn == root.maxx:
        return root
    """
    Take the mean of min and max element of arr as the pivot and
    partition arr into left_arr and right_arr with all elements <= pivot in the
    left_arr and the rest in right_arr, maintaining the order of the elements,
    then recursively build trees for left_arr and right_arr
    """
    pivot = (root.minn + root.maxx) // 2

    left_arr: list[int] = []
    right_arr: list[int] = []

    for index, num in enumerate(arr):
        if num <= pivot:
            left_arr.append(num)
        else:
            right_arr.append(num)
        root.map_left[index] = len(left_arr)
    root.left = build_tree(left_arr)
    root.right = build_tree(right_arr)
    return root


def rank_till_index(node: Node | None, num: int, index: int) -> int:
    """
    Returns the number of occurrences of num in interval [0, index] in the list

    >>> root = build_tree(test_array)
    >>> rank_till_index(root, 6, 6)
    1
    >>> rank_till_index(root, 2, 0)
    1
    >>> rank_till_index(root, 1, 10)
    2
    >>> rank_till_index(root, 17, 7)
    0
    >>> rank_till_index(root, 0, 9)
    1
    """
    if index < 0 or node is None:
        return 0
    # Leaf node cases
    if node.minn == node.maxx:
        return index + 1 if node.minn == num else 0
    pivot = (node.minn + node.maxx) // 2
    if num <= pivot:
        # go the left subtree and map index to the left subtree
        return rank_till_index(node.left, num, node.map_left[index] - 1)
    else:
        # go to the right subtree and map index to the right subtree
        return rank_till_index(node.right, num, index - node.map_left[index])


def rank(node: Node | None, num: int, start: int, end: int) -> int:
    """
    Returns the number of occurrences of num in interval [start, end] in the list

    >>> root = build_tree(test_array)
    >>> rank(root, 6, 3, 13)
    2
    >>> rank(root, 2, 0, 19)
    4
    >>> rank(root, 9, 2 ,2)
    0
    >>> rank(root, 0, 5, 10)
    2
    """
    if start > end:
        return 0
    rank_till_end = rank_till_index(node, num, end)
    rank_before_start = rank_till_index(node, num, start - 1)
    return rank_till_end - rank_before_start


def quantile(node: Node | None, index: int, start: int, end: int) -> int:
    """
    Returns the index'th smallest element in interval [start, end] in the list
    index is 0-indexed

    >>> root = build_tree(test_array)
    >>> quantile(root, 2, 2, 5)
    5
    >>> quantile(root, 5, 2, 13)
    4
    >>> quantile(root, 0, 6, 6)
    8
    >>> quantile(root, 4, 2, 5)
    -1
    """
    if index > (end - start) or start > end or node is None:
        return -1
    # Leaf node case
    if node.minn == node.maxx:
        return node.minn
    # Number of elements in the left subtree in interval [start, end]
    num_elements_in_left_tree = node.map_left[end] - (
        node.map_left[start - 1] if start else 0
    )
    if num_elements_in_left_tree > index:
        return quantile(
            node.left,
            index,
            (node.map_left[start - 1] if start else 0),
            node.map_left[end] - 1,
        )
    else:
        return quantile(
            node.right,
            index - num_elements_in_left_tree,
            start - (node.map_left[start - 1] if start else 0),
            end - node.map_left[end],
        )


def range_counting(
    node: Node | None, start: int, end: int, start_num: int, end_num: int
) -> int:
    """
    Returns the number of elements in range [start_num, end_num]
    in interval [start, end] in the list

    >>> root = build_tree(test_array)
    >>> range_counting(root, 1, 10, 3, 7)
    3
    >>> range_counting(root, 2, 2, 1, 4)
    1
    >>> range_counting(root, 0, 19, 0, 100)
    20
    >>> range_counting(root, 1, 0, 1, 100)
    0
    >>> range_counting(root, 0, 17, 100, 1)
    0
    """
    if (
        start > end
        or node is None
        or start_num > end_num
        or node.minn > end_num
        or node.maxx < start_num
    ):
        return 0
    if start_num <= node.minn and node.maxx <= end_num:
        return end - start + 1
    left = range_counting(
        node.left,
        (node.map_left[start - 1] if start else 0),
        node.map_left[end] - 1,
        start_num,
        end_num,
    )
    right = range_counting(
        node.right,
        start - (node.map_left[start - 1] if start else 0),
        end - node.map_left[end],
        start_num,
        end_num,
    )
    return left + right


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/disjoint_set/alternate_disjoint_set.py
================================================
"""
Implements a disjoint set using Lists and some added heuristics for efficiency
Union by Rank Heuristic and Path Compression
"""


class DisjointSet:
    def __init__(self, set_counts: list) -> None:
        """
        Initialize with a list of the number of items in each set
        and with rank = 1 for each set
        """
        self.set_counts = set_counts
        self.max_set = max(set_counts)
        num_sets = len(set_counts)
        self.ranks = [1] * num_sets
        self.parents = list(range(num_sets))

    def merge(self, src: int, dst: int) -> bool:
        """
        Merge two sets together using Union by rank heuristic
        Return True if successful
        Merge two disjoint sets
        >>> A = DisjointSet([1, 1, 1])
        >>> A.merge(1, 2)
        True
        >>> A.merge(0, 2)
        True
        >>> A.merge(0, 1)
        False
        """
        src_parent = self.get_parent(src)
        dst_parent = self.get_parent(dst)

        if src_parent == dst_parent:
            return False

        if self.ranks[dst_parent] >= self.ranks[src_parent]:
            self.set_counts[dst_parent] += self.set_counts[src_parent]
            self.set_counts[src_parent] = 0
            self.parents[src_parent] = dst_parent
            if self.ranks[dst_parent] == self.ranks[src_parent]:
                self.ranks[dst_parent] += 1
            joined_set_size = self.set_counts[dst_parent]
        else:
            self.set_counts[src_parent] += self.set_counts[dst_parent]
            self.set_counts[dst_parent] = 0
            self.parents[dst_parent] = src_parent
            joined_set_size = self.set_counts[src_parent]

        self.max_set = max(self.max_set, joined_set_size)
        return True

    def get_parent(self, disj_set: int) -> int:
        """
        Find the Parent of a given set
        >>> A = DisjointSet([1, 1, 1])
        >>> A.merge(1, 2)
        True
        >>> A.get_parent(0)
        0
        >>> A.get_parent(1)
        2
        """
        if self.parents[disj_set] == disj_set:
            return disj_set
        self.parents[disj_set] = self.get_parent(self.parents[disj_set])
        return self.parents[disj_set]


================================================
File: data_structures/disjoint_set/disjoint_set.py
================================================
"""
Disjoint set.
Reference: https://en.wikipedia.org/wiki/Disjoint-set_data_structure
"""


class Node:
    def __init__(self, data: int) -> None:
        self.data = data
        self.rank: int
        self.parent: Node


def make_set(x: Node) -> None:
    """
    Make x as a set.
    """
    # rank is the distance from x to its' parent
    # root's rank is 0
    x.rank = 0
    x.parent = x


def union_set(x: Node, y: Node) -> None:
    """
    Union of two sets.
    set with bigger rank should be parent, so that the
    disjoint set tree will be more flat.
    """
    x, y = find_set(x), find_set(y)
    if x == y:
        return

    elif x.rank > y.rank:
        y.parent = x
    else:
        x.parent = y
        if x.rank == y.rank:
            y.rank += 1


def find_set(x: Node) -> Node:
    """
    Return the parent of x
    """
    if x != x.parent:
        x.parent = find_set(x.parent)
    return x.parent


def find_python_set(node: Node) -> set:
    """
    Return a Python Standard Library set that contains i.
    """
    sets = ({0, 1, 2}, {3, 4, 5})
    for s in sets:
        if node.data in s:
            return s
    msg = f"{node.data} is not in {sets}"
    raise ValueError(msg)


def test_disjoint_set() -> None:
    """
    >>> test_disjoint_set()
    """
    vertex = [Node(i) for i in range(6)]
    for v in vertex:
        make_set(v)

    union_set(vertex[0], vertex[1])
    union_set(vertex[1], vertex[2])
    union_set(vertex[3], vertex[4])
    union_set(vertex[3], vertex[5])

    for node0 in vertex:
        for node1 in vertex:
            if find_python_set(node0).isdisjoint(find_python_set(node1)):
                assert find_set(node0) != find_set(node1)
            else:
                assert find_set(node0) == find_set(node1)


if __name__ == "__main__":
    test_disjoint_set()


================================================
File: data_structures/hashing/bloom_filter.py
================================================
"""
See https://en.wikipedia.org/wiki/Bloom_filter

The use of this data structure is to test membership in a set.
Compared to Python's built-in set() it is more space-efficient.
In the following example, only 8 bits of memory will be used:
>>> bloom = Bloom(size=8)

Initially, the filter contains all zeros:
>>> bloom.bitstring
'00000000'

When an element is added, two bits are set to 1
since there are 2 hash functions in this implementation:
>>> "Titanic" in bloom
False
>>> bloom.add("Titanic")
>>> bloom.bitstring
'01100000'
>>> "Titanic" in bloom
True

However, sometimes only one bit is added
because both hash functions return the same value
>>> bloom.add("Avatar")
>>> "Avatar" in bloom
True
>>> bloom.format_hash("Avatar")
'00000100'
>>> bloom.bitstring
'01100100'

Not added elements should return False ...
>>> not_present_films = ("The Godfather", "Interstellar", "Parasite", "Pulp Fiction")
>>> {
...   film: bloom.format_hash(film) for film in not_present_films
... } # doctest: +NORMALIZE_WHITESPACE
{'The Godfather': '00000101',
 'Interstellar': '00000011',
 'Parasite': '00010010',
 'Pulp Fiction': '10000100'}
>>> any(film in bloom for film in not_present_films)
False

but sometimes there are false positives:
>>> "Ratatouille" in bloom
True
>>> bloom.format_hash("Ratatouille")
'01100000'

The probability increases with the number of elements added.
The probability decreases with the number of bits in the bitarray.
>>> bloom.estimated_error_rate
0.140625
>>> bloom.add("The Godfather")
>>> bloom.estimated_error_rate
0.25
>>> bloom.bitstring
'01100101'
"""

from hashlib import md5, sha256

HASH_FUNCTIONS = (sha256, md5)


class Bloom:
    def __init__(self, size: int = 8) -> None:
        self.bitarray = 0b0
        self.size = size

    def add(self, value: str) -> None:
        h = self.hash_(value)
        self.bitarray |= h

    def exists(self, value: str) -> bool:
        h = self.hash_(value)
        return (h & self.bitarray) == h

    def __contains__(self, other: str) -> bool:
        return self.exists(other)

    def format_bin(self, bitarray: int) -> str:
        res = bin(bitarray)[2:]
        return res.zfill(self.size)

    @property
    def bitstring(self) -> str:
        return self.format_bin(self.bitarray)

    def hash_(self, value: str) -> int:
        res = 0b0
        for func in HASH_FUNCTIONS:
            position = (
                int.from_bytes(func(value.encode()).digest(), "little") % self.size
            )
            res |= 2**position
        return res

    def format_hash(self, value: str) -> str:
        return self.format_bin(self.hash_(value))

    @property
    def estimated_error_rate(self) -> float:
        n_ones = bin(self.bitarray).count("1")
        return (n_ones / self.size) ** len(HASH_FUNCTIONS)


================================================
File: data_structures/hashing/double_hash.py
================================================
#!/usr/bin/env python3
"""
Double hashing is a collision resolving technique in Open Addressed Hash tables.
Double hashing uses the idea of applying a second hash function to key when a collision
occurs. The advantage of Double hashing is that it is one of the best form of  probing,
producing a uniform distribution of records throughout a hash table. This technique
does not yield any clusters. It is one of effective method for resolving collisions.

Double hashing can be done using: (hash1(key) + i * hash2(key)) % TABLE_SIZE
Where hash1() and hash2() are hash functions and TABLE_SIZE is size of hash table.

Reference: https://en.wikipedia.org/wiki/Double_hashing
"""

from .hash_table import HashTable
from .number_theory.prime_numbers import is_prime, next_prime


class DoubleHash(HashTable):
    """
    Hash Table example with open addressing and Double Hash
    """

    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)

    def __hash_function_2(self, value, data):
        next_prime_gt = (
            next_prime(value % self.size_table)
            if not is_prime(value % self.size_table)
            else value % self.size_table
        )  # gt = bigger than
        return next_prime_gt - (data % next_prime_gt)

    def __hash_double_function(self, key, data, increment):
        return (increment * self.__hash_function_2(key, data)) % self.size_table

    def _collision_resolution(self, key, data=None):
        """
        Examples:

        1. Try to add three data elements when the size is three
        >>> dh = DoubleHash(3)
        >>> dh.insert_data(10)
        >>> dh.insert_data(20)
        >>> dh.insert_data(30)
        >>> dh.keys()
        {1: 10, 2: 20, 0: 30}

        2. Try to add three data elements when the size is two
        >>> dh = DoubleHash(2)
        >>> dh.insert_data(10)
        >>> dh.insert_data(20)
        >>> dh.insert_data(30)
        >>> dh.keys()
        {10: 10, 9: 20, 8: 30}

        3. Try to add three data elements when the size is four
        >>> dh = DoubleHash(4)
        >>> dh.insert_data(10)
        >>> dh.insert_data(20)
        >>> dh.insert_data(30)
        >>> dh.keys()
        {9: 20, 10: 10, 8: 30}
        """
        i = 1
        new_key = self.hash_function(data)

        while self.values[new_key] is not None and self.values[new_key] != key:
            new_key = (
                self.__hash_double_function(key, data, i)
                if self.balanced_factor() >= self.lim_charge
                else None
            )
            if new_key is None:
                break
            else:
                i += 1

        return new_key


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/hashing/hash_map.py
================================================
"""
Hash map with open addressing.

https://en.wikipedia.org/wiki/Hash_table

Another hash map implementation, with a good explanation.
Modern Dictionaries by Raymond Hettinger
https://www.youtube.com/watch?v=p33CVV29OG8
"""

from collections.abc import Iterator, MutableMapping
from dataclasses import dataclass
from typing import Generic, TypeVar

KEY = TypeVar("KEY")
VAL = TypeVar("VAL")


@dataclass(frozen=True, slots=True)
class _Item(Generic[KEY, VAL]):
    key: KEY
    val: VAL


class _DeletedItem(_Item):
    def __init__(self) -> None:
        super().__init__(None, None)

    def __bool__(self) -> bool:
        return False


_deleted = _DeletedItem()


class HashMap(MutableMapping[KEY, VAL]):
    """
    Hash map with open addressing.
    """

    def __init__(
        self, initial_block_size: int = 8, capacity_factor: float = 0.75
    ) -> None:
        self._initial_block_size = initial_block_size
        self._buckets: list[_Item | None] = [None] * initial_block_size
        assert 0.0 < capacity_factor < 1.0
        self._capacity_factor = capacity_factor
        self._len = 0

    def _get_bucket_index(self, key: KEY) -> int:
        return hash(key) % len(self._buckets)

    def _get_next_ind(self, ind: int) -> int:
        """
        Get next index.

        Implements linear open addressing.
        >>> HashMap(5)._get_next_ind(3)
        4
        >>> HashMap(5)._get_next_ind(5)
        1
        >>> HashMap(5)._get_next_ind(6)
        2
        >>> HashMap(5)._get_next_ind(9)
        0
        """
        return (ind + 1) % len(self._buckets)

    def _try_set(self, ind: int, key: KEY, val: VAL) -> bool:
        """
        Try to add value to the bucket.

        If bucket is empty or key is the same, does insert and return True.

        If bucket has another key or deleted placeholder,
        that means that we need to check next bucket.
        """
        stored = self._buckets[ind]
        if not stored:
            self._buckets[ind] = _Item(key, val)
            self._len += 1
            return True
        elif stored.key == key:
            self._buckets[ind] = _Item(key, val)
            return True
        else:
            return False

    def _is_full(self) -> bool:
        """
        Return true if we have reached safe capacity.

        So we need to increase the number of buckets to avoid collisions.

        >>> hm = HashMap(2)
        >>> hm._add_item(1, 10)
        >>> hm._add_item(2, 20)
        >>> hm._is_full()
        True
        >>> HashMap(2)._is_full()
        False
        """
        limit = len(self._buckets) * self._capacity_factor
        return len(self) >= int(limit)

    def _is_sparse(self) -> bool:
        """Return true if we need twice fewer buckets when we have now."""
        if len(self._buckets) <= self._initial_block_size:
            return False
        limit = len(self._buckets) * self._capacity_factor / 2
        return len(self) < limit

    def _resize(self, new_size: int) -> None:
        old_buckets = self._buckets
        self._buckets = [None] * new_size
        self._len = 0
        for item in old_buckets:
            if item:
                self._add_item(item.key, item.val)

    def _size_up(self) -> None:
        self._resize(len(self._buckets) * 2)

    def _size_down(self) -> None:
        self._resize(len(self._buckets) // 2)

    def _iterate_buckets(self, key: KEY) -> Iterator[int]:
        ind = self._get_bucket_index(key)
        for _ in range(len(self._buckets)):
            yield ind
            ind = self._get_next_ind(ind)

    def _add_item(self, key: KEY, val: VAL) -> None:
        """
        Try to add 3 elements when the size is 5
        >>> hm = HashMap(5)
        >>> hm._add_item(1, 10)
        >>> hm._add_item(2, 20)
        >>> hm._add_item(3, 30)
        >>> hm
        HashMap(1: 10, 2: 20, 3: 30)

        Try to add 3 elements when the size is 5
        >>> hm = HashMap(5)
        >>> hm._add_item(-5, 10)
        >>> hm._add_item(6, 30)
        >>> hm._add_item(-7, 20)
        >>> hm
        HashMap(-5: 10, 6: 30, -7: 20)

        Try to add 3 elements when size is 1
        >>> hm = HashMap(1)
        >>> hm._add_item(10, 13.2)
        >>> hm._add_item(6, 5.26)
        >>> hm._add_item(7, 5.155)
        >>> hm
        HashMap(10: 13.2)

        Trying to add an element with a key that is a floating point value
        >>> hm = HashMap(5)
        >>> hm._add_item(1.5, 10)
        >>> hm
        HashMap(1.5: 10)

        5. Trying to add an item with the same key
        >>> hm = HashMap(5)
        >>> hm._add_item(1, 10)
        >>> hm._add_item(1, 20)
        >>> hm
        HashMap(1: 20)
        """
        for ind in self._iterate_buckets(key):
            if self._try_set(ind, key, val):
                break

    def __setitem__(self, key: KEY, val: VAL) -> None:
        """
        1. Changing value of item whose key is present
        >>> hm = HashMap(5)
        >>> hm._add_item(1, 10)
        >>> hm.__setitem__(1, 20)
        >>> hm
        HashMap(1: 20)

        2. Changing value of item whose key is not present
        >>> hm = HashMap(5)
        >>> hm._add_item(1, 10)
        >>> hm.__setitem__(0, 20)
        >>> hm
        HashMap(0: 20, 1: 10)

        3. Changing the value of the same item multiple times
        >>> hm = HashMap(5)
        >>> hm._add_item(1, 10)
        >>> hm.__setitem__(1, 20)
        >>> hm.__setitem__(1, 30)
        >>> hm
        HashMap(1: 30)
        """
        if self._is_full():
            self._size_up()

        self._add_item(key, val)

    def __delitem__(self, key: KEY) -> None:
        """
        >>> hm = HashMap(5)
        >>> hm._add_item(1, 10)
        >>> hm._add_item(2, 20)
        >>> hm._add_item(3, 30)
        >>> hm.__delitem__(3)
        >>> hm
        HashMap(1: 10, 2: 20)
        >>> hm = HashMap(5)
        >>> hm._add_item(-5, 10)
        >>> hm._add_item(6, 30)
        >>> hm._add_item(-7, 20)
        >>> hm.__delitem__(-5)
        >>> hm
        HashMap(6: 30, -7: 20)

        # Trying to remove a non-existing item
        >>> hm = HashMap(5)
        >>> hm._add_item(1, 10)
        >>> hm._add_item(2, 20)
        >>> hm._add_item(3, 30)
        >>> hm.__delitem__(4)
        Traceback (most recent call last):
        ...
        KeyError: 4
        """
        for ind in self._iterate_buckets(key):
            item = self._buckets[ind]
            if item is None:
                raise KeyError(key)
            if item is _deleted:
                continue
            if item.key == key:
                self._buckets[ind] = _deleted
                self._len -= 1
                break
        if self._is_sparse():
            self._size_down()

    def __getitem__(self, key: KEY) -> VAL:
        """
        Returns the item at the given key

        >>> hm = HashMap(5)
        >>> hm._add_item(1, 10)
        >>> hm.__getitem__(1)
        10

        >>> hm = HashMap(5)
        >>> hm._add_item(10, -10)
        >>> hm._add_item(20, -20)
        >>> hm.__getitem__(20)
        -20

        >>> hm = HashMap(5)
        >>> hm._add_item(-1, 10)
        >>> hm.__getitem__(-1)
        10
        """
        for ind in self._iterate_buckets(key):
            item = self._buckets[ind]
            if item is None:
                break
            if item is _deleted:
                continue
            if item.key == key:
                return item.val
        raise KeyError(key)

    def __len__(self) -> int:
        """
        Returns the number of items present in hashmap

        >>> hm = HashMap(5)
        >>> hm._add_item(1, 10)
        >>> hm._add_item(2, 20)
        >>> hm._add_item(3, 30)
        >>> hm.__len__()
        3

        >>> hm = HashMap(5)
        >>> hm.__len__()
        0
        """
        return self._len

    def __iter__(self) -> Iterator[KEY]:
        yield from (item.key for item in self._buckets if item)

    def __repr__(self) -> str:
        val_string = ", ".join(
            f"{item.key}: {item.val}" for item in self._buckets if item
        )
        return f"HashMap({val_string})"


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/hashing/hash_table.py
================================================
#!/usr/bin/env python3
from abc import abstractmethod

from .number_theory.prime_numbers import next_prime


class HashTable:
    """
    Basic Hash Table example with open addressing and linear probing
    """

    def __init__(
        self,
        size_table: int,
        charge_factor: int | None = None,
        lim_charge: float | None = None,
    ) -> None:
        self.size_table = size_table
        self.values = [None] * self.size_table
        self.lim_charge = 0.75 if lim_charge is None else lim_charge
        self.charge_factor = 1 if charge_factor is None else charge_factor
        self.__aux_list: list = []
        self._keys: dict = {}

    def keys(self):
        """
        The keys function returns a dictionary containing the key value pairs.
        key being the index number in hash table and value being the data value.

        Examples:
        1. creating HashTable with size 10 and inserting 3 elements
        >>> ht = HashTable(10)
        >>> ht.insert_data(10)
        >>> ht.insert_data(20)
        >>> ht.insert_data(30)
        >>> ht.keys()
        {0: 10, 1: 20, 2: 30}

        2. creating HashTable with size 5 and inserting 5 elements
        >>> ht = HashTable(5)
        >>> ht.insert_data(5)
        >>> ht.insert_data(4)
        >>> ht.insert_data(3)
        >>> ht.insert_data(2)
        >>> ht.insert_data(1)
        >>> ht.keys()
        {0: 5, 4: 4, 3: 3, 2: 2, 1: 1}
        """
        return self._keys

    def balanced_factor(self):
        return sum(1 for slot in self.values if slot is not None) / (
            self.size_table * self.charge_factor
        )

    def hash_function(self, key):
        """
        Generates hash for the given key value

        Examples:

        Creating HashTable with size 5
        >>> ht = HashTable(5)
        >>> ht.hash_function(10)
        0
        >>> ht.hash_function(20)
        0
        >>> ht.hash_function(4)
        4
        >>> ht.hash_function(18)
        3
        >>> ht.hash_function(-18)
        2
        >>> ht.hash_function(18.5)
        3.5
        >>> ht.hash_function(0)
        0
        >>> ht.hash_function(-0)
        0
        """
        return key % self.size_table

    def _step_by_step(self, step_ord):
        print(f"step {step_ord}")
        print(list(range(len(self.values))))
        print(self.values)

    def bulk_insert(self, values):
        """
        bulk_insert is used for entering more than one element at a time
        in the HashTable.

        Examples:
        1.
        >>> ht = HashTable(5)
        >>> ht.bulk_insert((10,20,30))
        step 1
        [0, 1, 2, 3, 4]
        [10, None, None, None, None]
        step 2
        [0, 1, 2, 3, 4]
        [10, 20, None, None, None]
        step 3
        [0, 1, 2, 3, 4]
        [10, 20, 30, None, None]

        2.
        >>> ht = HashTable(5)
        >>> ht.bulk_insert([5,4,3,2,1])
        step 1
        [0, 1, 2, 3, 4]
        [5, None, None, None, None]
        step 2
        [0, 1, 2, 3, 4]
        [5, None, None, None, 4]
        step 3
        [0, 1, 2, 3, 4]
        [5, None, None, 3, 4]
        step 4
        [0, 1, 2, 3, 4]
        [5, None, 2, 3, 4]
        step 5
        [0, 1, 2, 3, 4]
        [5, 1, 2, 3, 4]
        """
        i = 1
        self.__aux_list = values
        for value in values:
            self.insert_data(value)
            self._step_by_step(i)
            i += 1

    def _set_value(self, key, data):
        """
        _set_value functions allows to update value at a particular hash

        Examples:
        1. _set_value in HashTable of size 5
        >>> ht = HashTable(5)
        >>> ht.insert_data(10)
        >>> ht.insert_data(20)
        >>> ht.insert_data(30)
        >>> ht._set_value(0,15)
        >>> ht.keys()
        {0: 15, 1: 20, 2: 30}

        2. _set_value in HashTable of size 2
        >>> ht = HashTable(2)
        >>> ht.insert_data(17)
        >>> ht.insert_data(18)
        >>> ht.insert_data(99)
        >>> ht._set_value(3,15)
        >>> ht.keys()
        {3: 15, 2: 17, 4: 99}

        3. _set_value in HashTable when hash is not present
        >>> ht = HashTable(2)
        >>> ht.insert_data(17)
        >>> ht.insert_data(18)
        >>> ht.insert_data(99)
        >>> ht._set_value(0,15)
        >>> ht.keys()
        {3: 18, 2: 17, 4: 99, 0: 15}

        4. _set_value in HashTable when multiple hash are not present
        >>> ht = HashTable(2)
        >>> ht.insert_data(17)
        >>> ht.insert_data(18)
        >>> ht.insert_data(99)
        >>> ht._set_value(0,15)
        >>> ht._set_value(1,20)
        >>> ht.keys()
        {3: 18, 2: 17, 4: 99, 0: 15, 1: 20}
        """
        self.values[key] = data
        self._keys[key] = data

    @abstractmethod
    def _collision_resolution(self, key, data=None):
        """
        This method is a type of open addressing which is used for handling collision.

        In this implementation the concept of linear probing has been used.

        The hash table is searched sequentially from the original location of the
        hash, if the new hash/location we get is already occupied we check for the next
        hash/location.

        references:
            - https://en.wikipedia.org/wiki/Linear_probing

        Examples:
        1. The collision will be with keys 18 & 99, so new hash will be created for 99
        >>> ht = HashTable(3)
        >>> ht.insert_data(17)
        >>> ht.insert_data(18)
        >>> ht.insert_data(99)
        >>> ht.keys()
        {2: 17, 0: 18, 1: 99}

        2. The collision will be with keys 17 & 101, so new hash
        will be created for 101
        >>> ht = HashTable(4)
        >>> ht.insert_data(17)
        >>> ht.insert_data(18)
        >>> ht.insert_data(99)
        >>> ht.insert_data(101)
        >>> ht.keys()
        {1: 17, 2: 18, 3: 99, 0: 101}

        2. The collision will be with all keys, so new hash will be created for all
        >>> ht = HashTable(1)
        >>> ht.insert_data(17)
        >>> ht.insert_data(18)
        >>> ht.insert_data(99)
        >>> ht.keys()
        {2: 17, 3: 18, 4: 99}

        3. Trying to insert float key in hash
        >>> ht = HashTable(1)
        >>> ht.insert_data(17)
        >>> ht.insert_data(18)
        >>> ht.insert_data(99.99)
        Traceback (most recent call last):
        ...
        TypeError: list indices must be integers or slices, not float
        """
        new_key = self.hash_function(key + 1)

        while self.values[new_key] is not None and self.values[new_key] != key:
            if self.values.count(None) > 0:
                new_key = self.hash_function(new_key + 1)
            else:
                new_key = None
                break

        return new_key

    def rehashing(self):
        survivor_values = [value for value in self.values if value is not None]
        self.size_table = next_prime(self.size_table, factor=2)
        self._keys.clear()
        self.values = [None] * self.size_table  # hell's pointers D: don't DRY ;/
        for value in survivor_values:
            self.insert_data(value)

    def insert_data(self, data):
        """
        insert_data is used for inserting a single element at a time in the HashTable.

        Examples:

        >>> ht = HashTable(3)
        >>> ht.insert_data(5)
        >>> ht.keys()
        {2: 5}
        >>> ht = HashTable(5)
        >>> ht.insert_data(30)
        >>> ht.insert_data(50)
        >>> ht.keys()
        {0: 30, 1: 50}
        """
        key = self.hash_function(data)

        if self.values[key] is None:
            self._set_value(key, data)

        elif self.values[key] == data:
            pass

        else:
            collision_resolution = self._collision_resolution(key, data)
            if collision_resolution is not None:
                self._set_value(collision_resolution, data)
            else:
                self.rehashing()
                self.insert_data(data)


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/hashing/hash_table_with_linked_list.py
================================================
from collections import deque

from .hash_table import HashTable


class HashTableWithLinkedList(HashTable):
    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)

    def _set_value(self, key, data):
        self.values[key] = deque([]) if self.values[key] is None else self.values[key]
        self.values[key].appendleft(data)
        self._keys[key] = self.values[key]

    def balanced_factor(self):
        return (
            sum(self.charge_factor - len(slot) for slot in self.values)
            / self.size_table
            * self.charge_factor
        )

    def _collision_resolution(self, key, data=None):
        if not (
            len(self.values[key]) == self.charge_factor and self.values.count(None) == 0
        ):
            return key
        return super()._collision_resolution(key, data)


================================================
File: data_structures/hashing/quadratic_probing.py
================================================
#!/usr/bin/env python3

from .hash_table import HashTable


class QuadraticProbing(HashTable):
    """
    Basic Hash Table example with open addressing using Quadratic Probing
    """

    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)

    def _collision_resolution(self, key, data=None):  # noqa: ARG002
        """
        Quadratic probing is an open addressing scheme used for resolving
        collisions in hash table.

        It works by taking the original hash index and adding successive
        values of an arbitrary quadratic polynomial until open slot is found.

        Hash + 1², Hash + 2², Hash + 3² .... Hash + n²

        reference:
            - https://en.wikipedia.org/wiki/Quadratic_probing
        e.g:
        1. Create hash table with size 7
        >>> qp = QuadraticProbing(7)
        >>> qp.insert_data(90)
        >>> qp.insert_data(340)
        >>> qp.insert_data(24)
        >>> qp.insert_data(45)
        >>> qp.insert_data(99)
        >>> qp.insert_data(73)
        >>> qp.insert_data(7)
        >>> qp.keys()
        {11: 45, 14: 99, 7: 24, 0: 340, 5: 73, 6: 90, 8: 7}

        2. Create hash table with size 8
        >>> qp = QuadraticProbing(8)
        >>> qp.insert_data(0)
        >>> qp.insert_data(999)
        >>> qp.insert_data(111)
        >>> qp.keys()
        {0: 0, 7: 999, 3: 111}

        3. Try to add three data elements when the size is two
        >>> qp =  QuadraticProbing(2)
        >>> qp.insert_data(0)
        >>> qp.insert_data(999)
        >>> qp.insert_data(111)
        >>> qp.keys()
        {0: 0, 4: 999, 1: 111}

        4. Try to add three data elements when the size is one
        >>> qp =  QuadraticProbing(1)
        >>> qp.insert_data(0)
        >>> qp.insert_data(999)
        >>> qp.insert_data(111)
        >>> qp.keys()
        {4: 999, 1: 111}
        """

        i = 1
        new_key = self.hash_function(key + i * i)

        while self.values[new_key] is not None and self.values[new_key] != key:
            i += 1
            new_key = (
                self.hash_function(key + i * i)
                if not self.balanced_factor() >= self.lim_charge
                else None
            )

            if new_key is None:
                break

        return new_key


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/hashing/number_theory/prime_numbers.py
================================================
#!/usr/bin/env python3
"""
module to operations with prime numbers
"""

import math


def is_prime(number: int) -> bool:
    """Checks to see if a number is a prime in O(sqrt(n)).

    A number is prime if it has exactly two factors: 1 and itself.

    >>> is_prime(0)
    False
    >>> is_prime(1)
    False
    >>> is_prime(2)
    True
    >>> is_prime(3)
    True
    >>> is_prime(27)
    False
    >>> is_prime(87)
    False
    >>> is_prime(563)
    True
    >>> is_prime(2999)
    True
    >>> is_prime(67483)
    False
    """

    # precondition
    assert isinstance(number, int) and (number >= 0), (
        "'number' must been an int and positive"
    )

    if 1 < number < 4:
        # 2 and 3 are primes
        return True
    elif number < 2 or not number % 2:
        # Negatives, 0, 1 and all even numbers are not primes
        return False

    odd_numbers = range(3, int(math.sqrt(number) + 1), 2)
    return not any(not number % i for i in odd_numbers)


def next_prime(value, factor=1, **kwargs):
    value = factor * value
    first_value_val = value

    while not is_prime(value):
        value += 1 if not ("desc" in kwargs and kwargs["desc"] is True) else -1

    if value == first_value_val:
        return next_prime(value + 1, **kwargs)
    return value


================================================
File: data_structures/hashing/tests/test_hash_map.py
================================================
from operator import delitem, getitem, setitem

import pytest

from data_structures.hashing.hash_map import HashMap


def _get(k):
    return getitem, k


def _set(k, v):
    return setitem, k, v


def _del(k):
    return delitem, k


def _run_operation(obj, fun, *args):
    try:
        return fun(obj, *args), None
    except Exception as e:
        return None, e


_add_items = (
    _set("key_a", "val_a"),
    _set("key_b", "val_b"),
)

_overwrite_items = [
    _set("key_a", "val_a"),
    _set("key_a", "val_b"),
]

_delete_items = [
    _set("key_a", "val_a"),
    _set("key_b", "val_b"),
    _del("key_a"),
    _del("key_b"),
    _set("key_a", "val_a"),
    _del("key_a"),
]

_access_absent_items = [
    _get("key_a"),
    _del("key_a"),
    _set("key_a", "val_a"),
    _del("key_a"),
    _del("key_a"),
    _get("key_a"),
]

_add_with_resize_up = [
    *[_set(x, x) for x in range(5)],  # guaranteed upsize
]

_add_with_resize_down = [
    *[_set(x, x) for x in range(5)],  # guaranteed upsize
    *[_del(x) for x in range(5)],
    _set("key_a", "val_b"),
]


@pytest.mark.parametrize(
    "operations",
    [
        pytest.param(_add_items, id="add items"),
        pytest.param(_overwrite_items, id="overwrite items"),
        pytest.param(_delete_items, id="delete items"),
        pytest.param(_access_absent_items, id="access absent items"),
        pytest.param(_add_with_resize_up, id="add with resize up"),
        pytest.param(_add_with_resize_down, id="add with resize down"),
    ],
)
def test_hash_map_is_the_same_as_dict(operations):
    my = HashMap(initial_block_size=4)
    py = {}
    for _, (fun, *args) in enumerate(operations):
        my_res, my_exc = _run_operation(my, fun, *args)
        py_res, py_exc = _run_operation(py, fun, *args)
        assert my_res == py_res
        assert str(my_exc) == str(py_exc)
        assert set(py) == set(my)
        assert len(py) == len(my)
        assert set(my.items()) == set(py.items())


def test_no_new_methods_was_added_to_api():
    def is_public(name: str) -> bool:
        return not name.startswith("_")

    dict_public_names = {name for name in dir({}) if is_public(name)}
    hash_public_names = {name for name in dir(HashMap()) if is_public(name)}

    assert dict_public_names > hash_public_names


================================================
File: data_structures/heap/binomial_heap.py
================================================
"""
Binomial Heap
Reference: Advanced Data Structures, Peter Brass
"""


class Node:
    """
    Node in a doubly-linked binomial tree, containing:
        - value
        - size of left subtree
        - link to left, right and parent nodes
    """

    def __init__(self, val):
        self.val = val
        # Number of nodes in left subtree
        self.left_tree_size = 0
        self.left = None
        self.right = None
        self.parent = None

    def merge_trees(self, other):
        """
        In-place merge of two binomial trees of equal size.
        Returns the root of the resulting tree
        """
        assert self.left_tree_size == other.left_tree_size, "Unequal Sizes of Blocks"

        if self.val < other.val:
            other.left = self.right
            other.parent = None
            if self.right:
                self.right.parent = other
            self.right = other
            self.left_tree_size = self.left_tree_size * 2 + 1
            return self
        else:
            self.left = other.right
            self.parent = None
            if other.right:
                other.right.parent = self
            other.right = self
            other.left_tree_size = other.left_tree_size * 2 + 1
            return other


class BinomialHeap:
    r"""
    Min-oriented priority queue implemented with the Binomial Heap data
    structure implemented with the BinomialHeap class. It supports:
        - Insert element in a heap with n elements: Guaranteed logn, amoratized 1
        - Merge (meld) heaps of size m and n: O(logn + logm)
        - Delete Min: O(logn)
        - Peek (return min without deleting it): O(1)

    Example:

    Create a random permutation of 30 integers to be inserted and 19 of them deleted
    >>> import numpy as np
    >>> permutation = np.random.permutation(list(range(30)))

    Create a Heap and insert the 30 integers
    __init__() test
    >>> first_heap = BinomialHeap()

    30 inserts - insert() test
    >>> for number in permutation:
    ...     first_heap.insert(number)

    Size test
    >>> first_heap.size
    30

    Deleting - delete() test
    >>> [int(first_heap.delete_min()) for _ in range(20)]
    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]

    Create a new Heap
    >>> second_heap = BinomialHeap()
    >>> vals = [17, 20, 31, 34]
    >>> for value in vals:
    ...     second_heap.insert(value)


    The heap should have the following structure:

                    17
                   /  \
                  #    31
                      /  \
                    20    34
                   /  \  /  \
                  #    # #   #

    preOrder() test
    >>> " ".join(str(x) for x in second_heap.pre_order())
    "(17, 0) ('#', 1) (31, 1) (20, 2) ('#', 3) ('#', 3) (34, 2) ('#', 3) ('#', 3)"

    printing Heap - __str__() test
    >>> print(second_heap)
    17
    -#
    -31
    --20
    ---#
    ---#
    --34
    ---#
    ---#

    mergeHeaps() test
    >>>
    >>> merged = second_heap.merge_heaps(first_heap)
    >>> merged.peek()
    17

    values in merged heap; (merge is inplace)
    >>> results = []
    >>> while not first_heap.is_empty():
    ...     results.append(int(first_heap.delete_min()))
    >>> results
    [17, 20, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 31, 34]
    """

    def __init__(self, bottom_root=None, min_node=None, heap_size=0):
        self.size = heap_size
        self.bottom_root = bottom_root
        self.min_node = min_node

    def merge_heaps(self, other):
        """
        In-place merge of two binomial heaps.
        Both of them become the resulting merged heap
        """

        # Empty heaps corner cases
        if other.size == 0:
            return None
        if self.size == 0:
            self.size = other.size
            self.bottom_root = other.bottom_root
            self.min_node = other.min_node
            return None
        # Update size
        self.size = self.size + other.size

        # Update min.node
        if self.min_node.val > other.min_node.val:
            self.min_node = other.min_node
        # Merge

        # Order roots by left_subtree_size
        combined_roots_list = []
        i, j = self.bottom_root, other.bottom_root
        while i or j:
            if i and ((not j) or i.left_tree_size < j.left_tree_size):
                combined_roots_list.append((i, True))
                i = i.parent
            else:
                combined_roots_list.append((j, False))
                j = j.parent
        # Insert links between them
        for i in range(len(combined_roots_list) - 1):
            if combined_roots_list[i][1] != combined_roots_list[i + 1][1]:
                combined_roots_list[i][0].parent = combined_roots_list[i + 1][0]
                combined_roots_list[i + 1][0].left = combined_roots_list[i][0]
        # Consecutively merge roots with same left_tree_size
        i = combined_roots_list[0][0]
        while i.parent:
            if (
                (i.left_tree_size == i.parent.left_tree_size) and (not i.parent.parent)
            ) or (
                i.left_tree_size == i.parent.left_tree_size
                and i.left_tree_size != i.parent.parent.left_tree_size
            ):
                # Neighbouring Nodes
                previous_node = i.left
                next_node = i.parent.parent

                # Merging trees
                i = i.merge_trees(i.parent)

                # Updating links
                i.left = previous_node
                i.parent = next_node
                if previous_node:
                    previous_node.parent = i
                if next_node:
                    next_node.left = i
            else:
                i = i.parent
        # Updating self.bottom_root
        while i.left:
            i = i.left
        self.bottom_root = i

        # Update other
        other.size = self.size
        other.bottom_root = self.bottom_root
        other.min_node = self.min_node

        # Return the merged heap
        return self

    def insert(self, val):
        """
        insert a value in the heap
        """
        if self.size == 0:
            self.bottom_root = Node(val)
            self.size = 1
            self.min_node = self.bottom_root
        else:
            # Create new node
            new_node = Node(val)

            # Update size
            self.size += 1

            # update min_node
            if val < self.min_node.val:
                self.min_node = new_node
            # Put new_node as a bottom_root in heap
            self.bottom_root.left = new_node
            new_node.parent = self.bottom_root
            self.bottom_root = new_node

            # Consecutively merge roots with same left_tree_size
            while (
                self.bottom_root.parent
                and self.bottom_root.left_tree_size
                == self.bottom_root.parent.left_tree_size
            ):
                # Next node
                next_node = self.bottom_root.parent.parent

                # Merge
                self.bottom_root = self.bottom_root.merge_trees(self.bottom_root.parent)

                # Update Links
                self.bottom_root.parent = next_node
                self.bottom_root.left = None
                if next_node:
                    next_node.left = self.bottom_root

    def peek(self):
        """
        return min element without deleting it
        """
        return self.min_node.val

    def is_empty(self):
        return self.size == 0

    def delete_min(self):
        """
        delete min element and return it
        """
        # assert not self.isEmpty(), "Empty Heap"

        # Save minimal value
        min_value = self.min_node.val

        # Last element in heap corner case
        if self.size == 1:
            # Update size
            self.size = 0

            # Update bottom root
            self.bottom_root = None

            # Update min_node
            self.min_node = None

            return min_value
        # No right subtree corner case
        # The structure of the tree implies that this should be the bottom root
        # and there is at least one other root
        if self.min_node.right is None:
            # Update size
            self.size -= 1

            # Update bottom root
            self.bottom_root = self.bottom_root.parent
            self.bottom_root.left = None

            # Update min_node
            self.min_node = self.bottom_root
            i = self.bottom_root.parent
            while i:
                if i.val < self.min_node.val:
                    self.min_node = i
                i = i.parent
            return min_value
        # General case
        # Find the BinomialHeap of the right subtree of min_node
        bottom_of_new = self.min_node.right
        bottom_of_new.parent = None
        min_of_new = bottom_of_new
        size_of_new = 1

        # Size, min_node and bottom_root
        while bottom_of_new.left:
            size_of_new = size_of_new * 2 + 1
            bottom_of_new = bottom_of_new.left
            if bottom_of_new.val < min_of_new.val:
                min_of_new = bottom_of_new
        # Corner case of single root on top left path
        if (not self.min_node.left) and (not self.min_node.parent):
            self.size = size_of_new
            self.bottom_root = bottom_of_new
            self.min_node = min_of_new
            # print("Single root, multiple nodes case")
            return min_value
        # Remaining cases
        # Construct heap of right subtree
        new_heap = BinomialHeap(
            bottom_root=bottom_of_new, min_node=min_of_new, heap_size=size_of_new
        )

        # Update size
        self.size = self.size - 1 - size_of_new

        # Neighbour nodes
        previous_node = self.min_node.left
        next_node = self.min_node.parent

        # Initialize new bottom_root and min_node
        self.min_node = previous_node or next_node
        self.bottom_root = next_node

        # Update links of previous_node and search below for new min_node and
        # bottom_root
        if previous_node:
            previous_node.parent = next_node

            # Update bottom_root and search for min_node below
            self.bottom_root = previous_node
            self.min_node = previous_node
            while self.bottom_root.left:
                self.bottom_root = self.bottom_root.left
                if self.bottom_root.val < self.min_node.val:
                    self.min_node = self.bottom_root
        if next_node:
            next_node.left = previous_node

            # Search for new min_node above min_node
            i = next_node
            while i:
                if i.val < self.min_node.val:
                    self.min_node = i
                i = i.parent
        # Merge heaps
        self.merge_heaps(new_heap)

        return int(min_value)

    def pre_order(self):
        """
        Returns the Pre-order representation of the heap including
        values of nodes plus their level distance from the root;
        Empty nodes appear as #
        """
        # Find top root
        top_root = self.bottom_root
        while top_root.parent:
            top_root = top_root.parent
        # preorder
        heap_pre_order = []
        self.__traversal(top_root, heap_pre_order)
        return heap_pre_order

    def __traversal(self, curr_node, preorder, level=0):
        """
        Pre-order traversal of nodes
        """
        if curr_node:
            preorder.append((curr_node.val, level))
            self.__traversal(curr_node.left, preorder, level + 1)
            self.__traversal(curr_node.right, preorder, level + 1)
        else:
            preorder.append(("#", level))

    def __str__(self):
        """
        Overwriting str for a pre-order print of nodes in heap;
        Performance is poor, so use only for small examples
        """
        if self.is_empty():
            return ""
        preorder_heap = self.pre_order()

        return "\n".join(("-" * level + str(value)) for value, level in preorder_heap)


# Unit Tests
if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/heap/heap.py
================================================
from __future__ import annotations

from abc import abstractmethod
from collections.abc import Iterable
from typing import Generic, Protocol, TypeVar


class Comparable(Protocol):
    @abstractmethod
    def __lt__(self: T, other: T) -> bool:
        pass

    @abstractmethod
    def __gt__(self: T, other: T) -> bool:
        pass

    @abstractmethod
    def __eq__(self: T, other: object) -> bool:
        pass


T = TypeVar("T", bound=Comparable)


class Heap(Generic[T]):
    """A Max Heap Implementation

    >>> unsorted = [103, 9, 1, 7, 11, 15, 25, 201, 209, 107, 5]
    >>> h = Heap()
    >>> h.build_max_heap(unsorted)
    >>> h
    [209, 201, 25, 103, 107, 15, 1, 9, 7, 11, 5]
    >>>
    >>> h.extract_max()
    209
    >>> h
    [201, 107, 25, 103, 11, 15, 1, 9, 7, 5]
    >>>
    >>> h.insert(100)
    >>> h
    [201, 107, 25, 103, 100, 15, 1, 9, 7, 5, 11]
    >>>
    >>> h.heap_sort()
    >>> h
    [1, 5, 7, 9, 11, 15, 25, 100, 103, 107, 201]
    """

    def __init__(self) -> None:
        self.h: list[T] = []
        self.heap_size: int = 0

    def __repr__(self) -> str:
        return str(self.h)

    def parent_index(self, child_idx: int) -> int | None:
        """
        returns the parent index based on the given child index

        >>> h = Heap()
        >>> h.build_max_heap([103, 9, 1, 7, 11, 15, 25, 201, 209, 107, 5])
        >>> h
        [209, 201, 25, 103, 107, 15, 1, 9, 7, 11, 5]

        >>> h.parent_index(-1)  # returns none if index is <=0

        >>> h.parent_index(0)   # returns none if index is <=0

        >>> h.parent_index(1)
        0
        >>> h.parent_index(2)
        0
        >>> h.parent_index(3)
        1
        >>> h.parent_index(4)
        1
        >>> h.parent_index(5)
        2
        >>> h.parent_index(10.5)
        4.0
        >>> h.parent_index(209.0)
        104.0
        >>> h.parent_index("Test")
        Traceback (most recent call last):
        ...
        TypeError: '>' not supported between instances of 'str' and 'int'
        """
        if child_idx > 0:
            return (child_idx - 1) // 2
        return None

    def left_child_idx(self, parent_idx: int) -> int | None:
        """
        return the left child index if the left child exists.
        if not, return None.
        """
        left_child_index = 2 * parent_idx + 1
        if left_child_index < self.heap_size:
            return left_child_index
        return None

    def right_child_idx(self, parent_idx: int) -> int | None:
        """
        return the right child index if the right child exists.
        if not, return None.
        """
        right_child_index = 2 * parent_idx + 2
        if right_child_index < self.heap_size:
            return right_child_index
        return None

    def max_heapify(self, index: int) -> None:
        """
        correct a single violation of the heap property in a subtree's root.

        It is the function that is responsible for restoring the property
        of Max heap i.e the maximum element is always at top.
        """
        if index < self.heap_size:
            violation: int = index
            left_child = self.left_child_idx(index)
            right_child = self.right_child_idx(index)
            # check which child is larger than its parent
            if left_child is not None and self.h[left_child] > self.h[violation]:
                violation = left_child
            if right_child is not None and self.h[right_child] > self.h[violation]:
                violation = right_child
            # if violation indeed exists
            if violation != index:
                # swap to fix the violation
                self.h[violation], self.h[index] = self.h[index], self.h[violation]
                # fix the subsequent violation recursively if any
                self.max_heapify(violation)

    def build_max_heap(self, collection: Iterable[T]) -> None:
        """
        build max heap from an unsorted array

        >>> h = Heap()
        >>> h.build_max_heap([20,40,50,20,10])
        >>> h
        [50, 40, 20, 20, 10]

        >>> h = Heap()
        >>> h.build_max_heap([1,2,3,4,5,6,7,8,9,0])
        >>> h
        [9, 8, 7, 4, 5, 6, 3, 2, 1, 0]

        >>> h = Heap()
        >>> h.build_max_heap([514,5,61,57,8,99,105])
        >>> h
        [514, 57, 105, 5, 8, 99, 61]

        >>> h = Heap()
        >>> h.build_max_heap([514,5,61.6,57,8,9.9,105])
        >>> h
        [514, 57, 105, 5, 8, 9.9, 61.6]
        """
        self.h = list(collection)
        self.heap_size = len(self.h)
        if self.heap_size > 1:
            # max_heapify from right to left but exclude leaves (last level)
            for i in range(self.heap_size // 2 - 1, -1, -1):
                self.max_heapify(i)

    def extract_max(self) -> T:
        """
        get and remove max from heap

        >>> h = Heap()
        >>> h.build_max_heap([20,40,50,20,10])
        >>> h.extract_max()
        50

        >>> h = Heap()
        >>> h.build_max_heap([514,5,61,57,8,99,105])
        >>> h.extract_max()
        514

        >>> h = Heap()
        >>> h.build_max_heap([1,2,3,4,5,6,7,8,9,0])
        >>> h.extract_max()
        9
        """
        if self.heap_size >= 2:
            me = self.h[0]
            self.h[0] = self.h.pop(-1)
            self.heap_size -= 1
            self.max_heapify(0)
            return me
        elif self.heap_size == 1:
            self.heap_size -= 1
            return self.h.pop(-1)
        else:
            raise Exception("Empty heap")

    def insert(self, value: T) -> None:
        """
        insert a new value into the max heap

        >>> h = Heap()
        >>> h.insert(10)
        >>> h
        [10]

        >>> h = Heap()
        >>> h.insert(10)
        >>> h.insert(10)
        >>> h
        [10, 10]

        >>> h = Heap()
        >>> h.insert(10)
        >>> h.insert(10.1)
        >>> h
        [10.1, 10]

        >>> h = Heap()
        >>> h.insert(0.1)
        >>> h.insert(0)
        >>> h.insert(9)
        >>> h.insert(5)
        >>> h
        [9, 5, 0.1, 0]
        """
        self.h.append(value)
        idx = (self.heap_size - 1) // 2
        self.heap_size += 1
        while idx >= 0:
            self.max_heapify(idx)
            idx = (idx - 1) // 2

    def heap_sort(self) -> None:
        size = self.heap_size
        for j in range(size - 1, 0, -1):
            self.h[0], self.h[j] = self.h[j], self.h[0]
            self.heap_size -= 1
            self.max_heapify(0)
        self.heap_size = size


if __name__ == "__main__":
    import doctest

    # run doc test
    doctest.testmod()

    # demo
    for unsorted in [
        [0],
        [2],
        [3, 5],
        [5, 3],
        [5, 5],
        [0, 0, 0, 0],
        [1, 1, 1, 1],
        [2, 2, 3, 5],
        [0, 2, 2, 3, 5],
        [2, 5, 3, 0, 2, 3, 0, 3],
        [6, 1, 2, 7, 9, 3, 4, 5, 10, 8],
        [103, 9, 1, 7, 11, 15, 25, 201, 209, 107, 5],
        [-45, -2, -5],
    ]:
        print(f"unsorted array: {unsorted}")

        heap: Heap[int] = Heap()
        heap.build_max_heap(unsorted)
        print(f"after build heap: {heap}")

        print(f"max value: {heap.extract_max()}")
        print(f"after max value removed: {heap}")

        heap.insert(100)
        print(f"after new value 100 inserted: {heap}")

        heap.heap_sort()
        print(f"heap-sorted array: {heap}\n")


================================================
File: data_structures/heap/heap_generic.py
================================================
from collections.abc import Callable


class Heap:
    """
    A generic Heap class, can be used as min or max by passing the key function
    accordingly.
    """

    def __init__(self, key: Callable | None = None) -> None:
        # Stores actual heap items.
        self.arr: list = []
        # Stores indexes of each item for supporting updates and deletion.
        self.pos_map: dict = {}
        # Stores current size of heap.
        self.size = 0
        # Stores function used to evaluate the score of an item on which basis ordering
        # will be done.
        self.key = key or (lambda x: x)

    def _parent(self, i: int) -> int | None:
        """Returns parent index of given index if exists else None"""
        return int((i - 1) / 2) if i > 0 else None

    def _left(self, i: int) -> int | None:
        """Returns left-child-index of given index if exists else None"""
        left = int(2 * i + 1)
        return left if 0 < left < self.size else None

    def _right(self, i: int) -> int | None:
        """Returns right-child-index of given index if exists else None"""
        right = int(2 * i + 2)
        return right if 0 < right < self.size else None

    def _swap(self, i: int, j: int) -> None:
        """Performs changes required for swapping two elements in the heap"""
        # First update the indexes of the items in index map.
        self.pos_map[self.arr[i][0]], self.pos_map[self.arr[j][0]] = (
            self.pos_map[self.arr[j][0]],
            self.pos_map[self.arr[i][0]],
        )
        # Then swap the items in the list.
        self.arr[i], self.arr[j] = self.arr[j], self.arr[i]

    def _cmp(self, i: int, j: int) -> bool:
        """Compares the two items using default comparison"""
        return self.arr[i][1] < self.arr[j][1]

    def _get_valid_parent(self, i: int) -> int:
        """
        Returns index of valid parent as per desired ordering among given index and
        both it's children
        """
        left = self._left(i)
        right = self._right(i)
        valid_parent = i

        if left is not None and not self._cmp(left, valid_parent):
            valid_parent = left
        if right is not None and not self._cmp(right, valid_parent):
            valid_parent = right

        return valid_parent

    def _heapify_up(self, index: int) -> None:
        """Fixes the heap in upward direction of given index"""
        parent = self._parent(index)
        while parent is not None and not self._cmp(index, parent):
            self._swap(index, parent)
            index, parent = parent, self._parent(parent)

    def _heapify_down(self, index: int) -> None:
        """Fixes the heap in downward direction of given index"""
        valid_parent = self._get_valid_parent(index)
        while valid_parent != index:
            self._swap(index, valid_parent)
            index, valid_parent = valid_parent, self._get_valid_parent(valid_parent)

    def update_item(self, item: int, item_value: int) -> None:
        """Updates given item value in heap if present"""
        if item not in self.pos_map:
            return
        index = self.pos_map[item]
        self.arr[index] = [item, self.key(item_value)]
        # Make sure heap is right in both up and down direction.
        # Ideally only one of them will make any change.
        self._heapify_up(index)
        self._heapify_down(index)

    def delete_item(self, item: int) -> None:
        """Deletes given item from heap if present"""
        if item not in self.pos_map:
            return
        index = self.pos_map[item]
        del self.pos_map[item]
        self.arr[index] = self.arr[self.size - 1]
        self.pos_map[self.arr[self.size - 1][0]] = index
        self.size -= 1
        # Make sure heap is right in both up and down direction. Ideally only one
        # of them will make any change- so no performance loss in calling both.
        if self.size > index:
            self._heapify_up(index)
            self._heapify_down(index)

    def insert_item(self, item: int, item_value: int) -> None:
        """Inserts given item with given value in heap"""
        arr_len = len(self.arr)
        if arr_len == self.size:
            self.arr.append([item, self.key(item_value)])
        else:
            self.arr[self.size] = [item, self.key(item_value)]
        self.pos_map[item] = self.size
        self.size += 1
        self._heapify_up(self.size - 1)

    def get_top(self) -> tuple | None:
        """Returns top item tuple (Calculated value, item) from heap if present"""
        return self.arr[0] if self.size else None

    def extract_top(self) -> tuple | None:
        """
        Return top item tuple (Calculated value, item) from heap and removes it as well
        if present
        """
        top_item_tuple = self.get_top()
        if top_item_tuple:
            self.delete_item(top_item_tuple[0])
        return top_item_tuple


def test_heap() -> None:
    """
    >>> h = Heap()  # Max-heap
    >>> h.insert_item(5, 34)
    >>> h.insert_item(6, 31)
    >>> h.insert_item(7, 37)
    >>> h.get_top()
    [7, 37]
    >>> h.extract_top()
    [7, 37]
    >>> h.extract_top()
    [5, 34]
    >>> h.extract_top()
    [6, 31]
    >>> h = Heap(key=lambda x: -x)  # Min heap
    >>> h.insert_item(5, 34)
    >>> h.insert_item(6, 31)
    >>> h.insert_item(7, 37)
    >>> h.get_top()
    [6, -31]
    >>> h.extract_top()
    [6, -31]
    >>> h.extract_top()
    [5, -34]
    >>> h.extract_top()
    [7, -37]
    >>> h.insert_item(8, 45)
    >>> h.insert_item(9, 40)
    >>> h.insert_item(10, 50)
    >>> h.get_top()
    [9, -40]
    >>> h.update_item(10, 30)
    >>> h.get_top()
    [10, -30]
    >>> h.delete_item(10)
    >>> h.get_top()
    [9, -40]
    """


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/heap/max_heap.py
================================================
class BinaryHeap:
    """
    A max-heap implementation in Python
    >>> binary_heap = BinaryHeap()
    >>> binary_heap.insert(6)
    >>> binary_heap.insert(10)
    >>> binary_heap.insert(15)
    >>> binary_heap.insert(12)
    >>> binary_heap.pop()
    15
    >>> binary_heap.pop()
    12
    >>> binary_heap.get_list
    [10, 6]
    >>> len(binary_heap)
    2
    """

    def __init__(self):
        self.__heap = [0]
        self.__size = 0

    def __swap_up(self, i: int) -> None:
        """Swap the element up"""
        temporary = self.__heap[i]
        while i // 2 > 0:
            if self.__heap[i] > self.__heap[i // 2]:
                self.__heap[i] = self.__heap[i // 2]
                self.__heap[i // 2] = temporary
            i //= 2

    def insert(self, value: int) -> None:
        """Insert new element"""
        self.__heap.append(value)
        self.__size += 1
        self.__swap_up(self.__size)

    def __swap_down(self, i: int) -> None:
        """Swap the element down"""
        while self.__size >= 2 * i:
            if 2 * i + 1 > self.__size:  # noqa: SIM114
                bigger_child = 2 * i
            elif self.__heap[2 * i] > self.__heap[2 * i + 1]:
                bigger_child = 2 * i
            else:
                bigger_child = 2 * i + 1
            temporary = self.__heap[i]
            if self.__heap[i] < self.__heap[bigger_child]:
                self.__heap[i] = self.__heap[bigger_child]
                self.__heap[bigger_child] = temporary
            i = bigger_child

    def pop(self) -> int:
        """Pop the root element"""
        max_value = self.__heap[1]
        self.__heap[1] = self.__heap[self.__size]
        self.__size -= 1
        self.__heap.pop()
        self.__swap_down(1)
        return max_value

    @property
    def get_list(self):
        return self.__heap[1:]

    def __len__(self):
        """Length of the array"""
        return self.__size


if __name__ == "__main__":
    import doctest

    doctest.testmod()
    # create an instance of BinaryHeap
    binary_heap = BinaryHeap()
    binary_heap.insert(6)
    binary_heap.insert(10)
    binary_heap.insert(15)
    binary_heap.insert(12)
    # pop root(max-values because it is max heap)
    print(binary_heap.pop())  # 15
    print(binary_heap.pop())  # 12
    # get the list and size after operations
    print(binary_heap.get_list)
    print(len(binary_heap))


================================================
File: data_structures/heap/min_heap.py
================================================
# Min heap data structure
# with decrease key functionality - in O(log(n)) time


class Node:
    def __init__(self, name, val):
        self.name = name
        self.val = val

    def __str__(self):
        return f"{self.__class__.__name__}({self.name}, {self.val})"

    def __lt__(self, other):
        return self.val < other.val


class MinHeap:
    """
    >>> r = Node("R", -1)
    >>> b = Node("B", 6)
    >>> a = Node("A", 3)
    >>> x = Node("X", 1)
    >>> e = Node("E", 4)
    >>> print(b)
    Node(B, 6)
    >>> myMinHeap = MinHeap([r, b, a, x, e])
    >>> myMinHeap.decrease_key(b, -17)
    >>> print(b)
    Node(B, -17)
    >>> myMinHeap["B"]
    -17
    """

    def __init__(self, array):
        self.idx_of_element = {}
        self.heap_dict = {}
        self.heap = self.build_heap(array)

    def __getitem__(self, key):
        return self.get_value(key)

    def get_parent_idx(self, idx):
        return (idx - 1) // 2

    def get_left_child_idx(self, idx):
        return idx * 2 + 1

    def get_right_child_idx(self, idx):
        return idx * 2 + 2

    def get_value(self, key):
        return self.heap_dict[key]

    def build_heap(self, array):
        last_idx = len(array) - 1
        start_from = self.get_parent_idx(last_idx)

        for idx, i in enumerate(array):
            self.idx_of_element[i] = idx
            self.heap_dict[i.name] = i.val

        for i in range(start_from, -1, -1):
            self.sift_down(i, array)
        return array

    # this is min-heapify method
    def sift_down(self, idx, array):
        while True:
            left = self.get_left_child_idx(idx)
            right = self.get_right_child_idx(idx)

            smallest = idx
            if left < len(array) and array[left] < array[idx]:
                smallest = left
            if right < len(array) and array[right] < array[smallest]:
                smallest = right

            if smallest != idx:
                array[idx], array[smallest] = array[smallest], array[idx]
                (
                    self.idx_of_element[array[idx]],
                    self.idx_of_element[array[smallest]],
                ) = (
                    self.idx_of_element[array[smallest]],
                    self.idx_of_element[array[idx]],
                )
                idx = smallest
            else:
                break

    def sift_up(self, idx):
        p = self.get_parent_idx(idx)
        while p >= 0 and self.heap[p] > self.heap[idx]:
            self.heap[p], self.heap[idx] = self.heap[idx], self.heap[p]
            self.idx_of_element[self.heap[p]], self.idx_of_element[self.heap[idx]] = (
                self.idx_of_element[self.heap[idx]],
                self.idx_of_element[self.heap[p]],
            )
            idx = p
            p = self.get_parent_idx(idx)

    def peek(self):
        return self.heap[0]

    def remove(self):
        self.heap[0], self.heap[-1] = self.heap[-1], self.heap[0]
        self.idx_of_element[self.heap[0]], self.idx_of_element[self.heap[-1]] = (
            self.idx_of_element[self.heap[-1]],
            self.idx_of_element[self.heap[0]],
        )

        x = self.heap.pop()
        del self.idx_of_element[x]
        self.sift_down(0, self.heap)
        return x

    def insert(self, node):
        self.heap.append(node)
        self.idx_of_element[node] = len(self.heap) - 1
        self.heap_dict[node.name] = node.val
        self.sift_up(len(self.heap) - 1)

    def is_empty(self):
        return len(self.heap) == 0

    def decrease_key(self, node, new_value):
        assert self.heap[self.idx_of_element[node]].val > new_value, (
            "newValue must be less that current value"
        )
        node.val = new_value
        self.heap_dict[node.name] = new_value
        self.sift_up(self.idx_of_element[node])


# USAGE

r = Node("R", -1)
b = Node("B", 6)
a = Node("A", 3)
x = Node("X", 1)
e = Node("E", 4)

# Use one of these two ways to generate Min-Heap

# Generating Min-Heap from array
my_min_heap = MinHeap([r, b, a, x, e])

# Generating Min-Heap by Insert method
# myMinHeap.insert(a)
# myMinHeap.insert(b)
# myMinHeap.insert(x)
# myMinHeap.insert(r)
# myMinHeap.insert(e)

# Before
print("Min Heap - before decrease key")
for i in my_min_heap.heap:
    print(i)

print("Min Heap - After decrease key of node [B -> -17]")
my_min_heap.decrease_key(b, -17)

# After
for i in my_min_heap.heap:
    print(i)

if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/heap/randomized_heap.py
================================================
#!/usr/bin/env python3

from __future__ import annotations

import random
from collections.abc import Iterable
from typing import Any, Generic, TypeVar

T = TypeVar("T", bound=bool)


class RandomizedHeapNode(Generic[T]):
    """
    One node of the randomized heap. Contains the value and references to
    two children.
    """

    def __init__(self, value: T) -> None:
        self._value: T = value
        self.left: RandomizedHeapNode[T] | None = None
        self.right: RandomizedHeapNode[T] | None = None

    @property
    def value(self) -> T:
        """
        Return the value of the node.

        >>> rhn = RandomizedHeapNode(10)
        >>> rhn.value
        10
        >>> rhn = RandomizedHeapNode(-10)
        >>> rhn.value
        -10
        """
        return self._value

    @staticmethod
    def merge(
        root1: RandomizedHeapNode[T] | None, root2: RandomizedHeapNode[T] | None
    ) -> RandomizedHeapNode[T] | None:
        """
        Merge 2 nodes together.

        >>> rhn1 = RandomizedHeapNode(10)
        >>> rhn2 = RandomizedHeapNode(20)
        >>> RandomizedHeapNode.merge(rhn1, rhn2).value
        10

        >>> rhn1 = RandomizedHeapNode(20)
        >>> rhn2 = RandomizedHeapNode(10)
        >>> RandomizedHeapNode.merge(rhn1, rhn2).value
        10

        >>> rhn1 = RandomizedHeapNode(5)
        >>> rhn2 = RandomizedHeapNode(0)
        >>> RandomizedHeapNode.merge(rhn1, rhn2).value
        0
        """
        if not root1:
            return root2

        if not root2:
            return root1

        if root1.value > root2.value:
            root1, root2 = root2, root1

        if random.choice([True, False]):
            root1.left, root1.right = root1.right, root1.left

        root1.left = RandomizedHeapNode.merge(root1.left, root2)

        return root1


class RandomizedHeap(Generic[T]):
    """
    A data structure that allows inserting a new value and to pop the smallest
    values. Both operations take O(logN) time where N is the size of the
    structure.
    Wiki: https://en.wikipedia.org/wiki/Randomized_meldable_heap

    >>> RandomizedHeap([2, 3, 1, 5, 1, 7]).to_sorted_list()
    [1, 1, 2, 3, 5, 7]

    >>> rh = RandomizedHeap()
    >>> rh.pop()
    Traceback (most recent call last):
        ...
    IndexError: Can't get top element for the empty heap.

    >>> rh.insert(1)
    >>> rh.insert(-1)
    >>> rh.insert(0)
    >>> rh.to_sorted_list()
    [-1, 0, 1]
    """

    def __init__(self, data: Iterable[T] | None = ()) -> None:
        """
        >>> rh = RandomizedHeap([3, 1, 3, 7])
        >>> rh.to_sorted_list()
        [1, 3, 3, 7]
        """
        self._root: RandomizedHeapNode[T] | None = None

        if data:
            for item in data:
                self.insert(item)

    def insert(self, value: T) -> None:
        """
        Insert the value into the heap.

        >>> rh = RandomizedHeap()
        >>> rh.insert(3)
        >>> rh.insert(1)
        >>> rh.insert(3)
        >>> rh.insert(7)
        >>> rh.to_sorted_list()
        [1, 3, 3, 7]
        """
        self._root = RandomizedHeapNode.merge(self._root, RandomizedHeapNode(value))

    def pop(self) -> T | None:
        """
        Pop the smallest value from the heap and return it.

        >>> rh = RandomizedHeap([3, 1, 3, 7])
        >>> rh.pop()
        1
        >>> rh.pop()
        3
        >>> rh.pop()
        3
        >>> rh.pop()
        7
        >>> rh.pop()
        Traceback (most recent call last):
            ...
        IndexError: Can't get top element for the empty heap.
        """

        result = self.top()

        if self._root is None:
            return None

        self._root = RandomizedHeapNode.merge(self._root.left, self._root.right)

        return result

    def top(self) -> T:
        """
        Return the smallest value from the heap.

        >>> rh = RandomizedHeap()
        >>> rh.insert(3)
        >>> rh.top()
        3
        >>> rh.insert(1)
        >>> rh.top()
        1
        >>> rh.insert(3)
        >>> rh.top()
        1
        >>> rh.insert(7)
        >>> rh.top()
        1
        """
        if not self._root:
            raise IndexError("Can't get top element for the empty heap.")
        return self._root.value

    def clear(self) -> None:
        """
        Clear the heap.

        >>> rh = RandomizedHeap([3, 1, 3, 7])
        >>> rh.clear()
        >>> rh.pop()
        Traceback (most recent call last):
            ...
        IndexError: Can't get top element for the empty heap.
        """
        self._root = None

    def to_sorted_list(self) -> list[Any]:
        """
        Returns sorted list containing all the values in the heap.

        >>> rh = RandomizedHeap([3, 1, 3, 7])
        >>> rh.to_sorted_list()
        [1, 3, 3, 7]
        """
        result = []
        while self:
            result.append(self.pop())

        return result

    def __bool__(self) -> bool:
        """
        Check if the heap is not empty.

        >>> rh = RandomizedHeap()
        >>> bool(rh)
        False
        >>> rh.insert(1)
        >>> bool(rh)
        True
        >>> rh.clear()
        >>> bool(rh)
        False
        """
        return self._root is not None


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/heap/skew_heap.py
================================================
#!/usr/bin/env python3

from __future__ import annotations

from collections.abc import Iterable, Iterator
from typing import Any, Generic, TypeVar

T = TypeVar("T", bound=bool)


class SkewNode(Generic[T]):
    """
    One node of the skew heap. Contains the value and references to
    two children.
    """

    def __init__(self, value: T) -> None:
        self._value: T = value
        self.left: SkewNode[T] | None = None
        self.right: SkewNode[T] | None = None

    @property
    def value(self) -> T:
        """
        Return the value of the node.

        >>> SkewNode(0).value
        0
        >>> SkewNode(3.14159).value
        3.14159
        >>> SkewNode("hello").value
        'hello'
        >>> SkewNode(None).value

        >>> SkewNode(True).value
        True
        >>> SkewNode([]).value
        []
        >>> SkewNode({}).value
        {}
        >>> SkewNode(set()).value
        set()
        >>> SkewNode(0.0).value
        0.0
        >>> SkewNode(-1e-10).value
        -1e-10
        >>> SkewNode(10).value
        10
        >>> SkewNode(-10.5).value
        -10.5
        >>> SkewNode().value
        Traceback (most recent call last):
        ...
        TypeError: SkewNode.__init__() missing 1 required positional argument: 'value'
        """
        return self._value

    @staticmethod
    def merge(
        root1: SkewNode[T] | None, root2: SkewNode[T] | None
    ) -> SkewNode[T] | None:
        """
        Merge 2 nodes together.
        >>> SkewNode.merge(SkewNode(10),SkewNode(-10.5)).value
        -10.5
        >>> SkewNode.merge(SkewNode(10),SkewNode(10.5)).value
        10
        >>> SkewNode.merge(SkewNode(10),SkewNode(10)).value
        10
        >>> SkewNode.merge(SkewNode(-100),SkewNode(-10.5)).value
        -100
        """
        if not root1:
            return root2

        if not root2:
            return root1

        if root1.value > root2.value:
            root1, root2 = root2, root1

        result = root1
        temp = root1.right
        result.right = root1.left
        result.left = SkewNode.merge(temp, root2)

        return result


class SkewHeap(Generic[T]):
    """
    A data structure that allows inserting a new value and to pop the smallest
    values. Both operations take O(logN) time where N is the size of the
    structure.
    Wiki: https://en.wikipedia.org/wiki/Skew_heap
    Visualization: https://www.cs.usfca.edu/~galles/visualization/SkewHeap.html

    >>> list(SkewHeap([2, 3, 1, 5, 1, 7]))
    [1, 1, 2, 3, 5, 7]

    >>> sh = SkewHeap()
    >>> sh.pop()
    Traceback (most recent call last):
        ...
    IndexError: Can't get top element for the empty heap.

    >>> sh.insert(1)
    >>> sh.insert(-1)
    >>> sh.insert(0)
    >>> list(sh)
    [-1, 0, 1]
    """

    def __init__(self, data: Iterable[T] | None = ()) -> None:
        """
        >>> sh = SkewHeap([3, 1, 3, 7])
        >>> list(sh)
        [1, 3, 3, 7]
        """
        self._root: SkewNode[T] | None = None
        if data:
            for item in data:
                self.insert(item)

    def __bool__(self) -> bool:
        """
        Check if the heap is not empty.

        >>> sh = SkewHeap()
        >>> bool(sh)
        False
        >>> sh.insert(1)
        >>> bool(sh)
        True
        >>> sh.clear()
        >>> bool(sh)
        False
        """
        return self._root is not None

    def __iter__(self) -> Iterator[T]:
        """
        Returns sorted list containing all the values in the heap.

        >>> sh = SkewHeap([3, 1, 3, 7])
        >>> list(sh)
        [1, 3, 3, 7]
        """
        result: list[Any] = []
        while self:
            result.append(self.pop())

        # Pushing items back to the heap not to clear it.
        for item in result:
            self.insert(item)

        return iter(result)

    def insert(self, value: T) -> None:
        """
        Insert the value into the heap.

        >>> sh = SkewHeap()
        >>> sh.insert(3)
        >>> sh.insert(1)
        >>> sh.insert(3)
        >>> sh.insert(7)
        >>> list(sh)
        [1, 3, 3, 7]
        """
        self._root = SkewNode.merge(self._root, SkewNode(value))

    def pop(self) -> T | None:
        """
        Pop the smallest value from the heap and return it.

        >>> sh = SkewHeap([3, 1, 3, 7])
        >>> sh.pop()
        1
        >>> sh.pop()
        3
        >>> sh.pop()
        3
        >>> sh.pop()
        7
        >>> sh.pop()
        Traceback (most recent call last):
            ...
        IndexError: Can't get top element for the empty heap.
        """
        result = self.top()
        self._root = (
            SkewNode.merge(self._root.left, self._root.right) if self._root else None
        )

        return result

    def top(self) -> T:
        """
        Return the smallest value from the heap.

        >>> sh = SkewHeap()
        >>> sh.insert(3)
        >>> sh.top()
        3
        >>> sh.insert(1)
        >>> sh.top()
        1
        >>> sh.insert(3)
        >>> sh.top()
        1
        >>> sh.insert(7)
        >>> sh.top()
        1
        """
        if not self._root:
            raise IndexError("Can't get top element for the empty heap.")
        return self._root.value

    def clear(self) -> None:
        """
        Clear the heap.

        >>> sh = SkewHeap([3, 1, 3, 7])
        >>> sh.clear()
        >>> sh.pop()
        Traceback (most recent call last):
            ...
        IndexError: Can't get top element for the empty heap.
        """
        self._root = None


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/kd_tree/build_kdtree.py
================================================
#  Created by: Ramy-Badr-Ahmed (https://github.com/Ramy-Badr-Ahmed)
#  in Pull Request: #11532
#  https://github.com/TheAlgorithms/Python/pull/11532
#
#  Please mention me (@Ramy-Badr-Ahmed) in any issue or pull request
#  addressing bugs/corrections to this file.
#  Thank you!

from data_structures.kd_tree.kd_node import KDNode


def build_kdtree(points: list[list[float]], depth: int = 0) -> KDNode | None:
    """
    Builds a KD-Tree from a list of points.

    Args:
        points: The list of points to build the KD-Tree from.
        depth: The current depth in the tree
                     (used to determine axis for splitting).

    Returns:
        The root node of the KD-Tree,
                       or None if no points are provided.
    """
    if not points:
        return None

    k = len(points[0])  # Dimensionality of the points
    axis = depth % k

    # Sort point list and choose median as pivot element
    points.sort(key=lambda point: point[axis])
    median_idx = len(points) // 2

    # Create node and construct subtrees
    left_points = points[:median_idx]
    right_points = points[median_idx + 1 :]

    return KDNode(
        point=points[median_idx],
        left=build_kdtree(left_points, depth + 1),
        right=build_kdtree(right_points, depth + 1),
    )


================================================
File: data_structures/kd_tree/kd_node.py
================================================
#  Created by: Ramy-Badr-Ahmed (https://github.com/Ramy-Badr-Ahmed)
#  in Pull Request: #11532
#  https://github.com/TheAlgorithms/Python/pull/11532
#
#  Please mention me (@Ramy-Badr-Ahmed) in any issue or pull request
#  addressing bugs/corrections to this file.
#  Thank you!

from __future__ import annotations


class KDNode:
    """
    Represents a node in a KD-Tree.

    Attributes:
        point: The point stored in this node.
        left: The left child node.
        right: The right child node.
    """

    def __init__(
        self,
        point: list[float],
        left: KDNode | None = None,
        right: KDNode | None = None,
    ) -> None:
        """
        Initializes a KDNode with the given point and child nodes.

        Args:
            point (list[float]): The point stored in this node.
            left (Optional[KDNode]): The left child node.
            right (Optional[KDNode]): The right child node.
        """
        self.point = point
        self.left = left
        self.right = right


================================================
File: data_structures/kd_tree/nearest_neighbour_search.py
================================================
#  Created by: Ramy-Badr-Ahmed (https://github.com/Ramy-Badr-Ahmed)
#  in Pull Request: #11532
#  https://github.com/TheAlgorithms/Python/pull/11532
#
#  Please mention me (@Ramy-Badr-Ahmed) in any issue or pull request
#  addressing bugs/corrections to this file.
#  Thank you!

from data_structures.kd_tree.kd_node import KDNode


def nearest_neighbour_search(
    root: KDNode | None, query_point: list[float]
) -> tuple[list[float] | None, float, int]:
    """
    Performs a nearest neighbor search in a KD-Tree for a given query point.

    Args:
        root (KDNode | None): The root node of the KD-Tree.
        query_point (list[float]): The point for which the nearest neighbor
                                    is being searched.

    Returns:
        tuple[list[float] | None, float, int]:
            - The nearest point found in the KD-Tree to the query point,
              or None if no point is found.
            - The squared distance to the nearest point.
            - The number of nodes visited during the search.
    """
    nearest_point: list[float] | None = None
    nearest_dist: float = float("inf")
    nodes_visited: int = 0

    def search(node: KDNode | None, depth: int = 0) -> None:
        """
        Recursively searches for the nearest neighbor in the KD-Tree.

        Args:
            node: The current node in the KD-Tree.
            depth: The current depth in the KD-Tree.
        """
        nonlocal nearest_point, nearest_dist, nodes_visited
        if node is None:
            return

        nodes_visited += 1

        # Calculate the current distance (squared distance)
        current_point = node.point
        current_dist = sum(
            (query_coord - point_coord) ** 2
            for query_coord, point_coord in zip(query_point, current_point)
        )

        # Update nearest point if the current node is closer
        if nearest_point is None or current_dist < nearest_dist:
            nearest_point = current_point
            nearest_dist = current_dist

        # Determine which subtree to search first (based on axis and query point)
        k = len(query_point)  # Dimensionality of points
        axis = depth % k

        if query_point[axis] <= current_point[axis]:
            nearer_subtree = node.left
            further_subtree = node.right
        else:
            nearer_subtree = node.right
            further_subtree = node.left

        # Search the nearer subtree first
        search(nearer_subtree, depth + 1)

        # If the further subtree has a closer point
        if (query_point[axis] - current_point[axis]) ** 2 < nearest_dist:
            search(further_subtree, depth + 1)

    search(root, 0)
    return nearest_point, nearest_dist, nodes_visited


================================================
File: data_structures/kd_tree/example/example_usage.py
================================================
#  Created by: Ramy-Badr-Ahmed (https://github.com/Ramy-Badr-Ahmed)
#  in Pull Request: #11532
#  https://github.com/TheAlgorithms/Python/pull/11532
#
#  Please mention me (@Ramy-Badr-Ahmed) in any issue or pull request
#  addressing bugs/corrections to this file.
#  Thank you!

import numpy as np

from data_structures.kd_tree.build_kdtree import build_kdtree
from data_structures.kd_tree.example.hypercube_points import hypercube_points
from data_structures.kd_tree.nearest_neighbour_search import nearest_neighbour_search


def main() -> None:
    """
    Demonstrates the use of KD-Tree by building it from random points
    in a 10-dimensional hypercube and performing a nearest neighbor search.
    """
    num_points: int = 5000
    cube_size: float = 10.0  # Size of the hypercube (edge length)
    num_dimensions: int = 10

    # Generate random points within the hypercube
    points: np.ndarray = hypercube_points(num_points, cube_size, num_dimensions)
    hypercube_kdtree = build_kdtree(points.tolist())

    # Generate a random query point within the same space
    rng = np.random.default_rng()
    query_point: list[float] = rng.random(num_dimensions).tolist()

    # Perform nearest neighbor search
    nearest_point, nearest_dist, nodes_visited = nearest_neighbour_search(
        hypercube_kdtree, query_point
    )

    # Print the results
    print(f"Query point: {query_point}")
    print(f"Nearest point: {nearest_point}")
    print(f"Distance: {nearest_dist:.4f}")
    print(f"Nodes visited: {nodes_visited}")


if __name__ == "__main__":
    main()


================================================
File: data_structures/kd_tree/example/hypercube_points.py
================================================
#  Created by: Ramy-Badr-Ahmed (https://github.com/Ramy-Badr-Ahmed)
#  in Pull Request: #11532
#  https://github.com/TheAlgorithms/Python/pull/11532
#
#  Please mention me (@Ramy-Badr-Ahmed) in any issue or pull request
#  addressing bugs/corrections to this file.
#  Thank you!

import numpy as np


def hypercube_points(
    num_points: int, hypercube_size: float, num_dimensions: int
) -> np.ndarray:
    """
    Generates random points uniformly distributed within an n-dimensional hypercube.

    Args:
        num_points: Number of points to generate.
        hypercube_size: Size of the hypercube.
        num_dimensions: Number of dimensions of the hypercube.

    Returns:
        An array of shape (num_points, num_dimensions)
                    with generated points.
    """
    rng = np.random.default_rng()
    shape = (num_points, num_dimensions)
    return hypercube_size * rng.random(shape)


================================================
File: data_structures/kd_tree/tests/test_kdtree.py
================================================
#  Created by: Ramy-Badr-Ahmed (https://github.com/Ramy-Badr-Ahmed)
#  in Pull Request: #11532
#  https://github.com/TheAlgorithms/Python/pull/11532
#
#  Please mention me (@Ramy-Badr-Ahmed) in any issue or pull request
#  addressing bugs/corrections to this file.
#  Thank you!

import numpy as np
import pytest

from data_structures.kd_tree.build_kdtree import build_kdtree
from data_structures.kd_tree.example.hypercube_points import hypercube_points
from data_structures.kd_tree.kd_node import KDNode
from data_structures.kd_tree.nearest_neighbour_search import nearest_neighbour_search


@pytest.mark.parametrize(
    ("num_points", "cube_size", "num_dimensions", "depth", "expected_result"),
    [
        (0, 10.0, 2, 0, None),  # Empty points list
        (10, 10.0, 2, 2, KDNode),  # Depth = 2, 2D points
        (10, 10.0, 3, -2, KDNode),  # Depth = -2, 3D points
    ],
)
def test_build_kdtree(num_points, cube_size, num_dimensions, depth, expected_result):
    """
    Test that KD-Tree is built correctly.

    Cases:
        - Empty points list.
        - Positive depth value.
        - Negative depth value.
    """
    points = (
        hypercube_points(num_points, cube_size, num_dimensions).tolist()
        if num_points > 0
        else []
    )

    kdtree = build_kdtree(points, depth=depth)

    if expected_result is None:
        # Empty points list case
        assert kdtree is None, f"Expected None for empty points list, got {kdtree}"
    else:
        # Check if root node is not None
        assert kdtree is not None, "Expected a KDNode, got None"

        # Check if root has correct dimensions
        assert len(kdtree.point) == num_dimensions, (
            f"Expected point dimension {num_dimensions}, got {len(kdtree.point)}"
        )

        # Check that the tree is balanced to some extent (simplistic check)
        assert isinstance(kdtree, KDNode), (
            f"Expected KDNode instance, got {type(kdtree)}"
        )


def test_nearest_neighbour_search():
    """
    Test the nearest neighbor search function.
    """
    num_points = 10
    cube_size = 10.0
    num_dimensions = 2
    points = hypercube_points(num_points, cube_size, num_dimensions)
    kdtree = build_kdtree(points.tolist())

    rng = np.random.default_rng()
    query_point = rng.random(num_dimensions).tolist()

    nearest_point, nearest_dist, nodes_visited = nearest_neighbour_search(
        kdtree, query_point
    )

    # Check that nearest point is not None
    assert nearest_point is not None

    # Check that distance is a non-negative number
    assert nearest_dist >= 0

    # Check that nodes visited is a non-negative integer
    assert nodes_visited >= 0


def test_edge_cases():
    """
    Test edge cases such as an empty KD-Tree.
    """
    empty_kdtree = build_kdtree([])
    query_point = [0.0] * 2  # Using a default 2D query point

    nearest_point, nearest_dist, nodes_visited = nearest_neighbour_search(
        empty_kdtree, query_point
    )

    # With an empty KD-Tree, nearest_point should be None
    assert nearest_point is None
    assert nearest_dist == float("inf")
    assert nodes_visited == 0


if __name__ == "__main__":
    import pytest

    pytest.main()


================================================
File: data_structures/linked_list/__init__.py
================================================
"""
Linked Lists consists of Nodes.
Nodes contain data and also may link to other nodes:
    - Head Node: First node, the address of the
                 head node gives us access of the complete list
    - Last node: points to null
"""

from __future__ import annotations

from typing import Any


class Node:
    def __init__(self, item: Any, next: Any) -> None:  # noqa: A002
        self.item = item
        self.next = next


class LinkedList:
    def __init__(self) -> None:
        self.head: Node | None = None
        self.size = 0

    def add(self, item: Any, position: int = 0) -> None:
        """
        Add an item to the LinkedList at the specified position.
        Default position is 0 (the head).

        Args:
            item (Any): The item to add to the LinkedList.
            position (int, optional): The position at which to add the item.
                Defaults to 0.

        Raises:
            ValueError: If the position is negative or out of bounds.

        >>> linked_list = LinkedList()
        >>> linked_list.add(1)
        >>> linked_list.add(2)
        >>> linked_list.add(3)
        >>> linked_list.add(4, 2)
        >>> print(linked_list)
        3 --> 2 --> 4 --> 1

        # Test adding to a negative position
        >>> linked_list.add(5, -3)
        Traceback (most recent call last):
            ...
        ValueError: Position must be non-negative

        # Test adding to an out-of-bounds position
        >>> linked_list.add(5,7)
        Traceback (most recent call last):
            ...
        ValueError: Out of bounds
        >>> linked_list.add(5, 4)
        >>> print(linked_list)
        3 --> 2 --> 4 --> 1 --> 5
        """
        if position < 0:
            raise ValueError("Position must be non-negative")

        if position == 0 or self.head is None:
            new_node = Node(item, self.head)
            self.head = new_node
        else:
            current = self.head
            for _ in range(position - 1):
                current = current.next
                if current is None:
                    raise ValueError("Out of bounds")
            new_node = Node(item, current.next)
            current.next = new_node
        self.size += 1

    def remove(self) -> Any:
        # Switched 'self.is_empty()' to 'self.head is None'
        # because mypy was considering the possibility that 'self.head'
        # can be None in below else part and giving error
        if self.head is None:
            return None
        else:
            item = self.head.item
            self.head = self.head.next
            self.size -= 1
            return item

    def is_empty(self) -> bool:
        return self.head is None

    def __str__(self) -> str:
        """
        >>> linked_list = LinkedList()
        >>> linked_list.add(23)
        >>> linked_list.add(14)
        >>> linked_list.add(9)
        >>> print(linked_list)
        9 --> 14 --> 23
        """
        if self.is_empty():
            return ""
        else:
            iterate = self.head
            item_str = ""
            item_list: list[str] = []
            while iterate:
                item_list.append(str(iterate.item))
                iterate = iterate.next

            item_str = " --> ".join(item_list)

            return item_str

    def __len__(self) -> int:
        """
        >>> linked_list = LinkedList()
        >>> len(linked_list)
        0
        >>> linked_list.add("a")
        >>> len(linked_list)
        1
        >>> linked_list.add("b")
        >>> len(linked_list)
        2
        >>> _ = linked_list.remove()
        >>> len(linked_list)
        1
        >>> _ = linked_list.remove()
        >>> len(linked_list)
        0
        """
        return self.size


================================================
File: data_structures/linked_list/circular_linked_list.py
================================================
from __future__ import annotations

from collections.abc import Iterator
from dataclasses import dataclass
from typing import Any


@dataclass
class Node:
    data: Any
    next_node: Node | None = None


@dataclass
class CircularLinkedList:
    head: Node | None = None  # Reference to the head (first node)
    tail: Node | None = None  # Reference to the tail (last node)

    def __iter__(self) -> Iterator[Any]:
        """
        Iterate through all nodes in the Circular Linked List yielding their data.
        Yields:
            The data of each node in the linked list.
        """
        node = self.head
        while node:
            yield node.data
            node = node.next_node
            if node == self.head:
                break

    def __len__(self) -> int:
        """
        Get the length (number of nodes) in the Circular Linked List.
        """
        return sum(1 for _ in self)

    def __repr__(self) -> str:
        """
        Generate a string representation of the Circular Linked List.
        Returns:
            A string of the format "1->2->....->N".
        """
        return "->".join(str(item) for item in iter(self))

    def insert_tail(self, data: Any) -> None:
        """
        Insert a node with the given data at the end of the Circular Linked List.
        """
        self.insert_nth(len(self), data)

    def insert_head(self, data: Any) -> None:
        """
        Insert a node with the given data at the beginning of the Circular Linked List.
        """
        self.insert_nth(0, data)

    def insert_nth(self, index: int, data: Any) -> None:
        """
        Insert the data of the node at the nth pos in the Circular Linked List.
        Args:
            index: The index at which the data should be inserted.
            data: The data to be inserted.

        Raises:
            IndexError: If the index is out of range.
        """
        if index < 0 or index > len(self):
            raise IndexError("list index out of range.")
        new_node: Node = Node(data)
        if self.head is None:
            new_node.next_node = new_node  # First node points to itself
            self.tail = self.head = new_node
        elif index == 0:  # Insert at the head
            new_node.next_node = self.head
            assert self.tail is not None  # List is not empty, tail exists
            self.head = self.tail.next_node = new_node
        else:
            temp: Node | None = self.head
            for _ in range(index - 1):
                assert temp is not None
                temp = temp.next_node
            assert temp is not None
            new_node.next_node = temp.next_node
            temp.next_node = new_node
            if index == len(self) - 1:  # Insert at the tail
                self.tail = new_node

    def delete_front(self) -> Any:
        """
        Delete and return the data of the node at the front of the Circular Linked List.
        Raises:
            IndexError: If the list is empty.
        """
        return self.delete_nth(0)

    def delete_tail(self) -> Any:
        """
        Delete and return the data of the node at the end of the Circular Linked List.
        Returns:
            Any: The data of the deleted node.
        Raises:
            IndexError: If the index is out of range.
        """
        return self.delete_nth(len(self) - 1)

    def delete_nth(self, index: int = 0) -> Any:
        """
        Delete and return the data of the node at the nth pos in Circular Linked List.
        Args:
            index (int): The index of the node to be deleted. Defaults to 0.
        Returns:
            Any: The data of the deleted node.
        Raises:
            IndexError: If the index is out of range.
        """
        if not 0 <= index < len(self):
            raise IndexError("list index out of range.")

        assert self.head is not None
        assert self.tail is not None
        delete_node: Node = self.head
        if self.head == self.tail:  # Just one node
            self.head = self.tail = None
        elif index == 0:  # Delete head node
            assert self.tail.next_node is not None
            self.tail.next_node = self.tail.next_node.next_node
            self.head = self.head.next_node
        else:
            temp: Node | None = self.head
            for _ in range(index - 1):
                assert temp is not None
                temp = temp.next_node
            assert temp is not None
            assert temp.next_node is not None
            delete_node = temp.next_node
            temp.next_node = temp.next_node.next_node
            if index == len(self) - 1:  # Delete at tail
                self.tail = temp
        return delete_node.data

    def is_empty(self) -> bool:
        """
        Check if the Circular Linked List is empty.
        Returns:
            bool: True if the list is empty, False otherwise.
        """
        return len(self) == 0


def test_circular_linked_list() -> None:
    """
    Test cases for the CircularLinkedList class.
    >>> test_circular_linked_list()
    """
    circular_linked_list = CircularLinkedList()
    assert len(circular_linked_list) == 0
    assert circular_linked_list.is_empty() is True
    assert str(circular_linked_list) == ""

    try:
        circular_linked_list.delete_front()
        raise AssertionError  # This should not happen
    except IndexError:
        assert True  # This should happen

    try:
        circular_linked_list.delete_tail()
        raise AssertionError  # This should not happen
    except IndexError:
        assert True  # This should happen

    try:
        circular_linked_list.delete_nth(-1)
        raise AssertionError
    except IndexError:
        assert True

    try:
        circular_linked_list.delete_nth(0)
        raise AssertionError
    except IndexError:
        assert True

    assert circular_linked_list.is_empty() is True
    for i in range(5):
        assert len(circular_linked_list) == i
        circular_linked_list.insert_nth(i, i + 1)
    assert str(circular_linked_list) == "->".join(str(i) for i in range(1, 6))

    circular_linked_list.insert_tail(6)
    assert str(circular_linked_list) == "->".join(str(i) for i in range(1, 7))
    circular_linked_list.insert_head(0)
    assert str(circular_linked_list) == "->".join(str(i) for i in range(7))

    assert circular_linked_list.delete_front() == 0
    assert circular_linked_list.delete_tail() == 6
    assert str(circular_linked_list) == "->".join(str(i) for i in range(1, 6))
    assert circular_linked_list.delete_nth(2) == 3

    circular_linked_list.insert_nth(2, 3)
    assert str(circular_linked_list) == "->".join(str(i) for i in range(1, 6))

    assert circular_linked_list.is_empty() is False


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/linked_list/deque_doubly.py
================================================
"""
Implementing Deque using DoublyLinkedList ...
Operations:
    1. insertion in the front -> O(1)
    2. insertion in the end -> O(1)
    3. remove from the front -> O(1)
    4. remove from the end -> O(1)
"""


class _DoublyLinkedBase:
    """A Private class (to be inherited)"""

    class _Node:
        __slots__ = "_data", "_next", "_prev"

        def __init__(self, link_p, element, link_n):
            self._prev = link_p
            self._data = element
            self._next = link_n

        def has_next_and_prev(self):
            return (
                f" Prev -> {self._prev is not None}, Next -> {self._next is not None}"
            )

    def __init__(self):
        self._header = self._Node(None, None, None)
        self._trailer = self._Node(None, None, None)
        self._header._next = self._trailer
        self._trailer._prev = self._header
        self._size = 0

    def __len__(self):
        return self._size

    def is_empty(self):
        return self.__len__() == 0

    def _insert(self, predecessor, e, successor):
        # Create new_node by setting it's prev.link -> header
        # setting it's next.link -> trailer
        new_node = self._Node(predecessor, e, successor)
        predecessor._next = new_node
        successor._prev = new_node
        self._size += 1
        return self

    def _delete(self, node):
        predecessor = node._prev
        successor = node._next

        predecessor._next = successor
        successor._prev = predecessor
        self._size -= 1
        temp = node._data
        node._prev = node._next = node._data = None
        del node
        return temp


class LinkedDeque(_DoublyLinkedBase):
    def first(self):
        """return first element
        >>> d = LinkedDeque()
        >>> d.add_first('A').first()
        'A'
        >>> d.add_first('B').first()
        'B'
        """
        if self.is_empty():
            raise Exception("List is empty")
        return self._header._next._data

    def last(self):
        """return last element
        >>> d = LinkedDeque()
        >>> d.add_last('A').last()
        'A'
        >>> d.add_last('B').last()
        'B'
        """
        if self.is_empty():
            raise Exception("List is empty")
        return self._trailer._prev._data

    # DEque Insert Operations (At the front, At the end)

    def add_first(self, element):
        """insertion in the front
        >>> LinkedDeque().add_first('AV').first()
        'AV'
        """
        return self._insert(self._header, element, self._header._next)

    def add_last(self, element):
        """insertion in the end
        >>> LinkedDeque().add_last('B').last()
        'B'
        """
        return self._insert(self._trailer._prev, element, self._trailer)

    # DEqueu Remove Operations (At the front, At the end)

    def remove_first(self):
        """removal from the front
        >>> d = LinkedDeque()
        >>> d.is_empty()
        True
        >>> d.remove_first()
        Traceback (most recent call last):
           ...
        IndexError: remove_first from empty list
        >>> d.add_first('A') # doctest: +ELLIPSIS
        <data_structures.linked_list.deque_doubly.LinkedDeque object at ...
        >>> d.remove_first()
        'A'
        >>> d.is_empty()
        True
        """
        if self.is_empty():
            raise IndexError("remove_first from empty list")
        return self._delete(self._header._next)

    def remove_last(self):
        """removal in the end
        >>> d = LinkedDeque()
        >>> d.is_empty()
        True
        >>> d.remove_last()
        Traceback (most recent call last):
           ...
        IndexError: remove_first from empty list
        >>> d.add_first('A') # doctest: +ELLIPSIS
        <data_structures.linked_list.deque_doubly.LinkedDeque object at ...
        >>> d.remove_last()
        'A'
        >>> d.is_empty()
        True
        """
        if self.is_empty():
            raise IndexError("remove_first from empty list")
        return self._delete(self._trailer._prev)


================================================
File: data_structures/linked_list/doubly_linked_list.py
================================================
"""
https://en.wikipedia.org/wiki/Doubly_linked_list
"""


class Node:
    def __init__(self, data):
        self.data = data
        self.previous = None
        self.next = None

    def __str__(self):
        return f"{self.data}"


class DoublyLinkedList:
    def __init__(self):
        self.head = None
        self.tail = None

    def __iter__(self):
        """
        >>> linked_list = DoublyLinkedList()
        >>> linked_list.insert_at_head('b')
        >>> linked_list.insert_at_head('a')
        >>> linked_list.insert_at_tail('c')
        >>> tuple(linked_list)
        ('a', 'b', 'c')
        """
        node = self.head
        while node:
            yield node.data
            node = node.next

    def __str__(self):
        """
        >>> linked_list = DoublyLinkedList()
        >>> linked_list.insert_at_tail('a')
        >>> linked_list.insert_at_tail('b')
        >>> linked_list.insert_at_tail('c')
        >>> str(linked_list)
        'a->b->c'
        """
        return "->".join([str(item) for item in self])

    def __len__(self):
        """
        >>> linked_list = DoublyLinkedList()
        >>> for i in range(0, 5):
        ...     linked_list.insert_at_nth(i, i + 1)
        >>> len(linked_list) == 5
        True
        """
        return sum(1 for _ in self)

    def insert_at_head(self, data):
        self.insert_at_nth(0, data)

    def insert_at_tail(self, data):
        self.insert_at_nth(len(self), data)

    def insert_at_nth(self, index: int, data):
        """
        >>> linked_list = DoublyLinkedList()
        >>> linked_list.insert_at_nth(-1, 666)
        Traceback (most recent call last):
            ....
        IndexError: list index out of range
        >>> linked_list.insert_at_nth(1, 666)
        Traceback (most recent call last):
            ....
        IndexError: list index out of range
        >>> linked_list.insert_at_nth(0, 2)
        >>> linked_list.insert_at_nth(0, 1)
        >>> linked_list.insert_at_nth(2, 4)
        >>> linked_list.insert_at_nth(2, 3)
        >>> str(linked_list)
        '1->2->3->4'
        >>> linked_list.insert_at_nth(5, 5)
        Traceback (most recent call last):
            ....
        IndexError: list index out of range
        """
        length = len(self)

        if not 0 <= index <= length:
            raise IndexError("list index out of range")
        new_node = Node(data)
        if self.head is None:
            self.head = self.tail = new_node
        elif index == 0:
            self.head.previous = new_node
            new_node.next = self.head
            self.head = new_node
        elif index == length:
            self.tail.next = new_node
            new_node.previous = self.tail
            self.tail = new_node
        else:
            temp = self.head
            for _ in range(index):
                temp = temp.next
            temp.previous.next = new_node
            new_node.previous = temp.previous
            new_node.next = temp
            temp.previous = new_node

    def delete_head(self):
        return self.delete_at_nth(0)

    def delete_tail(self):
        return self.delete_at_nth(len(self) - 1)

    def delete_at_nth(self, index: int):
        """
        >>> linked_list = DoublyLinkedList()
        >>> linked_list.delete_at_nth(0)
        Traceback (most recent call last):
            ....
        IndexError: list index out of range
        >>> for i in range(0, 5):
        ...     linked_list.insert_at_nth(i, i + 1)
        >>> linked_list.delete_at_nth(0) == 1
        True
        >>> linked_list.delete_at_nth(3) == 5
        True
        >>> linked_list.delete_at_nth(1) == 3
        True
        >>> str(linked_list)
        '2->4'
        >>> linked_list.delete_at_nth(2)
        Traceback (most recent call last):
            ....
        IndexError: list index out of range
        """
        length = len(self)

        if not 0 <= index <= length - 1:
            raise IndexError("list index out of range")
        delete_node = self.head  # default first node
        if length == 1:
            self.head = self.tail = None
        elif index == 0:
            self.head = self.head.next
            self.head.previous = None
        elif index == length - 1:
            delete_node = self.tail
            self.tail = self.tail.previous
            self.tail.next = None
        else:
            temp = self.head
            for _ in range(index):
                temp = temp.next
            delete_node = temp
            temp.next.previous = temp.previous
            temp.previous.next = temp.next
        return delete_node.data

    def delete(self, data) -> str:
        current = self.head

        while current.data != data:  # Find the position to delete
            if current.next:
                current = current.next
            else:  # We have reached the end an no value matches
                raise ValueError("No data matching given value")

        if current == self.head:
            self.delete_head()

        elif current == self.tail:
            self.delete_tail()

        else:  # Before: 1 <--> 2(current) <--> 3
            current.previous.next = current.next  # 1 --> 3
            current.next.previous = current.previous  # 1 <--> 3
        return data

    def is_empty(self):
        """
        >>> linked_list = DoublyLinkedList()
        >>> linked_list.is_empty()
        True
        >>> linked_list.insert_at_tail(1)
        >>> linked_list.is_empty()
        False
        """
        return len(self) == 0


def test_doubly_linked_list() -> None:
    """
    >>> test_doubly_linked_list()
    """
    linked_list = DoublyLinkedList()
    assert linked_list.is_empty() is True
    assert str(linked_list) == ""

    try:
        linked_list.delete_head()
        raise AssertionError  # This should not happen.
    except IndexError:
        assert True  # This should happen.

    try:
        linked_list.delete_tail()
        raise AssertionError  # This should not happen.
    except IndexError:
        assert True  # This should happen.

    for i in range(10):
        assert len(linked_list) == i
        linked_list.insert_at_nth(i, i + 1)
    assert str(linked_list) == "->".join(str(i) for i in range(1, 11))

    linked_list.insert_at_head(0)
    linked_list.insert_at_tail(11)
    assert str(linked_list) == "->".join(str(i) for i in range(12))

    assert linked_list.delete_head() == 0
    assert linked_list.delete_at_nth(9) == 10
    assert linked_list.delete_tail() == 11
    assert len(linked_list) == 9
    assert str(linked_list) == "->".join(str(i) for i in range(1, 10))


if __name__ == "__main__":
    from doctest import testmod

    testmod()


================================================
File: data_structures/linked_list/doubly_linked_list_two.py
================================================
"""
- A linked list is similar to an array, it holds values. However, links in a linked
    list do not have indexes.
- This is an example of a double ended, doubly linked list.
- Each link references the next link and the previous one.
- A Doubly Linked List (DLL) contains an extra pointer, typically called previous
    pointer, together with next pointer and data which are there in singly linked list.
 - Advantages over SLL - It can be traversed in both forward and backward direction.
     Delete operation is more efficient
"""


class Node:
    def __init__(self, data: int, previous=None, next_node=None):
        self.data = data
        self.previous = previous
        self.next = next_node

    def __str__(self) -> str:
        return f"{self.data}"

    def get_data(self) -> int:
        return self.data

    def get_next(self):
        return self.next

    def get_previous(self):
        return self.previous


class LinkedListIterator:
    def __init__(self, head):
        self.current = head

    def __iter__(self):
        return self

    def __next__(self):
        if not self.current:
            raise StopIteration
        else:
            value = self.current.get_data()
            self.current = self.current.get_next()
            return value


class LinkedList:
    def __init__(self):
        self.head = None  # First node in list
        self.tail = None  # Last node in list

    def __str__(self):
        current = self.head
        nodes = []
        while current is not None:
            nodes.append(current.get_data())
            current = current.get_next()
        return " ".join(str(node) for node in nodes)

    def __contains__(self, value: int):
        current = self.head
        while current:
            if current.get_data() == value:
                return True
            current = current.get_next()
        return False

    def __iter__(self):
        return LinkedListIterator(self.head)

    def get_head_data(self):
        if self.head:
            return self.head.get_data()
        return None

    def get_tail_data(self):
        if self.tail:
            return self.tail.get_data()
        return None

    def set_head(self, node: Node) -> None:
        if self.head is None:
            self.head = node
            self.tail = node
        else:
            self.insert_before_node(self.head, node)

    def set_tail(self, node: Node) -> None:
        if self.head is None:
            self.set_head(node)
        else:
            self.insert_after_node(self.tail, node)

    def insert(self, value: int) -> None:
        node = Node(value)
        if self.head is None:
            self.set_head(node)
        else:
            self.set_tail(node)

    def insert_before_node(self, node: Node, node_to_insert: Node) -> None:
        node_to_insert.next = node
        node_to_insert.previous = node.previous

        if node.get_previous() is None:
            self.head = node_to_insert
        else:
            node.previous.next = node_to_insert

        node.previous = node_to_insert

    def insert_after_node(self, node: Node, node_to_insert: Node) -> None:
        node_to_insert.previous = node
        node_to_insert.next = node.next

        if node.get_next() is None:
            self.tail = node_to_insert
        else:
            node.next.previous = node_to_insert

        node.next = node_to_insert

    def insert_at_position(self, position: int, value: int) -> None:
        current_position = 1
        new_node = Node(value)
        node = self.head
        while node:
            if current_position == position:
                self.insert_before_node(node, new_node)
                return
            current_position += 1
            node = node.next
        self.insert_after_node(self.tail, new_node)

    def get_node(self, item: int) -> Node:
        node = self.head
        while node:
            if node.get_data() == item:
                return node
            node = node.get_next()
        raise Exception("Node not found")

    def delete_value(self, value):
        if (node := self.get_node(value)) is not None:
            if node == self.head:
                self.head = self.head.get_next()

            if node == self.tail:
                self.tail = self.tail.get_previous()

            self.remove_node_pointers(node)

    @staticmethod
    def remove_node_pointers(node: Node) -> None:
        if node.get_next():
            node.next.previous = node.previous

        if node.get_previous():
            node.previous.next = node.next

        node.next = None
        node.previous = None

    def is_empty(self):
        return self.head is None


def create_linked_list() -> None:
    """
    >>> new_linked_list = LinkedList()
    >>> new_linked_list.get_head_data() is None
    True
    >>> new_linked_list.get_tail_data() is None
    True
    >>> new_linked_list.is_empty()
    True
    >>> new_linked_list.insert(10)
    >>> new_linked_list.get_head_data()
    10
    >>> new_linked_list.get_tail_data()
    10
    >>> new_linked_list.insert_at_position(position=3, value=20)
    >>> new_linked_list.get_head_data()
    10
    >>> new_linked_list.get_tail_data()
    20
    >>> new_linked_list.set_head(Node(1000))
    >>> new_linked_list.get_head_data()
    1000
    >>> new_linked_list.get_tail_data()
    20
    >>> new_linked_list.set_tail(Node(2000))
    >>> new_linked_list.get_head_data()
    1000
    >>> new_linked_list.get_tail_data()
    2000
    >>> for value in new_linked_list:
    ...    print(value)
    1000
    10
    20
    2000
    >>> new_linked_list.is_empty()
    False
    >>> for value in new_linked_list:
    ...    print(value)
    1000
    10
    20
    2000
    >>> 10 in new_linked_list
    True
    >>> new_linked_list.delete_value(value=10)
    >>> 10 in new_linked_list
    False
    >>> new_linked_list.delete_value(value=2000)
    >>> new_linked_list.get_tail_data()
    20
    >>> new_linked_list.delete_value(value=1000)
    >>> new_linked_list.get_tail_data()
    20
    >>> new_linked_list.get_head_data()
    20
    >>> for value in new_linked_list:
    ...    print(value)
    20
    >>> new_linked_list.delete_value(value=20)
    >>> for value in new_linked_list:
    ...    print(value)
    >>> for value in range(1,10):
    ...    new_linked_list.insert(value=value)
    >>> for value in new_linked_list:
    ...    print(value)
    1
    2
    3
    4
    5
    6
    7
    8
    9
    """


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/linked_list/floyds_cycle_detection.py
================================================
"""
Floyd's cycle detection algorithm is a popular algorithm used to detect cycles
in a linked list. It uses two pointers, a slow pointer and a fast pointer,
to traverse the linked list. The slow pointer moves one node at a time while the fast
pointer moves two nodes at a time. If there is a cycle in the linked list,
the fast pointer will eventually catch up to the slow pointer and they will
meet at the same node. If there is no cycle, the fast pointer will reach the end of
the linked list and the algorithm will terminate.

For more information: https://en.wikipedia.org/wiki/Cycle_detection#Floyd's_tortoise_and_hare
"""

from collections.abc import Iterator
from dataclasses import dataclass
from typing import Any, Self


@dataclass
class Node:
    """
    A class representing a node in a singly linked list.
    """

    data: Any
    next_node: Self | None = None


@dataclass
class LinkedList:
    """
    A class representing a singly linked list.
    """

    head: Node | None = None

    def __iter__(self) -> Iterator:
        """
        Iterates through the linked list.

        Returns:
            Iterator: An iterator over the linked list.

        Examples:
        >>> linked_list = LinkedList()
        >>> list(linked_list)
        []
        >>> linked_list.add_node(1)
        >>> tuple(linked_list)
        (1,)
        """
        visited = []
        node = self.head
        while node:
            # Avoid infinite loop in there's a cycle
            if node in visited:
                return
            visited.append(node)
            yield node.data
            node = node.next_node

    def add_node(self, data: Any) -> None:
        """
        Adds a new node to the end of the linked list.

        Args:
            data (Any): The data to be stored in the new node.

        Examples:
        >>> linked_list = LinkedList()
        >>> linked_list.add_node(1)
        >>> linked_list.add_node(2)
        >>> linked_list.add_node(3)
        >>> linked_list.add_node(4)
        >>> tuple(linked_list)
        (1, 2, 3, 4)
        """
        new_node = Node(data)

        if self.head is None:
            self.head = new_node
            return

        current_node = self.head
        while current_node.next_node is not None:
            current_node = current_node.next_node

        current_node.next_node = new_node

    def detect_cycle(self) -> bool:
        """
        Detects if there is a cycle in the linked list using
        Floyd's cycle detection algorithm.

        Returns:
            bool: True if there is a cycle, False otherwise.

        Examples:
        >>> linked_list = LinkedList()
        >>> linked_list.add_node(1)
        >>> linked_list.add_node(2)
        >>> linked_list.add_node(3)
        >>> linked_list.add_node(4)

        >>> linked_list.detect_cycle()
        False

        # Create a cycle in the linked list
        >>> linked_list.head.next_node.next_node.next_node = linked_list.head.next_node

        >>> linked_list.detect_cycle()
        True
        """
        if self.head is None:
            return False

        slow_pointer: Node | None = self.head
        fast_pointer: Node | None = self.head

        while fast_pointer is not None and fast_pointer.next_node is not None:
            slow_pointer = slow_pointer.next_node if slow_pointer else None
            fast_pointer = fast_pointer.next_node.next_node
            if slow_pointer == fast_pointer:
                return True

        return False


if __name__ == "__main__":
    import doctest

    doctest.testmod()

    linked_list = LinkedList()
    linked_list.add_node(1)
    linked_list.add_node(2)
    linked_list.add_node(3)
    linked_list.add_node(4)

    # Create a cycle in the linked list
    # It first checks if the head, next_node, and next_node.next_node attributes of the
    # linked list are not None to avoid any potential type errors.
    if (
        linked_list.head
        and linked_list.head.next_node
        and linked_list.head.next_node.next_node
    ):
        linked_list.head.next_node.next_node.next_node = linked_list.head.next_node

    has_cycle = linked_list.detect_cycle()
    print(has_cycle)  # Output: True


================================================
File: data_structures/linked_list/from_sequence.py
================================================
# Recursive Prorgam to create a Linked List from a sequence and
# print a string representation of it.


class Node:
    def __init__(self, data=None):
        self.data = data
        self.next = None

    def __repr__(self):
        """Returns a visual representation of the node and all its following nodes."""
        string_rep = ""
        temp = self
        while temp:
            string_rep += f"<{temp.data}> ---> "
            temp = temp.next
        string_rep += "<END>"
        return string_rep


def make_linked_list(elements_list):
    """Creates a Linked List from the elements of the given sequence
    (list/tuple) and returns the head of the Linked List."""

    # if elements_list is empty
    if not elements_list:
        raise Exception("The Elements List is empty")

    # Set first element as Head
    head = Node(elements_list[0])
    current = head
    # Loop through elements from position 1
    for data in elements_list[1:]:
        current.next = Node(data)
        current = current.next
    return head


list_data = [1, 3, 5, 32, 44, 12, 43]
print(f"List: {list_data}")
print("Creating Linked List from List.")
linked_list = make_linked_list(list_data)
print("Linked List:")
print(linked_list)


================================================
File: data_structures/linked_list/has_loop.py
================================================
from __future__ import annotations

from typing import Any


class ContainsLoopError(Exception):
    pass


class Node:
    def __init__(self, data: Any) -> None:
        self.data: Any = data
        self.next_node: Node | None = None

    def __iter__(self):
        node = self
        visited = set()
        while node:
            if node in visited:
                raise ContainsLoopError
            visited.add(node)
            yield node.data
            node = node.next_node

    @property
    def has_loop(self) -> bool:
        """
        A loop is when the exact same Node appears more than once in a linked list.
        >>> root_node = Node(1)
        >>> root_node.next_node = Node(2)
        >>> root_node.next_node.next_node = Node(3)
        >>> root_node.next_node.next_node.next_node = Node(4)
        >>> root_node.has_loop
        False
        >>> root_node.next_node.next_node.next_node = root_node.next_node
        >>> root_node.has_loop
        True
        """
        try:
            list(self)
            return False
        except ContainsLoopError:
            return True


if __name__ == "__main__":
    root_node = Node(1)
    root_node.next_node = Node(2)
    root_node.next_node.next_node = Node(3)
    root_node.next_node.next_node.next_node = Node(4)
    print(root_node.has_loop)  # False
    root_node.next_node.next_node.next_node = root_node.next_node
    print(root_node.has_loop)  # True

    root_node = Node(5)
    root_node.next_node = Node(6)
    root_node.next_node.next_node = Node(5)
    root_node.next_node.next_node.next_node = Node(6)
    print(root_node.has_loop)  # False

    root_node = Node(1)
    print(root_node.has_loop)  # False


================================================
File: data_structures/linked_list/is_palindrome.py
================================================
from __future__ import annotations

from dataclasses import dataclass


@dataclass
class ListNode:
    val: int = 0
    next_node: ListNode | None = None


def is_palindrome(head: ListNode | None) -> bool:
    """
    Check if a linked list is a palindrome.

    Args:
        head: The head of the linked list.

    Returns:
        bool: True if the linked list is a palindrome, False otherwise.

    Examples:
        >>> is_palindrome(None)
        True

        >>> is_palindrome(ListNode(1))
        True

        >>> is_palindrome(ListNode(1, ListNode(2)))
        False

        >>> is_palindrome(ListNode(1, ListNode(2, ListNode(1))))
        True

        >>> is_palindrome(ListNode(1, ListNode(2, ListNode(2, ListNode(1)))))
        True
    """
    if not head:
        return True
    # split the list to two parts
    fast: ListNode | None = head.next_node
    slow: ListNode | None = head
    while fast and fast.next_node:
        fast = fast.next_node.next_node
        slow = slow.next_node if slow else None
    if slow:
        # slow will always be defined,
        # adding this check to resolve mypy static check
        second = slow.next_node
        slow.next_node = None  # Don't forget here! But forget still works!
    # reverse the second part
    node: ListNode | None = None
    while second:
        nxt = second.next_node
        second.next_node = node
        node = second
        second = nxt
    # compare two parts
    # second part has the same or one less node
    while node and head:
        if node.val != head.val:
            return False
        node = node.next_node
        head = head.next_node
    return True


def is_palindrome_stack(head: ListNode | None) -> bool:
    """
    Check if a linked list is a palindrome using a stack.

    Args:
        head (ListNode): The head of the linked list.

    Returns:
        bool: True if the linked list is a palindrome, False otherwise.

    Examples:
        >>> is_palindrome_stack(None)
        True

        >>> is_palindrome_stack(ListNode(1))
        True

        >>> is_palindrome_stack(ListNode(1, ListNode(2)))
        False

        >>> is_palindrome_stack(ListNode(1, ListNode(2, ListNode(1))))
        True

        >>> is_palindrome_stack(ListNode(1, ListNode(2, ListNode(2, ListNode(1)))))
        True
    """
    if not head or not head.next_node:
        return True

    # 1. Get the midpoint (slow)
    slow: ListNode | None = head
    fast: ListNode | None = head
    while fast and fast.next_node:
        fast = fast.next_node.next_node
        slow = slow.next_node if slow else None

    # slow will always be defined,
    # adding this check to resolve mypy static check
    if slow:
        stack = [slow.val]

        # 2. Push the second half into the stack
        while slow.next_node:
            slow = slow.next_node
            stack.append(slow.val)

        # 3. Comparison
        cur: ListNode | None = head
        while stack and cur:
            if stack.pop() != cur.val:
                return False
            cur = cur.next_node

    return True


def is_palindrome_dict(head: ListNode | None) -> bool:
    """
    Check if a linked list is a palindrome using a dictionary.

    Args:
        head (ListNode): The head of the linked list.

    Returns:
        bool: True if the linked list is a palindrome, False otherwise.

    Examples:
        >>> is_palindrome_dict(None)
        True

        >>> is_palindrome_dict(ListNode(1))
        True

        >>> is_palindrome_dict(ListNode(1, ListNode(2)))
        False

        >>> is_palindrome_dict(ListNode(1, ListNode(2, ListNode(1))))
        True

        >>> is_palindrome_dict(ListNode(1, ListNode(2, ListNode(2, ListNode(1)))))
        True

        >>> is_palindrome_dict(
        ...     ListNode(
        ...         1, ListNode(2, ListNode(1, ListNode(3, ListNode(2, ListNode(1)))))
        ...     )
        ... )
        False
    """
    if not head or not head.next_node:
        return True
    d: dict[int, list[int]] = {}
    pos = 0
    while head:
        if head.val in d:
            d[head.val].append(pos)
        else:
            d[head.val] = [pos]
        head = head.next_node
        pos += 1
    checksum = pos - 1
    middle = 0
    for v in d.values():
        if len(v) % 2 != 0:
            middle += 1
        else:
            for step, i in enumerate(range(len(v))):
                if v[i] + v[len(v) - 1 - step] != checksum:
                    return False
        if middle > 1:
            return False
    return True


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/linked_list/merge_two_lists.py
================================================
"""
Algorithm that merges two sorted linked lists into one sorted linked list.
"""

from __future__ import annotations

from collections.abc import Iterable, Iterator
from dataclasses import dataclass

test_data_odd = (3, 9, -11, 0, 7, 5, 1, -1)
test_data_even = (4, 6, 2, 0, 8, 10, 3, -2)


@dataclass
class Node:
    data: int
    next_node: Node | None


class SortedLinkedList:
    def __init__(self, ints: Iterable[int]) -> None:
        self.head: Node | None = None
        for i in sorted(ints, reverse=True):
            self.head = Node(i, self.head)

    def __iter__(self) -> Iterator[int]:
        """
        >>> tuple(SortedLinkedList(test_data_odd)) == tuple(sorted(test_data_odd))
        True
        >>> tuple(SortedLinkedList(test_data_even)) == tuple(sorted(test_data_even))
        True
        """
        node = self.head
        while node:
            yield node.data
            node = node.next_node

    def __len__(self) -> int:
        """
        >>> for i in range(3):
        ...     len(SortedLinkedList(range(i))) == i
        True
        True
        True
        >>> len(SortedLinkedList(test_data_odd))
        8
        """
        return sum(1 for _ in self)

    def __str__(self) -> str:
        """
        >>> str(SortedLinkedList([]))
        ''
        >>> str(SortedLinkedList(test_data_odd))
        '-11 -> -1 -> 0 -> 1 -> 3 -> 5 -> 7 -> 9'
        >>> str(SortedLinkedList(test_data_even))
        '-2 -> 0 -> 2 -> 3 -> 4 -> 6 -> 8 -> 10'
        """
        return " -> ".join([str(node) for node in self])


def merge_lists(
    sll_one: SortedLinkedList, sll_two: SortedLinkedList
) -> SortedLinkedList:
    """
    >>> SSL = SortedLinkedList
    >>> merged = merge_lists(SSL(test_data_odd), SSL(test_data_even))
    >>> len(merged)
    16
    >>> str(merged)
    '-11 -> -2 -> -1 -> 0 -> 0 -> 1 -> 2 -> 3 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8 -> 9 -> 10'
    >>> list(merged) == list(sorted(test_data_odd + test_data_even))
    True
    """
    return SortedLinkedList(list(sll_one) + list(sll_two))


if __name__ == "__main__":
    import doctest

    doctest.testmod()
    SSL = SortedLinkedList
    print(merge_lists(SSL(test_data_odd), SSL(test_data_even)))


================================================
File: data_structures/linked_list/middle_element_of_linked_list.py
================================================
from __future__ import annotations


class Node:
    def __init__(self, data: int) -> None:
        self.data = data
        self.next = None


class LinkedList:
    def __init__(self):
        self.head = None

    def push(self, new_data: int) -> int:
        new_node = Node(new_data)
        new_node.next = self.head
        self.head = new_node
        return self.head.data

    def middle_element(self) -> int | None:
        """
        >>> link = LinkedList()
        >>> link.middle_element()
        No element found.
        >>> link.push(5)
        5
        >>> link.push(6)
        6
        >>> link.push(8)
        8
        >>> link.push(8)
        8
        >>> link.push(10)
        10
        >>> link.push(12)
        12
        >>> link.push(17)
        17
        >>> link.push(7)
        7
        >>> link.push(3)
        3
        >>> link.push(20)
        20
        >>> link.push(-20)
        -20
        >>> link.middle_element()
        12
        >>>
        """
        slow_pointer = self.head
        fast_pointer = self.head
        if self.head:
            while fast_pointer and fast_pointer.next:
                fast_pointer = fast_pointer.next.next
                slow_pointer = slow_pointer.next
            return slow_pointer.data
        else:
            print("No element found.")
            return None


if __name__ == "__main__":
    link = LinkedList()
    for _ in range(int(input().strip())):
        data = int(input().strip())
        link.push(data)
    print(link.middle_element())


================================================
File: data_structures/linked_list/print_reverse.py
================================================
from __future__ import annotations

from collections.abc import Iterable, Iterator
from dataclasses import dataclass


@dataclass
class Node:
    data: int
    next_node: Node | None = None


class LinkedList:
    """A class to represent a Linked List.
    Use a tail pointer to speed up the append() operation.
    """

    def __init__(self) -> None:
        """Initialize a LinkedList with the head node set to None.
        >>> linked_list = LinkedList()
        >>> (linked_list.head, linked_list.tail)
        (None, None)
        """
        self.head: Node | None = None
        self.tail: Node | None = None  # Speeds up the append() operation

    def __iter__(self) -> Iterator[int]:
        """Iterate the LinkedList yielding each Node's data.
        >>> linked_list = LinkedList()
        >>> items = (1, 2, 3, 4, 5)
        >>> linked_list.extend(items)
        >>> tuple(linked_list) == items
        True
        """
        node = self.head
        while node:
            yield node.data
            node = node.next_node

    def __repr__(self) -> str:
        """Returns a string representation of the LinkedList.
        >>> linked_list = LinkedList()
        >>> str(linked_list)
        ''
        >>> linked_list.append(1)
        >>> str(linked_list)
        '1'
        >>> linked_list.extend([2, 3, 4, 5])
        >>> str(linked_list)
        '1 -> 2 -> 3 -> 4 -> 5'
        """
        return " -> ".join([str(data) for data in self])

    def append(self, data: int) -> None:
        """Appends a new node with the given data to the end of the LinkedList.
        >>> linked_list = LinkedList()
        >>> str(linked_list)
        ''
        >>> linked_list.append(1)
        >>> str(linked_list)
        '1'
        >>> linked_list.append(2)
        >>> str(linked_list)
        '1 -> 2'
        """
        if self.tail:
            self.tail.next_node = self.tail = Node(data)
        else:
            self.head = self.tail = Node(data)

    def extend(self, items: Iterable[int]) -> None:
        """Appends each item to the end of the LinkedList.
        >>> linked_list = LinkedList()
        >>> linked_list.extend([])
        >>> str(linked_list)
        ''
        >>> linked_list.extend([1, 2])
        >>> str(linked_list)
        '1 -> 2'
        >>> linked_list.extend([3,4])
        >>> str(linked_list)
        '1 -> 2 -> 3 -> 4'
        """
        for item in items:
            self.append(item)


def make_linked_list(elements_list: Iterable[int]) -> LinkedList:
    """Creates a Linked List from the elements of the given sequence
    (list/tuple) and returns the head of the Linked List.
    >>> make_linked_list([])
    Traceback (most recent call last):
        ...
    Exception: The Elements List is empty
    >>> make_linked_list([7])
    7
    >>> make_linked_list(['abc'])
    abc
    >>> make_linked_list([7, 25])
    7 -> 25
    """
    if not elements_list:
        raise Exception("The Elements List is empty")

    linked_list = LinkedList()
    linked_list.extend(elements_list)
    return linked_list


def in_reverse(linked_list: LinkedList) -> str:
    """Prints the elements of the given Linked List in reverse order
    >>> in_reverse(LinkedList())
    ''
    >>> in_reverse(make_linked_list([69, 88, 73]))
    '73 <- 88 <- 69'
    """
    return " <- ".join(str(line) for line in reversed(tuple(linked_list)))


if __name__ == "__main__":
    from doctest import testmod

    testmod()
    linked_list = make_linked_list((14, 52, 14, 12, 43))
    print(f"Linked List:  {linked_list}")
    print(f"Reverse List: {in_reverse(linked_list)}")


================================================
File: data_structures/linked_list/reverse_k_group.py
================================================
from __future__ import annotations

from collections.abc import Iterable, Iterator
from dataclasses import dataclass


@dataclass
class Node:
    data: int
    next_node: Node | None = None


class LinkedList:
    def __init__(self, ints: Iterable[int]) -> None:
        self.head: Node | None = None
        for i in ints:
            self.append(i)

    def __iter__(self) -> Iterator[int]:
        """
        >>> ints = []
        >>> list(LinkedList(ints)) == ints
        True
        >>> ints = tuple(range(5))
        >>> tuple(LinkedList(ints)) == ints
        True
        """
        node = self.head
        while node:
            yield node.data
            node = node.next_node

    def __len__(self) -> int:
        """
        >>> for i in range(3):
        ...     len(LinkedList(range(i))) == i
        True
        True
        True
        >>> len(LinkedList("abcdefgh"))
        8
        """
        return sum(1 for _ in self)

    def __str__(self) -> str:
        """
        >>> str(LinkedList([]))
        ''
        >>> str(LinkedList(range(5)))
        '0 -> 1 -> 2 -> 3 -> 4'
        """
        return " -> ".join([str(node) for node in self])

    def append(self, data: int) -> None:
        """
        >>> ll = LinkedList([1, 2])
        >>> tuple(ll)
        (1, 2)
        >>> ll.append(3)
        >>> tuple(ll)
        (1, 2, 3)
        >>> ll.append(4)
        >>> tuple(ll)
        (1, 2, 3, 4)
        >>> len(ll)
        4
        """
        if not self.head:
            self.head = Node(data)
            return
        node = self.head
        while node.next_node:
            node = node.next_node
        node.next_node = Node(data)

    def reverse_k_nodes(self, group_size: int) -> None:
        """
        reverse nodes within groups of size k
        >>> ll = LinkedList([1, 2, 3, 4, 5])
        >>> ll.reverse_k_nodes(2)
        >>> tuple(ll)
        (2, 1, 4, 3, 5)
        >>> str(ll)
        '2 -> 1 -> 4 -> 3 -> 5'
        """
        if self.head is None or self.head.next_node is None:
            return

        length = len(self)
        dummy_head = Node(0)
        dummy_head.next_node = self.head
        previous_node = dummy_head

        while length >= group_size:
            current_node = previous_node.next_node
            assert current_node
            next_node = current_node.next_node
            for _ in range(1, group_size):
                assert next_node, current_node
                current_node.next_node = next_node.next_node
                assert previous_node
                next_node.next_node = previous_node.next_node
                previous_node.next_node = next_node
                next_node = current_node.next_node
            previous_node = current_node
            length -= group_size
        self.head = dummy_head.next_node


if __name__ == "__main__":
    import doctest

    doctest.testmod()
    ll = LinkedList([1, 2, 3, 4, 5])
    print(f"Original Linked List: {ll}")
    k = 2
    ll.reverse_k_nodes(k)
    print(f"After reversing groups of size {k}: {ll}")


================================================
File: data_structures/linked_list/rotate_to_the_right.py
================================================
from __future__ import annotations

from dataclasses import dataclass


@dataclass
class Node:
    data: int
    next_node: Node | None = None


def print_linked_list(head: Node | None) -> None:
    """
        Print the entire linked list iteratively.

        This function prints the elements of a linked list separated by '->'.

        Parameters:
            head (Node | None): The head of the linked list to be printed,
    or None if the linked list is empty.

        >>> head = insert_node(None, 0)
        >>> head = insert_node(head, 2)
        >>> head = insert_node(head, 1)
        >>> print_linked_list(head)
        0->2->1
        >>> head = insert_node(head, 4)
        >>> head = insert_node(head, 5)
        >>> print_linked_list(head)
        0->2->1->4->5
    """
    if head is None:
        return
    while head.next_node is not None:
        print(head.data, end="->")
        head = head.next_node
    print(head.data)


def insert_node(head: Node | None, data: int) -> Node:
    """
    Insert a new node at the end of a linked list and return the new head.

    Parameters:
        head (Node | None): The head of the linked list.
        data (int): The data to be inserted into the new node.

    Returns:
        Node: The new head of the linked list.

    >>> head = insert_node(None, 10)
    >>> head = insert_node(head, 9)
    >>> head = insert_node(head, 8)
    >>> print_linked_list(head)
    10->9->8
    """
    new_node = Node(data)
    # If the linked list is empty, the new_node becomes the head
    if head is None:
        return new_node

    temp_node = head
    while temp_node.next_node:
        temp_node = temp_node.next_node

    temp_node.next_node = new_node
    return head


def rotate_to_the_right(head: Node, places: int) -> Node:
    """
    Rotate a linked list to the right by places times.

    Parameters:
        head: The head of the linked list.
        places: The number of places to rotate.

    Returns:
        Node: The head of the rotated linked list.

    >>> rotate_to_the_right(None, places=1)
    Traceback (most recent call last):
        ...
    ValueError: The linked list is empty.
    >>> head = insert_node(None, 1)
    >>> rotate_to_the_right(head, places=1) == head
    True
    >>> head = insert_node(None, 1)
    >>> head = insert_node(head, 2)
    >>> head = insert_node(head, 3)
    >>> head = insert_node(head, 4)
    >>> head = insert_node(head, 5)
    >>> new_head = rotate_to_the_right(head, places=2)
    >>> print_linked_list(new_head)
    4->5->1->2->3
    """
    # Check if the list is empty or has only one element
    if not head:
        raise ValueError("The linked list is empty.")

    if head.next_node is None:
        return head

    # Calculate the length of the linked list
    length = 1
    temp_node = head
    while temp_node.next_node is not None:
        length += 1
        temp_node = temp_node.next_node

    # Adjust the value of places to avoid places longer than the list.
    places %= length

    if places == 0:
        return head  # As no rotation is needed.

    # Find the new head position after rotation.
    new_head_index = length - places

    # Traverse to the new head position
    temp_node = head
    for _ in range(new_head_index - 1):
        assert temp_node.next_node
        temp_node = temp_node.next_node

    # Update pointers to perform rotation
    assert temp_node.next_node
    new_head = temp_node.next_node
    temp_node.next_node = None
    temp_node = new_head
    while temp_node.next_node:
        temp_node = temp_node.next_node
    temp_node.next_node = head

    assert new_head
    return new_head


if __name__ == "__main__":
    import doctest

    doctest.testmod()
    head = insert_node(None, 5)
    head = insert_node(head, 1)
    head = insert_node(head, 2)
    head = insert_node(head, 4)
    head = insert_node(head, 3)

    print("Original list: ", end="")
    print_linked_list(head)

    places = 3
    new_head = rotate_to_the_right(head, places)

    print(f"After {places} iterations: ", end="")
    print_linked_list(new_head)


================================================
File: data_structures/linked_list/singly_linked_list.py
================================================
from __future__ import annotations

from collections.abc import Iterator
from dataclasses import dataclass
from typing import Any


@dataclass
class Node:
    """
    Create and initialize Node class instance.
    >>> Node(20)
    Node(20)
    >>> Node("Hello, world!")
    Node(Hello, world!)
    >>> Node(None)
    Node(None)
    >>> Node(True)
    Node(True)
    """

    data: Any
    next_node: Node | None = None

    def __repr__(self) -> str:
        """
        Get the string representation of this node.
        >>> Node(10).__repr__()
        'Node(10)'
        >>> repr(Node(10))
        'Node(10)'
        >>> str(Node(10))
        'Node(10)'
        >>> Node(10)
        Node(10)
        """
        return f"Node({self.data})"


class LinkedList:
    def __init__(self):
        """
        Create and initialize LinkedList class instance.
        >>> linked_list = LinkedList()
        >>> linked_list.head is None
        True
        """
        self.head = None

    def __iter__(self) -> Iterator[Any]:
        """
        This function is intended for iterators to access
        and iterate through data inside linked list.
        >>> linked_list = LinkedList()
        >>> linked_list.insert_tail("tail")
        >>> linked_list.insert_tail("tail_1")
        >>> linked_list.insert_tail("tail_2")
        >>> for node in linked_list: # __iter__ used here.
        ...     node
        'tail'
        'tail_1'
        'tail_2'
        """
        node = self.head
        while node:
            yield node.data
            node = node.next_node

    def __len__(self) -> int:
        """
        Return length of linked list i.e. number of nodes
        >>> linked_list = LinkedList()
        >>> len(linked_list)
        0
        >>> linked_list.insert_tail("tail")
        >>> len(linked_list)
        1
        >>> linked_list.insert_head("head")
        >>> len(linked_list)
        2
        >>> _ = linked_list.delete_tail()
        >>> len(linked_list)
        1
        >>> _ = linked_list.delete_head()
        >>> len(linked_list)
        0
        """
        return sum(1 for _ in self)

    def __repr__(self) -> str:
        """
        String representation/visualization of a Linked Lists
        >>> linked_list = LinkedList()
        >>> linked_list.insert_tail(1)
        >>> linked_list.insert_tail(3)
        >>> linked_list.__repr__()
        '1 -> 3'
        >>> repr(linked_list)
        '1 -> 3'
        >>> str(linked_list)
        '1 -> 3'
        >>> linked_list.insert_tail(5)
        >>> f"{linked_list}"
        '1 -> 3 -> 5'
        """
        return " -> ".join([str(item) for item in self])

    def __getitem__(self, index: int) -> Any:
        """
        Indexing Support. Used to get a node at particular position
        >>> linked_list = LinkedList()
        >>> for i in range(0, 10):
        ...     linked_list.insert_nth(i, i)
        >>> all(str(linked_list[i]) == str(i) for i in range(0, 10))
        True
        >>> linked_list[-10]
        Traceback (most recent call last):
            ...
        ValueError: list index out of range.
        >>> linked_list[len(linked_list)]
        Traceback (most recent call last):
            ...
        ValueError: list index out of range.
        """
        if not 0 <= index < len(self):
            raise ValueError("list index out of range.")
        for i, node in enumerate(self):
            if i == index:
                return node
        return None

    # Used to change the data of a particular node
    def __setitem__(self, index: int, data: Any) -> None:
        """
        >>> linked_list = LinkedList()
        >>> for i in range(0, 10):
        ...     linked_list.insert_nth(i, i)
        >>> linked_list[0] = 666
        >>> linked_list[0]
        666
        >>> linked_list[5] = -666
        >>> linked_list[5]
        -666
        >>> linked_list[-10] = 666
        Traceback (most recent call last):
            ...
        ValueError: list index out of range.
        >>> linked_list[len(linked_list)] = 666
        Traceback (most recent call last):
            ...
        ValueError: list index out of range.
        """
        if not 0 <= index < len(self):
            raise ValueError("list index out of range.")
        current = self.head
        for _ in range(index):
            current = current.next_node
        current.data = data

    def insert_tail(self, data: Any) -> None:
        """
        Insert data to the end of linked list.
        >>> linked_list = LinkedList()
        >>> linked_list.insert_tail("tail")
        >>> linked_list
        tail
        >>> linked_list.insert_tail("tail_2")
        >>> linked_list
        tail -> tail_2
        >>> linked_list.insert_tail("tail_3")
        >>> linked_list
        tail -> tail_2 -> tail_3
        """
        self.insert_nth(len(self), data)

    def insert_head(self, data: Any) -> None:
        """
        Insert data to the beginning of linked list.
        >>> linked_list = LinkedList()
        >>> linked_list.insert_head("head")
        >>> linked_list
        head
        >>> linked_list.insert_head("head_2")
        >>> linked_list
        head_2 -> head
        >>> linked_list.insert_head("head_3")
        >>> linked_list
        head_3 -> head_2 -> head
        """
        self.insert_nth(0, data)

    def insert_nth(self, index: int, data: Any) -> None:
        """
        Insert data at given index.
        >>> linked_list = LinkedList()
        >>> linked_list.insert_tail("first")
        >>> linked_list.insert_tail("second")
        >>> linked_list.insert_tail("third")
        >>> linked_list
        first -> second -> third
        >>> linked_list.insert_nth(1, "fourth")
        >>> linked_list
        first -> fourth -> second -> third
        >>> linked_list.insert_nth(3, "fifth")
        >>> linked_list
        first -> fourth -> second -> fifth -> third
        """
        if not 0 <= index <= len(self):
            raise IndexError("list index out of range")
        new_node = Node(data)
        if self.head is None:
            self.head = new_node
        elif index == 0:
            new_node.next_node = self.head  # link new_node to head
            self.head = new_node
        else:
            temp = self.head
            for _ in range(index - 1):
                temp = temp.next_node
            new_node.next_node = temp.next_node
            temp.next_node = new_node

    def print_list(self) -> None:  # print every node data
        """
        This method prints every node data.
        >>> linked_list = LinkedList()
        >>> linked_list.insert_tail("first")
        >>> linked_list.insert_tail("second")
        >>> linked_list.insert_tail("third")
        >>> linked_list
        first -> second -> third
        """
        print(self)

    def delete_head(self) -> Any:
        """
        Delete the first node and return the
        node's data.
        >>> linked_list = LinkedList()
        >>> linked_list.insert_tail("first")
        >>> linked_list.insert_tail("second")
        >>> linked_list.insert_tail("third")
        >>> linked_list
        first -> second -> third
        >>> linked_list.delete_head()
        'first'
        >>> linked_list
        second -> third
        >>> linked_list.delete_head()
        'second'
        >>> linked_list
        third
        >>> linked_list.delete_head()
        'third'
        >>> linked_list.delete_head()
        Traceback (most recent call last):
            ...
        IndexError: List index out of range.
        """
        return self.delete_nth(0)

    def delete_tail(self) -> Any:  # delete from tail
        """
        Delete the tail end node and return the
        node's data.
        >>> linked_list = LinkedList()
        >>> linked_list.insert_tail("first")
        >>> linked_list.insert_tail("second")
        >>> linked_list.insert_tail("third")
        >>> linked_list
        first -> second -> third
        >>> linked_list.delete_tail()
        'third'
        >>> linked_list
        first -> second
        >>> linked_list.delete_tail()
        'second'
        >>> linked_list
        first
        >>> linked_list.delete_tail()
        'first'
        >>> linked_list.delete_tail()
        Traceback (most recent call last):
            ...
        IndexError: List index out of range.
        """
        return self.delete_nth(len(self) - 1)

    def delete_nth(self, index: int = 0) -> Any:
        """
        Delete node at given index and return the
        node's data.
        >>> linked_list = LinkedList()
        >>> linked_list.insert_tail("first")
        >>> linked_list.insert_tail("second")
        >>> linked_list.insert_tail("third")
        >>> linked_list
        first -> second -> third
        >>> linked_list.delete_nth(1) # delete middle
        'second'
        >>> linked_list
        first -> third
        >>> linked_list.delete_nth(5) # this raises error
        Traceback (most recent call last):
            ...
        IndexError: List index out of range.
        >>> linked_list.delete_nth(-1) # this also raises error
        Traceback (most recent call last):
            ...
        IndexError: List index out of range.
        """
        if not 0 <= index <= len(self) - 1:  # test if index is valid
            raise IndexError("List index out of range.")
        delete_node = self.head  # default first node
        if index == 0:
            self.head = self.head.next_node
        else:
            temp = self.head
            for _ in range(index - 1):
                temp = temp.next_node
            delete_node = temp.next_node
            temp.next_node = temp.next_node.next_node
        return delete_node.data

    def is_empty(self) -> bool:
        """
        Check if linked list is empty.
        >>> linked_list = LinkedList()
        >>> linked_list.is_empty()
        True
        >>> linked_list.insert_head("first")
        >>> linked_list.is_empty()
        False
        """
        return self.head is None

    def reverse(self) -> None:
        """
        This reverses the linked list order.
        >>> linked_list = LinkedList()
        >>> linked_list.insert_tail("first")
        >>> linked_list.insert_tail("second")
        >>> linked_list.insert_tail("third")
        >>> linked_list
        first -> second -> third
        >>> linked_list.reverse()
        >>> linked_list
        third -> second -> first
        """
        prev = None
        current = self.head

        while current:
            # Store the current node's next node.
            next_node = current.next_node
            # Make the current node's next_node point backwards
            current.next_node = prev
            # Make the previous node be the current node
            prev = current
            # Make the current node the next_node node (to progress iteration)
            current = next_node
        # Return prev in order to put the head at the end
        self.head = prev


def test_singly_linked_list() -> None:
    """
    >>> test_singly_linked_list()
    """
    linked_list = LinkedList()
    assert linked_list.is_empty() is True
    assert str(linked_list) == ""

    try:
        linked_list.delete_head()
        raise AssertionError  # This should not happen.
    except IndexError:
        assert True  # This should happen.

    try:
        linked_list.delete_tail()
        raise AssertionError  # This should not happen.
    except IndexError:
        assert True  # This should happen.

    for i in range(10):
        assert len(linked_list) == i
        linked_list.insert_nth(i, i + 1)
    assert str(linked_list) == " -> ".join(str(i) for i in range(1, 11))

    linked_list.insert_head(0)
    linked_list.insert_tail(11)
    assert str(linked_list) == " -> ".join(str(i) for i in range(12))

    assert linked_list.delete_head() == 0
    assert linked_list.delete_nth(9) == 10
    assert linked_list.delete_tail() == 11
    assert len(linked_list) == 9
    assert str(linked_list) == " -> ".join(str(i) for i in range(1, 10))

    assert all(linked_list[i] == i + 1 for i in range(9)) is True

    for i in range(9):
        linked_list[i] = -i
    assert all(linked_list[i] == -i for i in range(9)) is True

    linked_list.reverse()
    assert str(linked_list) == " -> ".join(str(i) for i in range(-8, 1))


def test_singly_linked_list_2() -> None:
    """
    This section of the test used varying data types for input.
    >>> test_singly_linked_list_2()
    """
    test_input = [
        -9,
        100,
        Node(77345112),
        "dlrow olleH",
        7,
        5555,
        0,
        -192.55555,
        "Hello, world!",
        77.9,
        Node(10),
        None,
        None,
        12.20,
    ]
    linked_list = LinkedList()

    for i in test_input:
        linked_list.insert_tail(i)

    # Check if it's empty or not
    assert linked_list.is_empty() is False
    assert (
        str(linked_list)
        == "-9 -> 100 -> Node(77345112) -> dlrow olleH -> 7 -> 5555 -> "
        "0 -> -192.55555 -> Hello, world! -> 77.9 -> Node(10) -> None -> None -> 12.2"
    )

    # Delete the head
    result = linked_list.delete_head()
    assert result == -9
    assert (
        str(linked_list) == "100 -> Node(77345112) -> dlrow olleH -> 7 -> 5555 -> 0 -> "
        "-192.55555 -> Hello, world! -> 77.9 -> Node(10) -> None -> None -> 12.2"
    )

    # Delete the tail
    result = linked_list.delete_tail()
    assert result == 12.2
    assert (
        str(linked_list) == "100 -> Node(77345112) -> dlrow olleH -> 7 -> 5555 -> 0 -> "
        "-192.55555 -> Hello, world! -> 77.9 -> Node(10) -> None -> None"
    )

    # Delete a node in specific location in linked list
    result = linked_list.delete_nth(10)
    assert result is None
    assert (
        str(linked_list) == "100 -> Node(77345112) -> dlrow olleH -> 7 -> 5555 -> 0 -> "
        "-192.55555 -> Hello, world! -> 77.9 -> Node(10) -> None"
    )

    # Add a Node instance to its head
    linked_list.insert_head(Node("Hello again, world!"))
    assert (
        str(linked_list)
        == "Node(Hello again, world!) -> 100 -> Node(77345112) -> dlrow olleH -> "
        "7 -> 5555 -> 0 -> -192.55555 -> Hello, world! -> 77.9 -> Node(10) -> None"
    )

    # Add None to its tail
    linked_list.insert_tail(None)
    assert (
        str(linked_list)
        == "Node(Hello again, world!) -> 100 -> Node(77345112) -> dlrow olleH -> 7 -> "
        "5555 -> 0 -> -192.55555 -> Hello, world! -> 77.9 -> Node(10) -> None -> None"
    )

    # Reverse the linked list
    linked_list.reverse()
    assert (
        str(linked_list)
        == "None -> None -> Node(10) -> 77.9 -> Hello, world! -> -192.55555 -> 0 -> "
        "5555 -> 7 -> dlrow olleH -> Node(77345112) -> 100 -> Node(Hello again, world!)"
    )


def main():
    from doctest import testmod

    testmod()

    linked_list = LinkedList()
    linked_list.insert_head(input("Inserting 1st at head ").strip())
    linked_list.insert_head(input("Inserting 2nd at head ").strip())
    print("\nPrint list:")
    linked_list.print_list()
    linked_list.insert_tail(input("\nInserting 1st at tail ").strip())
    linked_list.insert_tail(input("Inserting 2nd at tail ").strip())
    print("\nPrint list:")
    linked_list.print_list()
    print("\nDelete head")
    linked_list.delete_head()
    print("Delete tail")
    linked_list.delete_tail()
    print("\nPrint list:")
    linked_list.print_list()
    print("\nReverse linked list")
    linked_list.reverse()
    print("\nPrint list:")
    linked_list.print_list()
    print("\nString representation of linked list:")
    print(linked_list)
    print("\nReading/changing Node data using indexing:")
    print(f"Element at Position 1: {linked_list[1]}")
    linked_list[1] = input("Enter New Value: ").strip()
    print("New list:")
    print(linked_list)
    print(f"length of linked_list is : {len(linked_list)}")


if __name__ == "__main__":
    main()


================================================
File: data_structures/linked_list/skip_list.py
================================================
"""
Based on "Skip Lists: A Probabilistic Alternative to Balanced Trees" by William Pugh
https://epaperpress.com/sortsearch/download/skiplist.pdf
"""

from __future__ import annotations

from itertools import pairwise
from random import random
from typing import Generic, TypeVar

KT = TypeVar("KT")
VT = TypeVar("VT")


class Node(Generic[KT, VT]):
    def __init__(self, key: KT | str = "root", value: VT | None = None):
        self.key = key
        self.value = value
        self.forward: list[Node[KT, VT]] = []

    def __repr__(self) -> str:
        """
        :return: Visual representation of Node

        >>> node = Node("Key", 2)
        >>> repr(node)
        'Node(Key: 2)'
        """

        return f"Node({self.key}: {self.value})"

    @property
    def level(self) -> int:
        """
        :return: Number of forward references

        >>> node = Node("Key", 2)
        >>> node.level
        0
        >>> node.forward.append(Node("Key2", 4))
        >>> node.level
        1
        >>> node.forward.append(Node("Key3", 6))
        >>> node.level
        2
        """

        return len(self.forward)


class SkipList(Generic[KT, VT]):
    def __init__(self, p: float = 0.5, max_level: int = 16):
        self.head: Node[KT, VT] = Node[KT, VT]()
        self.level = 0
        self.p = p
        self.max_level = max_level

    def __str__(self) -> str:
        """
        :return: Visual representation of SkipList

        >>> skip_list = SkipList()
        >>> print(skip_list)
        SkipList(level=0)
        >>> skip_list.insert("Key1", "Value")
        >>> print(skip_list) # doctest: +ELLIPSIS
        SkipList(level=...
        [root]--...
        [Key1]--Key1...
        None    *...
        >>> skip_list.insert("Key2", "OtherValue")
        >>> print(skip_list) # doctest: +ELLIPSIS
        SkipList(level=...
        [root]--...
        [Key1]--Key1...
        [Key2]--Key2...
        None    *...
        """

        items = list(self)

        if len(items) == 0:
            return f"SkipList(level={self.level})"

        label_size = max((len(str(item)) for item in items), default=4)
        label_size = max(label_size, 4) + 4

        node = self.head
        lines = []

        forwards = node.forward.copy()
        lines.append(f"[{node.key}]".ljust(label_size, "-") + "* " * len(forwards))
        lines.append(" " * label_size + "| " * len(forwards))

        while len(node.forward) != 0:
            node = node.forward[0]

            lines.append(
                f"[{node.key}]".ljust(label_size, "-")
                + " ".join(str(n.key) if n.key == node.key else "|" for n in forwards)
            )
            lines.append(" " * label_size + "| " * len(forwards))
            forwards[: node.level] = node.forward

        lines.append("None".ljust(label_size) + "* " * len(forwards))
        return f"SkipList(level={self.level})\n" + "\n".join(lines)

    def __iter__(self):
        node = self.head

        while len(node.forward) != 0:
            yield node.forward[0].key
            node = node.forward[0]

    def random_level(self) -> int:
        """
        :return: Random level from [1, self.max_level] interval.
                 Higher values are less likely.
        """

        level = 1
        while random() < self.p and level < self.max_level:
            level += 1

        return level

    def _locate_node(self, key) -> tuple[Node[KT, VT] | None, list[Node[KT, VT]]]:
        """
        :param key: Searched key,
        :return: Tuple with searched node (or None if given key is not present)
                 and list of nodes that refer (if key is present) of should refer to
                 given node.
        """

        # Nodes with refer or should refer to output node
        update_vector = []

        node = self.head

        for i in reversed(range(self.level)):
            # i < node.level - When node level is lesser than `i` decrement `i`.
            # node.forward[i].key < key - Jumping to node with key value higher
            #                             or equal to searched key would result
            #                             in skipping searched key.
            while i < node.level and node.forward[i].key < key:
                node = node.forward[i]
            # Each leftmost node (relative to searched node) will potentially have to
            # be updated.
            update_vector.append(node)

        update_vector.reverse()  # Note that we were inserting values in reverse order.

        # len(node.forward) != 0 - If current node doesn't contain any further
        #                          references then searched key is not present.
        # node.forward[0].key == key - Next node key should be equal to search key
        #                              if key is present.
        if len(node.forward) != 0 and node.forward[0].key == key:
            return node.forward[0], update_vector
        else:
            return None, update_vector

    def delete(self, key: KT):
        """
        :param key: Key to remove from list.

        >>> skip_list = SkipList()
        >>> skip_list.insert(2, "Two")
        >>> skip_list.insert(1, "One")
        >>> skip_list.insert(3, "Three")
        >>> list(skip_list)
        [1, 2, 3]
        >>> skip_list.delete(2)
        >>> list(skip_list)
        [1, 3]
        """

        node, update_vector = self._locate_node(key)

        if node is not None:
            for i, update_node in enumerate(update_vector):
                # Remove or replace all references to removed node.
                if update_node.level > i and update_node.forward[i].key == key:
                    if node.level > i:
                        update_node.forward[i] = node.forward[i]
                    else:
                        update_node.forward = update_node.forward[:i]

    def insert(self, key: KT, value: VT):
        """
        :param key: Key to insert.
        :param value: Value associated with given key.

        >>> skip_list = SkipList()
        >>> skip_list.insert(2, "Two")
        >>> skip_list.find(2)
        'Two'
        >>> list(skip_list)
        [2]
        """

        node, update_vector = self._locate_node(key)
        if node is not None:
            node.value = value
        else:
            level = self.random_level()

            if level > self.level:
                # After level increase we have to add additional nodes to head.
                for _ in range(self.level - 1, level):
                    update_vector.append(self.head)
                self.level = level

            new_node = Node(key, value)

            for i, update_node in enumerate(update_vector[:level]):
                # Change references to pass through new node.
                if update_node.level > i:
                    new_node.forward.append(update_node.forward[i])

                if update_node.level < i + 1:
                    update_node.forward.append(new_node)
                else:
                    update_node.forward[i] = new_node

    def find(self, key: VT) -> VT | None:
        """
        :param key: Search key.
        :return: Value associated with given key or None if given key is not present.

        >>> skip_list = SkipList()
        >>> skip_list.find(2)
        >>> skip_list.insert(2, "Two")
        >>> skip_list.find(2)
        'Two'
        >>> skip_list.insert(2, "Three")
        >>> skip_list.find(2)
        'Three'
        """

        node, _ = self._locate_node(key)

        if node is not None:
            return node.value

        return None


def test_insert():
    skip_list = SkipList()
    skip_list.insert("Key1", 3)
    skip_list.insert("Key2", 12)
    skip_list.insert("Key3", 41)
    skip_list.insert("Key4", -19)

    node = skip_list.head
    all_values = {}
    while node.level != 0:
        node = node.forward[0]
        all_values[node.key] = node.value

    assert len(all_values) == 4
    assert all_values["Key1"] == 3
    assert all_values["Key2"] == 12
    assert all_values["Key3"] == 41
    assert all_values["Key4"] == -19


def test_insert_overrides_existing_value():
    skip_list = SkipList()
    skip_list.insert("Key1", 10)
    skip_list.insert("Key1", 12)

    skip_list.insert("Key5", 7)
    skip_list.insert("Key7", 10)
    skip_list.insert("Key10", 5)

    skip_list.insert("Key7", 7)
    skip_list.insert("Key5", 5)
    skip_list.insert("Key10", 10)

    node = skip_list.head
    all_values = {}
    while node.level != 0:
        node = node.forward[0]
        all_values[node.key] = node.value

    if len(all_values) != 4:
        print()
    assert len(all_values) == 4
    assert all_values["Key1"] == 12
    assert all_values["Key7"] == 7
    assert all_values["Key5"] == 5
    assert all_values["Key10"] == 10


def test_searching_empty_list_returns_none():
    skip_list = SkipList()
    assert skip_list.find("Some key") is None


def test_search():
    skip_list = SkipList()

    skip_list.insert("Key2", 20)
    assert skip_list.find("Key2") == 20

    skip_list.insert("Some Key", 10)
    skip_list.insert("Key2", 8)
    skip_list.insert("V", 13)

    assert skip_list.find("Y") is None
    assert skip_list.find("Key2") == 8
    assert skip_list.find("Some Key") == 10
    assert skip_list.find("V") == 13


def test_deleting_item_from_empty_list_do_nothing():
    skip_list = SkipList()
    skip_list.delete("Some key")

    assert len(skip_list.head.forward) == 0


def test_deleted_items_are_not_founded_by_find_method():
    skip_list = SkipList()

    skip_list.insert("Key1", 12)
    skip_list.insert("V", 13)
    skip_list.insert("X", 14)
    skip_list.insert("Key2", 15)

    skip_list.delete("V")
    skip_list.delete("Key2")

    assert skip_list.find("V") is None
    assert skip_list.find("Key2") is None


def test_delete_removes_only_given_key():
    skip_list = SkipList()

    skip_list.insert("Key1", 12)
    skip_list.insert("V", 13)
    skip_list.insert("X", 14)
    skip_list.insert("Key2", 15)

    skip_list.delete("V")
    assert skip_list.find("V") is None
    assert skip_list.find("X") == 14
    assert skip_list.find("Key1") == 12
    assert skip_list.find("Key2") == 15

    skip_list.delete("X")
    assert skip_list.find("V") is None
    assert skip_list.find("X") is None
    assert skip_list.find("Key1") == 12
    assert skip_list.find("Key2") == 15

    skip_list.delete("Key1")
    assert skip_list.find("V") is None
    assert skip_list.find("X") is None
    assert skip_list.find("Key1") is None
    assert skip_list.find("Key2") == 15

    skip_list.delete("Key2")
    assert skip_list.find("V") is None
    assert skip_list.find("X") is None
    assert skip_list.find("Key1") is None
    assert skip_list.find("Key2") is None


def test_delete_doesnt_leave_dead_nodes():
    skip_list = SkipList()

    skip_list.insert("Key1", 12)
    skip_list.insert("V", 13)
    skip_list.insert("X", 142)
    skip_list.insert("Key2", 15)

    skip_list.delete("X")

    def traverse_keys(node):
        yield node.key
        for forward_node in node.forward:
            yield from traverse_keys(forward_node)

    assert len(set(traverse_keys(skip_list.head))) == 4


def test_iter_always_yields_sorted_values():
    def is_sorted(lst):
        return all(next_item >= item for item, next_item in pairwise(lst))

    skip_list = SkipList()
    for i in range(10):
        skip_list.insert(i, i)
    assert is_sorted(list(skip_list))
    skip_list.delete(5)
    skip_list.delete(8)
    skip_list.delete(2)
    assert is_sorted(list(skip_list))
    skip_list.insert(-12, -12)
    skip_list.insert(77, 77)
    assert is_sorted(list(skip_list))


def pytests():
    for _ in range(100):
        # Repeat test 100 times due to the probabilistic nature of skip list
        # random values == random bugs
        test_insert()
        test_insert_overrides_existing_value()

        test_searching_empty_list_returns_none()
        test_search()

        test_deleting_item_from_empty_list_do_nothing()
        test_deleted_items_are_not_founded_by_find_method()
        test_delete_removes_only_given_key()
        test_delete_doesnt_leave_dead_nodes()

        test_iter_always_yields_sorted_values()


def main():
    """
    >>> pytests()
    """

    skip_list = SkipList()
    skip_list.insert(2, "2")
    skip_list.insert(4, "4")
    skip_list.insert(6, "4")
    skip_list.insert(4, "5")
    skip_list.insert(8, "4")
    skip_list.insert(9, "4")

    skip_list.delete(4)

    print(skip_list)


if __name__ == "__main__":
    import doctest

    doctest.testmod()
    main()


================================================
File: data_structures/linked_list/swap_nodes.py
================================================
from __future__ import annotations

from collections.abc import Iterator
from dataclasses import dataclass
from typing import Any


@dataclass
class Node:
    data: Any
    next_node: Node | None = None


@dataclass
class LinkedList:
    head: Node | None = None

    def __iter__(self) -> Iterator:
        """
        >>> linked_list = LinkedList()
        >>> list(linked_list)
        []
        >>> linked_list.push(0)
        >>> tuple(linked_list)
        (0,)
        """
        node = self.head
        while node:
            yield node.data
            node = node.next_node

    def __len__(self) -> int:
        """
        >>> linked_list = LinkedList()
        >>> len(linked_list)
        0
        >>> linked_list.push(0)
        >>> len(linked_list)
        1
        """
        return sum(1 for _ in self)

    def push(self, new_data: Any) -> None:
        """
        Add a new node with the given data to the beginning of the Linked List.

        Args:
            new_data (Any): The data to be added to the new node.

        Returns:
            None

        Examples:
            >>> linked_list = LinkedList()
            >>> linked_list.push(5)
            >>> linked_list.push(4)
            >>> linked_list.push(3)
            >>> linked_list.push(2)
            >>> linked_list.push(1)
            >>> list(linked_list)
            [1, 2, 3, 4, 5]
        """
        new_node = Node(new_data)
        new_node.next_node = self.head
        self.head = new_node

    def swap_nodes(self, node_data_1: Any, node_data_2: Any) -> None:
        """
        Swap the positions of two nodes in the Linked List based on their data values.

        Args:
            node_data_1: Data value of the first node to be swapped.
            node_data_2: Data value of the second node to be swapped.


        Note:
            If either of the specified data values isn't found then, no swapping occurs.

        Examples:
        When both values are present in a linked list.
            >>> linked_list = LinkedList()
            >>> linked_list.push(5)
            >>> linked_list.push(4)
            >>> linked_list.push(3)
            >>> linked_list.push(2)
            >>> linked_list.push(1)
            >>> list(linked_list)
            [1, 2, 3, 4, 5]
            >>> linked_list.swap_nodes(1, 5)
            >>> tuple(linked_list)
            (5, 2, 3, 4, 1)

        When one value is present and the other isn't in the linked list.
            >>> second_list = LinkedList()
            >>> second_list.push(6)
            >>> second_list.push(7)
            >>> second_list.push(8)
            >>> second_list.push(9)
            >>> second_list.swap_nodes(1, 6) is None
            True

        When both values are absent in the linked list.
            >>> second_list = LinkedList()
            >>> second_list.push(10)
            >>> second_list.push(9)
            >>> second_list.push(8)
            >>> second_list.push(7)
            >>> second_list.swap_nodes(1, 3) is None
            True

        When linkedlist is empty.
            >>> second_list = LinkedList()
            >>> second_list.swap_nodes(1, 3) is None
            True

        Returns:
            None
        """
        if node_data_1 == node_data_2:
            return

        node_1 = self.head
        while node_1 and node_1.data != node_data_1:
            node_1 = node_1.next_node
        node_2 = self.head
        while node_2 and node_2.data != node_data_2:
            node_2 = node_2.next_node
        if node_1 is None or node_2 is None:
            return
        # Swap the data values of the two nodes
        node_1.data, node_2.data = node_2.data, node_1.data


if __name__ == "__main__":
    """
    Python script that outputs the swap of nodes in a linked list.
    """
    from doctest import testmod

    testmod()
    linked_list = LinkedList()
    for i in range(5, 0, -1):
        linked_list.push(i)

    print(f"Original Linked List: {list(linked_list)}")
    linked_list.swap_nodes(1, 4)
    print(f"Modified Linked List: {list(linked_list)}")
    print("After swapping the nodes whose data is 1 and 4.")


================================================
File: data_structures/queues/circular_queue.py
================================================
# Implementation of Circular Queue (using Python lists)


class CircularQueue:
    """Circular FIFO queue with a fixed capacity"""

    def __init__(self, n: int):
        self.n = n
        self.array = [None] * self.n
        self.front = 0  # index of the first element
        self.rear = 0
        self.size = 0

    def __len__(self) -> int:
        """
        >>> cq = CircularQueue(5)
        >>> len(cq)
        0
        >>> cq.enqueue("A")  # doctest: +ELLIPSIS
        <data_structures.queues.circular_queue.CircularQueue object at ...
        >>> cq.array
        ['A', None, None, None, None]
        >>> len(cq)
        1
        """
        return self.size

    def is_empty(self) -> bool:
        """
        Checks whether the queue is empty or not
        >>> cq = CircularQueue(5)
        >>> cq.is_empty()
        True
        >>> cq.enqueue("A").is_empty()
        False
        """
        return self.size == 0

    def first(self):
        """
        Returns the first element of the queue
        >>> cq = CircularQueue(5)
        >>> cq.first()
        False
        >>> cq.enqueue("A").first()
        'A'
        """
        return False if self.is_empty() else self.array[self.front]

    def enqueue(self, data):
        """
        This function inserts an element at the end of the queue using self.rear value
        as an index.
        >>> cq = CircularQueue(5)
        >>> cq.enqueue("A")  # doctest: +ELLIPSIS
        <data_structures.queues.circular_queue.CircularQueue object at ...
        >>> (cq.size, cq.first())
        (1, 'A')
        >>> cq.enqueue("B")  # doctest: +ELLIPSIS
        <data_structures.queues.circular_queue.CircularQueue object at ...
        >>> cq.array
        ['A', 'B', None, None, None]
        >>> (cq.size, cq.first())
        (2, 'A')
        """
        if self.size >= self.n:
            raise Exception("QUEUE IS FULL")

        self.array[self.rear] = data
        self.rear = (self.rear + 1) % self.n
        self.size += 1
        return self

    def dequeue(self):
        """
        This function removes an element from the queue using on self.front value as an
        index and returns it
        >>> cq = CircularQueue(5)
        >>> cq.dequeue()
        Traceback (most recent call last):
           ...
        Exception: UNDERFLOW
        >>> cq.enqueue("A").enqueue("B").dequeue()
        'A'
        >>> (cq.size, cq.first())
        (1, 'B')
        >>> cq.dequeue()
        'B'
        >>> cq.dequeue()
        Traceback (most recent call last):
           ...
        Exception: UNDERFLOW
        """
        if self.size == 0:
            raise Exception("UNDERFLOW")

        temp = self.array[self.front]
        self.array[self.front] = None
        self.front = (self.front + 1) % self.n
        self.size -= 1
        return temp


================================================
File: data_structures/queues/circular_queue_linked_list.py
================================================
# Implementation of Circular Queue using linked lists
# https://en.wikipedia.org/wiki/Circular_buffer

from __future__ import annotations

from typing import Any


class CircularQueueLinkedList:
    """
    Circular FIFO list with the given capacity (default queue length : 6)

    >>> cq = CircularQueueLinkedList(2)
    >>> cq.enqueue('a')
    >>> cq.enqueue('b')
    >>> cq.enqueue('c')
    Traceback (most recent call last):
       ...
    Exception: Full Queue
    """

    def __init__(self, initial_capacity: int = 6) -> None:
        self.front: Node | None = None
        self.rear: Node | None = None
        self.create_linked_list(initial_capacity)

    def create_linked_list(self, initial_capacity: int) -> None:
        current_node = Node()
        self.front = current_node
        self.rear = current_node
        previous_node = current_node
        for _ in range(1, initial_capacity):
            current_node = Node()
            previous_node.next = current_node
            current_node.prev = previous_node
            previous_node = current_node
        previous_node.next = self.front
        self.front.prev = previous_node

    def is_empty(self) -> bool:
        """
        Checks whether the queue is empty or not
        >>> cq = CircularQueueLinkedList()
        >>> cq.is_empty()
        True
        >>> cq.enqueue('a')
        >>> cq.is_empty()
        False
        >>> cq.dequeue()
        'a'
        >>> cq.is_empty()
        True
        """

        return (
            self.front == self.rear
            and self.front is not None
            and self.front.data is None
        )

    def first(self) -> Any | None:
        """
        Returns the first element of the queue
        >>> cq = CircularQueueLinkedList()
        >>> cq.first()
        Traceback (most recent call last):
           ...
        Exception: Empty Queue
        >>> cq.enqueue('a')
        >>> cq.first()
        'a'
        >>> cq.dequeue()
        'a'
        >>> cq.first()
        Traceback (most recent call last):
           ...
        Exception: Empty Queue
        >>> cq.enqueue('b')
        >>> cq.enqueue('c')
        >>> cq.first()
        'b'
        """
        self.check_can_perform_operation()
        return self.front.data if self.front else None

    def enqueue(self, data: Any) -> None:
        """
        Saves data at the end of the queue

        >>> cq = CircularQueueLinkedList()
        >>> cq.enqueue('a')
        >>> cq.enqueue('b')
        >>> cq.dequeue()
        'a'
        >>> cq.dequeue()
        'b'
        >>> cq.dequeue()
        Traceback (most recent call last):
           ...
        Exception: Empty Queue
        """
        if self.rear is None:
            return

        self.check_is_full()
        if not self.is_empty():
            self.rear = self.rear.next
        if self.rear:
            self.rear.data = data

    def dequeue(self) -> Any:
        """
        Removes and retrieves the first element of the queue

        >>> cq = CircularQueueLinkedList()
        >>> cq.dequeue()
        Traceback (most recent call last):
           ...
        Exception: Empty Queue
        >>> cq.enqueue('a')
        >>> cq.dequeue()
        'a'
        >>> cq.dequeue()
        Traceback (most recent call last):
           ...
        Exception: Empty Queue
        """
        self.check_can_perform_operation()
        if self.rear is None or self.front is None:
            return None
        if self.front == self.rear:
            data = self.front.data
            self.front.data = None
            return data

        old_front = self.front
        self.front = old_front.next
        data = old_front.data
        old_front.data = None
        return data

    def check_can_perform_operation(self) -> None:
        if self.is_empty():
            raise Exception("Empty Queue")

    def check_is_full(self) -> None:
        if self.rear and self.rear.next == self.front:
            raise Exception("Full Queue")


class Node:
    def __init__(self) -> None:
        self.data: Any | None = None
        self.next: Node | None = None
        self.prev: Node | None = None


if __name__ == "__main__":
    import doctest

    doctest.testmod()


================================================
File: data_structures/queues/double_ended_queue.py
================================================
"""
Implementation of double ended queue.
"""

from __future__ import annotations

from collections.abc import Iterable
from dataclasses import dataclass
from typing import Any


class Deque:
    """
    Deque data structure.
    Operations
    ----------
    append(val: Any) -> None
    appendleft(val: Any) -> None
    extend(iterable: Iterable) -> None
    extendleft(iterable: Iterable) -> None
    pop() -> Any
    popleft() -> Any
    Observers
    ---------
    is_empty() -> bool
    Attributes
    ----------
    _front: _Node
        front of the deque a.k.a. the first element
    _back: _Node
        back of the element a.k.a. the last element
    _len: int
        the number of nodes
    """

    __slots__ = ("_back", "_front", "_len")

    @dataclass
    class _Node:
        """
        Representation of a node.
        Contains a value and a pointer to the next node as well as to the previous one.
        """

        val: Any = None
        next_node: Deque._Node | None = None
        prev_node: Deque._Node | None = None

    class _Iterator:
        """
        Helper class for iteration. Will be used to implement iteration.
        Attributes
        ----------
        _cur: _Node
            the current node of the iteration.
        """

        __slots__ = ("_cur",)

        def __init__(self, cur: Deque._Node | None) -> None:
            self._cur = cur

        def __iter__(self) -> Deque._Iterator:
            """
            >>> our_deque = Deque([1, 2, 3])
            >>> iterator = iter(our_deque)
            """
            return self

        def __next__(self) -> Any:
            """
            >>> our_deque = Deque([1, 2, 3])
            >>> iterator = iter(our_deque)
            >>> next(iterator)
            1
            >>> next(iterator)
            2
            >>> next(iterator)
            3
            """
            if self._cur is None:
                # finished iterating
                raise StopIteration
            val = self._cur.val
            self._cur = self._cur.next_node

            return val

    def __init__(self, iterable: Iterable[Any] | None = None) -> None:
        self._front: Any = None
        self._back: Any = None
        self._len: int = 0

        if iterable is not None:
            # append every value to the deque
            for val in iterable:
                self.append(val)

    def append(self, val: Any) -> None:
        """
        Adds val to the end of the deque.
        Time complexity: O(1)
        >>> our_deque_1 = Deque([1, 2, 3])
        >>> our_deque_1.append(4)
        >>> our_deque_1
        [1, 2, 3, 4]
        >>> our_deque_2 = Deque('ab')
        >>> our_deque_2.append('c')
        >>> our_deque_2
        ['a', 'b', 'c']
        >>> from collections import deque
        >>> deque_collections_1 = deque([1, 2, 3])
        >>> deque_collections_1.append(4)
        >>> deque_collections_1
        deque([1, 2, 3, 4])
        >>> deque_collections_2 = deque('ab')
        >>> deque_collections_2.append('c')
        >>> deque_collections_2
        deque(['a', 'b', 'c'])
        >>> list(our_deque_1) == list(deque_collections_1)
        True
        >>> list(our_deque_2) == list(deque_collections_2)
        True
        """
        node = self._Node(val, None, None)
        if self.is_empty():
            # front = back
            self._front = self._back = node
            self._len = 1
        else:
            # connect nodes
            self._back.next_node = node
            node.prev_node = self._back
            self._back = node  # assign new back to the new node

            self._len += 1

            # make sure there were no errors
            assert not self.is_empty(), "Error on appending value."

    def appendleft(self, val: Any) -> None:
        """
        Adds val to the beginning of the deque.
        Time complexity: O(1)
        >>> our_deque_1 = Deque([2, 3])
        >>> our_deque_1.appendleft(1)
        >>> our_deque_1
        [1, 2, 3]
        >>> our_deque_2 = Deque('bc')
        >>> our_deque_2.appendleft('a')
        >>> our_deque_2
        ['a', 'b', 'c']
        >>> from collections import deque
        >>> deque_collections_1 = deque([2, 3])
        >>> deque_collections_1.appendleft(1)
        >>> deque_collections_1
        deque([1, 2, 3])
        >>> deque_collections_2 = deque('bc')
        >>> deque_collections_2.appendleft('a')
        >>> deque_collections_2
        deque(['a', 'b', 'c'])
        >>> list(our_deque_1) == list(deque_collections_1)
        True
        >>> list(our_deque_2) == list(deque_collections_2)
        True
        """
        node = self._Node(val, None, None)
        if self.is_empty():
            # front = back
            self._front = self._back = node
            self._len = 1
        else:
            # connect nodes
            node.next_node = self._front
            self._front.prev_node = node
            self._front = node  # assign new front to the new node

            self._len += 1

            # make sure there were no errors
            assert not self.is_empty(), "Error on appending value."

    def extend(self, iterable: Iterable[Any]) -> None:
        """
        Appends every value of iterable to the end of the deque.
        Time complexity: O(n)
        >>> our_deque_1 = Deque([1, 2, 3])
        >>> our_deque_1.extend([4, 5])
        >>> our_deque_1
        [1, 2, 3, 4, 5]
        >>> our_deque_2 = Deque('ab')
        >>> our_deque_2.extend('cd')
        >>> our_deque_2
        ['a', 'b', 'c', 'd']
        >>> from collections import deque
        >>> deque_collections_1 = deque([1, 2, 3])
        >>> deque_collections_1.extend([4, 5])
        >>> deque_collections_1
        deque([1, 2, 3, 4, 5])
        >>> deque_collections_2 = deque('ab')
        >>> deque_collections_2.extend('cd')
        >>> deque_collections_2
        deque(['a', 'b', 'c', 'd'])
        >>> list(our_deque_1) == list(deque_collections_1)
        True
        >>> list(our_deque_2) == list(deque_collections_2)
        True
        """
        for val in iterable:
            self.append(val)

    def extendleft(self, iterable: Iterable[Any]) -> None:
        """
        Appends every value of iterable to the beginning of the deque.
        Time complexity: O(n)
        >>> our_deque_1 = Deque([1, 2, 3])
        >>> our_deque_1.extendleft([0, -1])
        >>> our_deque_1
        [-1, 0, 1, 2, 3]
        >>> our_deque_2 = Deque('cd')
        >>> our_deque_2.extendleft('ba')
        >>> our_deque_2
        ['a', 'b', 'c', 'd']
        >>> from collections import deque
        >>> deque_collections_1 = deque([1, 2, 3])
        >>> deque_collections_1.extendleft([0, -1])
        >>> deque_collections_1
        deque([-1, 0, 1, 2, 3])
        >>> deque_collections_2 = deque('cd')
        >>> deque_collections_2.extendleft('ba')
        >>> deque_collections_2
        deque(['a', 'b', 'c', 'd'])
        >>> list(our_deque_1) == list(deque_collections_1)
        True
        >>> list(our_deque_2) == list(deque_collections_2)
        True
        """
        for val in iterable:
            self.appendleft(val)

    def pop(self) -> Any:
        """
        Removes the last element of the deque and returns it.
        Time complexity: O(1)
        @returns topop.val: the value of the node to pop.
        >>> our_deque1 = Deque([1])
        >>> our_popped1 = our_deque1.pop()
        >>> our_popped1
        1
        >>> our_deque1
        []

        >>> our_deque2 = Deque([1, 2, 3, 15182])
        >>> our_popped2 = our_deque2.pop()
        >>> our_popped2
        15182
        >>> our_deque2
        [1, 2, 3]

        >>> from collections import deque
        >>> deque_collections = deque([1, 2, 3, 15182])
        >>> collections_popped = deque_collections.pop()
        >>> collections_popped
        15182
        >>> deque_collections
        deque([1, 2, 3])
        >>> list(our_deque2) == list(deque_collections)
        True
        >>> our_popped2 == collections_popped
        True
        """
        # make sure the deque has elements to pop
        assert not self.is_empty(), "Deque is empty."

        topop = self._back
        # if only one element in the queue: point the front and back to None
        # else remove one element from back
        if self._front == self._back:
            self._front = None
            self._back = None
        else:
            self._back = self._back.prev_node  # set new back
            # drop the last node, python will deallocate memory automatically
            self._back.next_node = None

        self._len -= 1

        return topop.val

    def popleft(self) -> Any:
        """
        Removes the first element of the deque and returns it.
        Time complexity: O(1)
        @returns topop.val: the value of the node to pop.
        >>> our_deque1 = Deque([1])
        >>> our_popped1 = our_deque1.pop()
        >>> our_popped1
        1
        >>> our_deque1
        []
        >>> our_deque2 = Deque([15182, 1, 2, 3])
        >>> our_popped2 = our_deque2.popleft()
        >>> our_popped2
        15182
        >>> our_deque2
        [1, 2, 3]
        >>> from collections import deque
        >>> deque_collections = deque([15182, 1, 2, 3])
        >>> collections_popped = deque_collections.popleft()
        >>> collections_popped
        15182
        >>> deque_collections
        deque([1, 2, 3])
        >>> list(our_deque2) == list(deque_collections)
        True
        >>> our_popped2 == collections_popped
        True
        """
        # make sure the deque has elements to pop
        assert not self.is_empty(), "Deque is empty."

        topop = self._front
        # if only one element in the queue: point the front and back to None
        # else remove one element from front
        if self._front == self._back:
            self._front = None
            self._back = None
        else:
            self._front = self._front.next_node  # set new front and drop the first node
            self._front.prev_node = None

        self._len -= 1

        return topop.val

    def is_empty(self) -> bool:
        """
        Checks if the deque is empty.
        Time complexity: O(1)
        >>> our_deque = Deque([1, 2, 3])
        >>> our_deque.is_empty()
        False
        >>> our_empty_deque = Deque()
        >>> our_empty_deque.is_empty()
        True
        >>> from collections import deque
        >>> empty_deque_collections = deque()
        >>> list(our_empty_deque) == list(empty_deque_collections)
        True
        """
        return self._front is None

    def __len__(self) -> int:
        """
        Implements len() function. Returns the length of the deque.
        Time complexity: O(1)
        >>> our_deque = Deque([1, 2, 3])
        >>> len(our_deque)
        3
        >>> our_empty_deque = Deque()
        >>> len(our_empty_deque)
        0
        >>> from collections import deque
        >>> deque_collections = deque([1, 2, 3])
        >>> len(deque_collections)
        3
        >>> empty_deque_collections = deque()
        >>> len(empty_deque_collections)
        0
        >>> len(our_empty_deque) == len(empty_deque_collections)
        True
        """
        return self._len

    def __eq__(self, other: object) -> bool:
        """
        Implements "==" operator. Returns if *self* is equal to *other*.
        Time complexity: O(n)
        >>> our_deque_1 = Deque([1, 2, 3])
        >>> our_deque_2 = Deque([1, 2, 3])
        >>> our_deque_1 == our_deque_2
        True
        >>> our_deque_3 = Deque([1, 2])
        >>> our_deque_1 == our_deque_3
        False
        >>> from collections import deque
        >>> deque_collections_1 = deque([1, 2, 3])
        >>> deque_collections_2 = deque([1, 2, 3])
        >>> deque_collections_1 == deque_collections_2
        True
        >>> deque_collections_3 = deque([1, 2])
        >>> deque_collections_1 == deque_collections_3
        False
        >>> (our_deque_1 == our_deque_2) == (deque_collections_1 == deque_collections_2)
        True
        >>> (our_deque_1 == our_deque_3) == (deque_collections_1 == deque_collections_3)
        True
        """

        if not isinstance(other, Deque):
            return NotImplemented

        me = self._front
        oth = other._front

        # if the length of the dequeues are not the same, they are not equal
        if len(self) != len(other):
            return False

        while me is not None and oth is not None:
            # compare every value
            if me.val != oth.val:
                return False
            me = me.next_node
            oth = oth.next_node

        return True

    def __iter__(self) -> Deque._Iterator:
        """
        Implements iteration.
        Time complexity: O(1)
        >>> our_deque = Deque([1, 2, 3])
        >>> for v in our_deque:
        ...     print(v)
        1
        2
        3
        >>> from collections import deque
        >>> deque_collections = deque([1, 2, 3])
        >>> for v in deque_collections:
        ...     print(v)
        1
        2
        3
        """
        return Deque._Iterator(self._front)

    def __repr__(self) -> str:
        """
        Implements representation of the deque.
        Represents it as a list, with its values between '[' and ']'.
        Time complexity: O(n)
        >>> our_deque = Deque([1, 2, 3])
        >>> our_deque
        [1, 2, 3]
        """
        values_list = []
        aux = self._front
        while aux is not None:
            # append the values in a list to display
            values_list.append(aux.val)
            aux = aux.next_node

        return f"[{', '.join(repr(val) for val in values_list)}]"


if __name__ == "__main__":
    import doctest

    doctest.testmod()
    dq = Deque([3])
    dq.pop()


================================================
File: data_structures/queues/linked_queue.py
================================================
"""A Queue using a linked list like structure"""

from __future__ import annotations

from collections.abc import Iterator
from typing import Any


class Node:
    def __init__(self, data: Any) -> None:
        self.data: Any = data
        self.next: Node | None = None

    def __str__(self) -> str:
        return f"{self.data}"


class LinkedQueue:
    """
    >>> queue = LinkedQueue()
    >>> queue.is_empty()
    True
    >>> queue.put(5)
    >>> queue.put(9)
    >>> queue.put('python')
    >>> queue.is_empty()
    False
    >>> queue.get()
    5
    >>> queue.put('algorithms')
    >>> queue.get()
    9
    >>> queue.get()
    'python'
    >>> queue.get()
    'algorithms'
    >>> queue.is_empty()
    True
    >>> queue.get()
    Traceback (most recent call last):
        ...
    IndexError: dequeue from empty queue
    """

    def __init__(self) -> None:
        self.front: Node | None = None
        self.rear: Node | None = None

    def __iter__(self) -> Iterator[Any]:
        node = self.front
        while node:
            yield node.data
            node = node.next

    def __len__(self) -> int:
        """
        >>> queue = LinkedQueue()
        >>> for i in range(1, 6):
        ...     queue.put(i)
        >>> len(queue)
        5
        >>> for i in range(1, 6):
        ...     assert len(queue) == 6 - i
        ...     _ = queue.get()
        >>> len(queue)
        0
        """
        return len(tuple(iter(self)))

    def __str__(self) -> str:
        """
        >>> queue = LinkedQueue()
        >>> for i in range(1, 4):
        ...     queue.put(i)
        >>> queue.put("Python")
        >>> queue.put(3.14)
        >>> queue.put(True)
        >>> str(queue)
        '1 <- 2 <- 3 <- Python <- 3.14 <- True'
        """
        return " <- ".join(str(item) for item in self)

    def is_empty(self) -> bool:
        """
        >>> queue = LinkedQueue()
        >>> queue.is_empty()
        True
        >>> for i in range(1, 6):
        ...     queue.put(i)
        >>> queue.is_empty()
        False
        """
        return len(self) == 0

    def put(self, item: Any) -> None:
        """
        >>> queue = LinkedQueue()
        >>> queue.get()
        Traceback (most recent call last):
            ...
        IndexError: dequeue from empty queue
        >>> for i in range(1, 6):
        ...     queue.put(i)
        >>> str(queue)
        '1 <- 2 <- 3 <- 4 <- 5'
        """
        node = Node(item)
        if self.is_empty():
            self.front = self.rear = node
        else:
            assert isinstance(self.rear, Node)
            self.rear.next = node
            self.rear = node

    def get(self) -> Any:
        """
        >>> queue = LinkedQueue()
        >>> queue.get()
        Traceback (most recent call last):
            ...
        IndexError: dequeue from empty queue
        >>> queue = LinkedQueue()
        >>> for i in range(1, 6):
        ...     queue.put(i)
        >>> for i in range(1, 6):
        ...     assert queue.get() == i
        >>> len(queue)
        0
        """
        if self.is_empty():
            raise IndexError("dequeue from empty queue")
        assert isinstance(self.front, Node)
        node = self.front
        self.front = self.front.next
        if self.front is None:
            self.rear = None
        return node.data

    def clear(self) -> None:
        """
        >>> queue = LinkedQueue()
        >>> for i in range(1, 6):
        ...     queue.put(i)
        >>> queue.clear()
        >>> len(queue)
        0
        >>> str(queue)
        ''
        """
        self.front = self.rear = None


if __name__ == "__main__":
    from doctest import testmod

    testmod()


================================================
File: data_structures/queues/priority_queue_using_list.py
================================================
"""
Pure Python implementations of a Fixed Priority Queue and an Element Priority Queue
using Python lists.
"""


class OverFlowError(Exception):
    pass


class UnderFlowError(Exception):
    pass


class FixedPriorityQueue:
    """
    Tasks can be added to a Priority Queue at any time and in any order but when Tasks
    are removed then the Task with the highest priority is removed in FIFO order.  In
    code we will use three levels of priority with priority zero Tasks being the most
    urgent (high priority) and priority 2 tasks being the least urgent.

    Examples
    >>> fpq = FixedPriorityQueue()
    >>> fpq.enqueue(0, 10)
    >>> fpq.enqueue(1, 70)
    >>> fpq.enqueue(0, 100)
    >>> fpq.enqueue(2, 1)
    >>> fpq.enqueue(2, 5)
    >>> fpq.enqueue(1, 7)
    >>> fpq.enqueue(2, 4)
    >>> fpq.enqueue(1, 64)
    >>> fpq.enqueue(0, 128)
    >>> print(fpq)
    Priority 0: [10, 100, 128]
    Priority 1: [70, 7, 64]
    Priority 2: [1, 5, 4]
    >>> fpq.dequeue()
    10
    >>> fpq.dequeue()
    100
    >>> fpq.dequeue()
    128
    >>> fpq.dequeue()
    70
    >>> fpq.dequeue()
    7
    >>> print(fpq)
    Priority 0: []
    Priority 1: [64]
    Priority 2: [1, 5, 4]
    >>> fpq.dequeue()
    64
    >>> fpq.dequeue()
    1
    >>> fpq.dequeue()
    5
    >>> fpq.dequeue()
    4
    >>> fpq.dequeue()
    Traceback (most recent call last):
        ...
    data_structures.queues.priority_queue_using_list.UnderFlowError: All queues are empty
    >>> print(fpq)
    Priority 0: []
    Priority 1: []
    Priority 2: []
    """  # noqa: E501

    def __init__(self):
        self.queues = [
            [],
            [],
            [],
        ]

    def enqueue(self, priority: int, data: int) -> None:
        """
        Add an element to a queue based on its priority.
        If the priority is invalid ValueError is raised.
        If the queue is full an OverFlowError is raised.
        """
        try:
            if len(self.queues[priority]) >= 100:
                raise OverflowError("Maximum queue size is 100")
            self.queues[priority].append(data)
        except IndexError:
            raise ValueError("Valid priorities are 0, 1, and 2")

    def dequeue(self) -> int:
        """
        Return the highest priority element in FIFO order.
        If the queue is empty then an under flow exception is raised.
        """
        for queue in self.queues:
            if queue:
                return queue.pop(0)
        raise UnderFlowError("All queues are empty")

    def __str__(self) -> str:
        return "\n".join(f"Priority {i}: {q}" for i, q in enumerate(self.queues))


class ElementPriorityQueue:
    """
    Element Priority Queue is the same as Fixed Priority Queue except that the value of
    the element itself is the priority. The rules for priorities are the same the as
    Fixed Priority Queue.

    >>> epq = ElementPriorityQueue()
    >>> epq.enqueue(10)
    >>> epq.enqueue(70)
    >>> epq.enqueue(4)
    >>> epq.enqueue(1)
    >>> epq.enqueue(5)
    >>> epq.enqueue(7)
    >>> epq.enqueue(4)
    >>> epq.enqueue(64)
    >>> epq.enqueue(128)
    >>> print(epq)
    [10, 70, 4, 1, 5, 7, 4, 64, 128]
    >>> epq.dequeue()
    1
    >>> epq.dequeue()
    4
    >>> epq.dequeue()
    4
    >>> epq.dequeue()
    5
    >>> epq.dequeue()
    7
    >>> epq.dequeue()
    10
    >>> print(epq)
    [70, 64, 128]
    >>> epq.dequeue()
    64
    >>> epq.dequeue()
    70
    >>> epq.dequeue()
    128
    >>> epq.dequeue()
    Traceback (most recent call last):
        ...
    data_structures.queues.priority_queue_using_list.UnderFlowError: The queue is empty
    >>> print(epq)
    []
    """

    def __init__(self):
        self.queue = []

    def enqueue(self, data: int) -> None:
        """
        This function enters the element into the queue
        If the queue is full an Exception is raised saying Over Flow!
        """
        if len(self.queue) == 100:
            raise OverFlowError("Maximum queue size is 100")
        self.queue.append(data)

    def dequeue(self) -> int:
        """
        Return the highest priority element in FIFO order.
        If the queue is empty then an under flow exception is raised.
        """
        if not self.queue:
            raise UnderFlowError("The queue is empty")
        else:
            data = min(self.queue)
            self.queue.remove(data)
            return data

    def __str__(self) -> str:
        """
        Prints all the elements within the Element Priority Queue
        """
        return str(self.queue)


def fixed_priority_queue():
    fpq = FixedPriorityQueue()
    fpq.enqueue(0, 10)
    fpq.enqueue(1, 70)
    fpq.enqueue(0, 100)
    fpq.enqueue(2, 1)
    fpq.enqueue(2, 5)
    fpq.enqueue(1, 7)
    fpq.enqueue(2, 4)
    fpq.enqueue(1, 64)
    fpq.enqueue(0, 128)
    print(fpq)
    print(fpq.dequeue())
    print(fpq.dequeue())
    print(fpq.dequeue())
    print(fpq.dequeue())
    print(fpq.dequeue())
    print(fpq)
    print(fpq.dequeue())
    print(fpq.dequeue())
    print(fpq.dequeue())
    print(fpq.dequeue())
    print(fpq.dequeue())


def element_priority_queue():
    epq = ElementPriorityQueue()
    epq.enqueue(10)
    epq.enqueue(70)
    epq.enqueue(100)
    epq.enqueue(1)
    epq.enqueue(5)
    epq.enqueue(7)
    epq.enqueue(4)
    epq.enqueue(64)
    epq.enqueue(128)
    print(epq)
    print(epq.dequeue())
    print(epq.dequeue())
    print(epq.dequeue())
    print(epq.dequeue())
    print(epq.dequeue())
    print(epq)
    print(epq.dequeue())
    print(epq.dequeue())
    print(epq.dequeue())
    print(epq.dequeue())
    print(epq.dequeue())


if __name__ == "__main__":
    fixed_priority_queue()
    element_priority_queue()


================================================
File: data_structures/queues/queue_by_list.py
================================================
"""Queue represented by a Python list"""

from collections.abc import Iterable
from typing import Generic, TypeVar

_T = TypeVar("_T")


class QueueByList(Generic[_T]):
    def __init__(self, iterable: Iterable[_T] | None = None) -> None:
        """
        >>> QueueByList()
        Queue(())
        >>> QueueByList([10, 20, 30])
        Queue((10, 20, 30))
        >>> QueueByList((i**2 for i in range(1, 4)))
        Queue((1, 4, 9))
        """
        self.entries: list[_T] = list(iterable or [])

    def __len__(self) -> int:
        """
        >>> len(QueueByList())
        0
        >>> from string import ascii_lowercase
        >>> len(QueueByList(ascii_lowercase))
        26
        >>> queue = QueueByList()
        >>> for i in range(1, 11):
        ...     queue.put(i)
        >>> len(queue)
        10
        >>> for i in range(2):
        ...   queue.get()
        1
        2
        >>> len(queue)
        8
        """

        return len(self.entries)

    def __repr__(self) -> str:
        """
        >>> queue = QueueByList()
        >>> queue
        Queue(())
        >>> str(queue)
        'Queue(())'
        >>> queue.put(10)
        >>> queue
        Queue((10,))
        >>> queue.put(20)
        >>> queue.put(30)
        >>> queue
        Queue((10, 20, 30))
        """

        return f"Queue({tuple(self.entries)})"

    def put(self, item: _T) -> None:
        """Put `item` to the Queue

        >>> queue = QueueByList()
        >>> queue.put(10)
        >>> queue.put(20)
        >>> len(queue)
        2
        >>> queue
        Queue((10, 20))
        """

        self.entries.append(item)

    def get(self) -> _T:
        """
        Get `item` from the Queue

        >>> queue = QueueByList((10, 20, 30))
        >>> queue.get()
        10
        >>> queue.put(40)
        >>> queue.get()
        20
        >>> queue.get()
        30
        >>> len(queue)
        1
        >>> queue.get()
        40
        >>> queue.get()
        Traceback (most recent call last):
            ...
        IndexError: Queue is empty
        """

        if not self.entries:
            raise IndexError("Queue is empty")
        return self.entries.pop(0)

    def rotate(self, rotation: int) -> None:
        """Rotate the items of the Queue `rotation` times

        >>> queue = QueueByList([10, 20, 30, 40])
        >>> queue
        Queue((10, 20, 30, 40))
        >>> queue.rotate(1)
        >>> queue
        Queue((20, 30, 40, 10))
        >>> queue.rotate(2)
        >>> queue
        Queue((40, 10, 20, 30))
        """

        put = self.entries.append
        get = self.entries.pop

        for _ in range(rotation):
            put(get(0))

    def get_front(self) -> _T:
        """Get the front item from the Queue

        >>> queue = QueueByList((10, 20, 30))
        >>> queue.get_front()
        10
        >>> queue
        Queue((10, 20, 30))
        >>> queue.get()
        10
        >>> queue.get_front()
        20
        """

        return self.entries[0]


if __name__ == "__main__":
    from doctest import testmod

    testmod()


================================================
File: data_structures/queues/queue_by_two_stacks.py
================================================
"""Queue implementation using two stacks"""

from collections.abc import Iterable
from typing import Generic, TypeVar

_T = TypeVar("_T")


class QueueByTwoStacks(Generic[_T]):
    def __init__(self, iterable: Iterable[_T] | None = None) -> None:
        """
        >>> QueueByTwoStacks()
        Queue(())
        >>> QueueByTwoStacks([10, 20, 30])
        Queue((10, 20, 30))
        >>> QueueByTwoStacks((i**2 for i in range(1, 4)))
        Queue((1, 4, 9))
        """
        self._stack1: list[_T] = list(iterable or [])
        self._stack2: list[_T] = []

    def __len__(self) -> int:
        """
        >>> len(QueueByTwoStacks())
        0
        >>> from string import ascii_lowercase
        >>> len(QueueByTwoStacks(ascii_lowercase))
        26
        >>> queue = QueueByTwoStacks()
        >>> for i in range(1, 11):
        ...     queue.put(i)
        ...
        >>> len(queue)
        10
        >>> for i in range(2):
        ...   queue.get()
        1
        2
        >>> len(queue)
        8
        """

        return len(self._stack1) + len(self._stack2)

    def __repr__(self) -> str:
        """
        >>> queue = QueueByTwoStacks()
        >>> queue
        Queue(())
        >>> str(queue)
        'Queue(())'
        >>> queue.put(10)
        >>> queue
        Queue((10,))
        >>> queue.put(20)
        >>> queue.put(30)
        >>> queue
        Queue((10, 20, 30))
        """
        return f"Queue({tuple(self._stack2[::-1] + self._stack1)})"

    def put(self, item: _T) -> None:
        """
        Put `item` into the Queue

        >>> queue = QueueByTwoStacks()
        >>> queue.put(10)
        >>> queue.put(20)
        >>> len(queue)
        2
        >>> queue
        Queue((10, 20))
        """

        self._stack1.append(item)

    def get(self) -> _T:
        """
        Get `item` from the Queue

        >>> queue = QueueByTwoStacks((10, 20, 30))
        >>> queue.get()
        10
        >>> queue.put(40)
        >>> queue.get()
        20
        >>> queue.get()
        30
        >>> len(queue)
        1
        >>> queue.get()
        40
        >>> queue.get()
        Traceback (most recent call last):
            ...
        IndexError: Queue is empty
        """

        # To reduce number of attribute look-ups in `while` loop.
        stack1_pop = self._stack1.pop
        stack2_append = self._stack2.append

        if not self._stack2:
            while self._stack1:
                stack2_append(stack1_pop())

        if not self._stack2:
            raise IndexError("Queue is empty")
        return self._stack2.pop()


if __name__ == "__main__":
    from doctest import testmod

    testmod()


================================================
File: data_structures/queues/queue_on_pseudo_stack.py
================================================
"""Queue represented by a pseudo stack (represented by a list with pop and append)"""

from typing import Any


class Queue:
    def __init__(self):
        self.stack = []
        self.length = 0

    def __str__(self):
        printed = "<" + str(self.stack)[1:-1] + ">"
        return printed

    """Enqueues {@code item}
    @param item
        item to enqueue"""

    def put(self, item: Any) -> None:
        self.stack.append(item)
        self.length = self.length + 1

    """Dequeues {@code item}
    @requirement: |self.length| > 0
    @return dequeued
        item that was dequeued"""

    def get(self) -> Any:
        self.rotate(1)
        dequeued = self.stack[self.length - 1]
        self.stack = self.stack[:-1]
        self.rotate(self.length - 1)
        self.length = self.length - 1
        return dequeued

    """Rotates the queue {@code rotation} times
    @param rotation
        number of times to rotate queue"""

    def rotate(self, rotation: int) -> None:
        for _ in range(rotation):
            temp = self.stack[0]
            self.stack = self.stack[1:]
            self.put(temp)
            self.length = self.length - 1

    """Reports item at the front of self
    @return item at front of self.stack"""

    def front(self) -> Any:
        front = self.get()
        self.put(front)
        self.rotate(self.length - 1)
        return front

    """Returns the length of this.stack"""

    def size(self) -> int:
        return self.length


================================================
File: data_structures/stacks/balanced_parentheses.py
================================================
from .stack import Stack


def balanced_parentheses(parentheses: str) -> bool:
    """Use a stack to check if a string of parentheses is balanced.
    >>> balanced_parentheses("([]{})")
    True
    >>> balanced_parentheses("[()]{}{[()()]()}")
    True
    >>> balanced_parentheses("[(])")
    False
    >>> balanced_parentheses("1+2*3-4")
    True
    >>> balanced_parentheses("")
    True
    """
    stack: Stack[str] = Stack()
    bracket_pairs = {"(": ")", "[": "]", "{": "}"}
    for bracket in parentheses:
        if bracket in bracket_pairs:
            stack.push(bracket)
        elif bracket in (")", "]", "}") and (
            stack.is_empty() or bracket_pairs[stack.pop()] != bracket
        ):
            return False
    return stack.is_empty()


if __name__ == "__main__":
    from doctest import testmod

    testmod()

    examples = ["((()))", "((())", "(()))"]
    print("Balanced parentheses demonstration:\n")
    for example in examples:
        not_str = "" if balanced_parentheses(example) else "not "
        print(f"{example} is {not_str}balanced")


================================================
File: data_structures/stacks/dijkstras_two_stack_algorithm.py
================================================
"""
Author: Alexander Joslin
GitHub: github.com/echoaj

Explanation:  https://medium.com/@haleesammar/implemented-in-js-dijkstras-2-stack-
              algorithm-for-evaluating-mathematical-expressions-fc0837dae1ea

We can use Dijkstra's two stack algorithm to solve an equation
such as: (5 + ((4 * 2) * (2 + 3)))

THESE ARE THE ALGORITHM'S RULES:
RULE 1: Scan the expression from left to right. When an operand is encountered,
        push it onto the operand stack.

RULE 2: When an operator is encountered in the expression,
        push it onto the operator stack.

RULE 3: When a left parenthesis is encountered in the expression, ignore it.

RULE 4: When a right parenthesis is encountered in the expression,
        pop an operator off the operator stack.  The two operands it must
        operate on must be the last two operands pushed onto the operand stack.
        We therefore pop the operand stack twice, perform the operation,
        and push the result back onto the operand stack so it will be available
        for use as an operand of the next operator popped off the operator stack.

RULE 5: When the entire infix expression has been scanned, the value left on
        the operand stack represents the value of the expression.

NOTE:   It only works with whole numbers.
"""

__author__ = "Alexander Joslin"

import operator as op

from .stack import Stack


def dijkstras_two_stack_algorithm(equation: str) -> int:
    """
    DocTests
    >>> dijkstras_two_stack_algorithm("(5 + 3)")
    8
    >>> dijkstras_two_stack_algorithm("((9 - (2 + 9)) + (8 - 1))")
    5
    >>> dijkstras_two_stack_algorithm("((((3 - 2) - (2 + 3)) + (2 - 4)) + 3)")
    -3

    :param equation: a string
    :return: result: an integer
    """
    operators = {"*": op.mul, "/": op.truediv, "+": op.add, "-": op.sub}

    operand_stack: Stack[int] = Stack()
    operator_stack: Stack[str] = Stack()

    for i in equation:
        if i.isdigit():
            # RULE 1
            operand_stack.push(int(i))
        elif i in operators:
            # RULE 2
            operator_stack.push(i)
        elif i == ")":
            # RULE 4
            opr = operator_stack.peek()
            operator_stack.pop()
            num1 = operand_stack.peek()
            operand_stack.pop()
            num2 = operand_stack.peek()
            operand_stack.pop()

            total = operators[opr](num2, num1)
            operand_stack.push(total)

    # RULE 5
    return operand_stack.peek()


if __name__ == "__main__":
    equation = "(5 + ((4 * 2) * (2 + 3)))"
    # answer = 45
    print(f"{equation} = {dijkstras_two_stack_algorithm(equation)}")


================================================
File: data_structures/stacks/infix_to_postfix_conversion.py
================================================
"""
https://en.wikipedia.org/wiki/Infix_notation
https://en.wikipedia.org/wiki/Reverse_Polish_notation
https://en.wikipedia.org/wiki/Shunting-yard_algorithm
"""

from typing import Literal

from .balanced_parentheses import balanced_parentheses
from .stack import Stack

PRECEDENCES: dict[str, int] = {
    "+": 1,
    "-": 1,
    "*": 2,
    "/": 2,
    "^": 3,
}
ASSOCIATIVITIES: dict[str, Literal["LR", "RL"]] = {
    "+": "LR",
    "-": "LR",
    "*": "LR",
    "/": "LR",
    "^": "RL",
}


def precedence(char: str) -> int:
    """
    Return integer value representing an operator's precedence, or
    order of operation.
    https://en.wikipedia.org/wiki/Order_of_operations
    """
    return PRECEDENCES.get(char, -1)


def associativity(char: str) -> Literal["LR", "RL"]:
    """
    Return the associativity of the operator `char`.
    https://en.wikipedia.org/wiki/Operator_associativity
    """
    return ASSOCIATIVITIES[char]


def infix_to_postfix(expression_str: str) -> str:
    """
    >>> infix_to_postfix("(1*(2+3)+4))")
    Traceback (most recent call last):
        ...
    ValueError: Mismatched parentheses
    >>> infix_to_postfix("")
    ''
    >>> infix_to_postfix("3+2")
    '3 2 +'
    >>> infix_to_postfix("(3+4)*5-6")
    '3 4 + 5 * 6 -'
    >>> infix_to_postfix("(1+2)*3/4-5")
    '1 2 + 3 * 4 / 5 -'
    >>> infix_to_postfix("a+b*c+(d*e+f)*g")
    'a b c * + d e * f + g * +'
    >>> infix_to_postfix("x^y/(5*z)+2")
    'x y ^ 5 z * / 2 +'
    >>> infix_to_postfix("2^3^2")
    '2 3 2 ^ ^'
    """
    if not balanced_parentheses(expression_str):
        raise ValueError("Mismatched parentheses")
    stack: Stack[str] = Stack()
    postfix = []
    for char in expression_str:
        if char.isalpha() or char.isdigit():
            postfix.append(char)
        elif char == "(":
            stack.push(char)
        elif char == ")":
            while not stack.is_empty() and stack.peek() != "(":
                postfix.append(stack.pop())
            stack.pop()
        else:
            while True:
                if stack.is_empty():
                    stack.push(char)
                    break

                char_precedence = precedence(char)
                tos_precedence = precedence(stack.peek())

                if char_precedence > tos_precedence:
                    stack.push(char)
                    break
                if char_precedence < tos_precedence:
                    postfix.append(stack.pop())
                    continue
                # Precedences are equal
                if associativity(char) == "RL":
                    stack.push(char)
                    break
                postfix.append(stack.pop())

    while not stack.is_empty():
        postfix.append(stack.pop())
    return " ".join(postfix)


if __name__ == "__main__":
    from doctest import testmod

    testmod()
    expression = "a+b*(c^d-e)^(f+g*h)-i"

    print("Infix to Postfix Notation demonstration:\n")
    print("Infix notation: " + expression)
    print("Postfix notation: " + infix_to_postfix(expression))


================================================
File: data_structures/stacks/infix_to_prefix_conversion.py
================================================
"""
Output:

Enter an Infix Equation = a + b ^c
 Symbol  |  Stack  | Postfix
----------------------------
   c     |         | c
   ^     | ^       | c
   b     | ^       | cb
   +     | +       | cb^
   a     | +       | cb^a
         |         | cb^a+

         a+b^c (Infix) ->  +a^bc (Prefix)
"""


def infix_2_postfix(infix: str) -> str:
    """
    >>> infix_2_postfix("a+b^c")  # doctest: +NORMALIZE_WHITESPACE
     Symbol  |  Stack  | Postfix
    ----------------------------
       a     |         | a
       +     | +       | a
       b     | +       | ab
       ^     | +^      | ab
       c     | +^      | abc
             | +       | abc^
             |         | abc^+
    'abc^+'

    >>> infix_2_postfix("1*((-a)*2+b)")   # doctest: +NORMALIZE_WHITESPACE
      Symbol  |    Stack     |   Postfix
    -------------------------------------------
       1     |              | 1
       *     | *            | 1
       (     | *(           | 1
       (     | *((          | 1
       -     | *((-         | 1
       a     | *((-         | 1a
       )     | *(           | 1a-
       *     | *(*          | 1a-
       2     | *(*          | 1a-2
       +     | *(+          | 1a-2*
       b     | *(+          | 1a-2*b
       )     | *            | 1a-2*b+
             |              | 1a-2*b+*
    '1a-2*b+*'

    >>> infix_2_postfix("")
     Symbol  |  Stack  | Postfix
    ----------------------------
    ''

    >>> infix_2_postfix("(()")
    Traceback (most recent call last):
        ...
    ValueError: invalid expression

    >>> infix_2_postfix("())")
    Traceback (most recent call last):
        ...
    IndexError: list index out of range
    """
    stack = []
    post_fix = []
    priority = {
        "^": 3,
        "*": 2,
        "/": 2,
        "%": 2,
        "+": 1,
        "-": 1,
    }  # Priority of each operator
    print_width = max(len(infix), 7)

    # Print table header for output
    print(
        "Symbol".center(8),
        "Stack".center(print_width),
        "Postfix".center(print_width),
        sep=" | ",
    )
    print("-" * (print_width * 3 + 7))

    for x in infix:
        if x.isalpha() or x.isdigit():
            post_fix.append(x)  # if x is Alphabet / Digit, add it to Postfix
        elif x == "(":
            stack.append(x)  # if x is "(" push to Stack
        elif x == ")":  # if x is ")" pop stack until "(" is encountered
            if len(stack) == 0:  # close bracket without open bracket
                raise IndexError("list index out of range")

            while stack[-1] != "(":
                post_fix.append(stack.pop())  # Pop stack & add the content to Postfix
            stack.pop()
        elif len(stack) == 0:
            stack.append(x)  # If stack is empty, push x to stack
        else:  # while priority of x is not > priority of element in the stack
            while stack and stack[-1] != "(" and priority[x] <= priority[stack[-1]]:
                post_fix.append(stack.pop())  # pop stack & add to Postfix
            stack.append(x)  # push x to stack

        print(
            x.center(8),
            ("".join(stack)).ljust(print_width),
            ("".join(post_fix)).ljust(print_width),
            sep=" | ",
        )  # Output in tabular format

    while len(stack) > 0:  # while stack is not empty
        if stack[-1] == "(":  # open bracket with no close bracket
            raise ValueError("invalid expression")

        post_fix.append(stack.pop())  # pop stack & add to Postfix
        print(
            " ".center(8),
            ("".join(stack)).ljust(print_width),
            ("".join(post_fix)).ljust(print_width),
            sep=" | ",
        )  # Output in tabular format

    return "".join(post_fix)  # return Postfix as str


def infix_2_prefix(infix: str) -> str:
    """
    >>> infix_2_prefix("a+b^c")  # doctest: +NORMALIZE_WHITESPACE
     Symbol  |  Stack  | Postfix
    ----------------------------
       c     |         | c
       ^     | ^       | c
       b     | ^       | cb
       +     | +       | cb^
       a     | +       | cb^a
             |         | cb^a+
    '+a^bc'

    >>> infix_2_prefix("1*((-a)*2+b)") # doctest: +NORMALIZE_WHITESPACE
     Symbol  |    Stack     |   Postfix
    -------------------------------------------
       (     | (            |
       b     | (            | b
       +     | (+           | b
       2     | (+           | b2
       *     | (+*          | b2
       (     | (+*(         | b2
       a     | (+*(         | b2a
       -     | (+*(-        | b2a
       )     | (+*          | b2a-
       )     |              | b2a-*+
       *     | *            | b2a-*+
       1     | *            | b2a-*+1
             |              | b2a-*+1*
    '*1+*-a2b'

    >>> infix_2_prefix('')
     Symbol  |  Stack  | Postfix
    ----------------------------
    ''

    >>> infix_2_prefix('(()')
    Traceback (most recent call last):
        ...
    IndexError: list index out of range

    >>> infix_2_prefix('())')
    Traceback (most recent call last):
        ...
    ValueError: invalid expression
    """
    reversed_infix = list(infix[::-1])  # reverse the infix equation

    for i in range(len(reversed_infix)):
        if reversed_infix[i] == "(":
            reversed_infix[i] = ")"  # change "(" to ")"
        elif reversed_infix[i] == ")":
            reversed_infix[i] = "("  # change ")" to "("

    # call infix_2_postfix on Infix, return reverse of Postfix
    return (infix_2_postfix("".join(reversed_infix)))[::-1]


if __name__ == "__main__":
    from doctest import testmod

    testmod()

    Infix = input("\nEnter an Infix Equation = ")  # Input an Infix equation
    Infix = "".join(Infix.split())  # Remove spaces from the input
    print("\n\t", Infix, "(Infix) -> ", infix_2_prefix(Infix), "(Prefix)")


================================================
File: data_structures/stacks/lexicographical_numbers.py
================================================
from collections.abc import Iterator


def lexical_order(max_number: int) -> Iterator[int]:
    """
    Generate numbers in lexical order from 1 to max_number.

    >>> " ".join(map(str, lexical_order(13)))
    '1 10 11 12 13 2 3 4 5 6 7 8 9'
    >>> list(lexical_order(1))
    [1]
    >>> " ".join(map(str, lexical_order(20)))
    '1 10 11 12 13 14 15 16 17 18 19 2 20 3 4 5 6 7 8 9'
    >>> " ".join(map(str, lexical_order(25)))
    '1 10 11 12 13 14 15 16 17 18 19 2 20 21 22 23 24 25 3 4 5 6 7 8 9'
    >>> list(lexical_order(12))
    [1, 10, 11, 12, 2, 3, 4, 5, 6, 7, 8, 9]
    """

    stack = [1]

    while stack:
        num = stack.pop()
        if num > max_number:
            continue

        yield num
        if (num % 10) != 9:
            stack.append(num + 1)

        stack.append(num * 10)


if __name__ == "__main__":
    from doctest import testmod

    testmod()
    print(f"Numbers from 1 to 25 in lexical order: {list(lexical_order(26))}")


================================================
File: data_structures/stacks/next_greater_element.py
================================================
from __future__ import annotations

arr = [-10, -5, 0, 5, 5.1, 11, 13, 21, 3, 4, -21, -10, -5, -1, 0]
expect = [-5, 0, 5, 5.1, 11, 13, 21, -1, 4, -1, -10, -5, -1, 0, -1]


def next_greatest_element_slow(arr: list[float]) -> list[float]:
    """
    Get the Next Greatest Element (NGE) for each element in the array
    by checking all subsequent elements to find the next greater one.

    This is a brute-force implementation, and it has a time complexity
    of O(n^2), where n is the size of the array.

    Args:
        arr: List of numbers for which the NGE is calculated.

    Returns:
        List containing the next greatest elements. If no
        greater element is found, -1 is placed in the result.

    Example:
    >>> next_greatest_element_slow(arr) == expect
    True
    """

    result = []
    arr_size = len(arr)

    for i in range(arr_size):
        next_element: float = -1
        for j in range(i + 1, arr_size):
            if arr[i] < arr[j]:
                next_element = arr[j]
                break
        result.append(next_element)
    return result


def next_greatest_element_fast(arr: list[float]) -> list[float]:
    """
    Find the Next Greatest Element (NGE) for each element in the array
    using a more readable approach. This implementation utilizes
    enumerate() for the outer loop and slicing for the inner loop.

    While this improves readability over next_greatest_element_slow(),
    it still has a time complexity of O(n^2).

    Args:
        arr: List of numbers for which the NGE is calculated.

    Returns:
        List containing the next greatest elements. If no
        greater element is found, -1 is placed in the result.

    Example:
    >>> next_greatest_element_fast(arr) == expect
    True
    """
    result = []
    for i, outer in enumerate(arr):
        next_item: float = -1
        for inner in arr[i + 1 :]:
            if outer < inner:
                next_item = inner
                break
        result.append(next_item)
    return result


def next_greatest_element(arr: list[float]) -> list[float]:
    """
    Efficient solution to find the Next Greatest Element (NGE) for all elements
    using a stack. The time complexity is reduced to O(n), making it suitable
    for larger arrays.

    The stack keeps track of elements for which the next greater element hasn't
    been found yet. By iterating through the array in reverse (from the last
    element to the first), the stack is used to efficiently determine the next
    greatest element for each element.

    Args:
        arr: List of numbers for which the NGE is calculated.

    Returns:
        List containing the next greatest elements. If no
        greater element is found, -1 is placed in the result.

    Example:
    >>> next_greatest_element(arr) == expect
    True
    """
    arr_size = len(arr)
    stack: list[float] = []
    result: list[float] = [-1] * arr_size

    for index in reversed(range(arr_size)):
        if stack:
            while stack[-1] <= arr[index]:
                stack.pop()
                if not stack:
                    break
        if stack:
            result[index] = stack[-1]
        stack.append(arr[index])
    return result


if __name__ == "__main__":
    from doctest import testmod
    from timeit import timeit

    testmod()
    print(next_greatest_element_slow(arr))
    print(next_greatest_element_fast(arr))
    print(next_greatest_element(arr))

    setup = (
        "from __main__ import arr, next_greatest_element_slow, "
        "next_greatest_element_fast, next_greatest_element"
    )
    print(
        "next_greatest_element_slow():",
        timeit("next_greatest_element_slow(arr)", setup=setup),
    )
    print(
        "next_greatest_element_fast():",
        timeit("next_greatest_element_fast(arr)", setup=setup),
    )
    print(
        "     next_greatest_element():",
        timeit("next_greatest_element(arr)", setup=setup),
    )


================================================
File: data_structures/stacks/postfix_evaluation.py
================================================
"""
Reverse Polish Nation is also known as Polish postfix notation or simply postfix
notation.
https://en.wikipedia.org/wiki/Reverse_Polish_notation
Classic examples of simple stack implementations.
Valid operators are +, -, *, /.
Each operand may be an integer or another expression.

Output:

Enter a Postfix Equation (space separated) = 5 6 9 * +
 Symbol  |    Action    | Stack
-----------------------------------
       5 | push(5)      | 5
       6 | push(6)      | 5,6
       9 | push(9)      | 5,6,9
         | pop(9)       | 5,6
         | pop(6)       | 5
       * | push(6*9)    | 5,54
         | pop(54)      | 5
         | pop(5)       |
       + | push(5+54)   | 59

        Result =  59
"""

# Defining valid unary operator symbols
UNARY_OP_SYMBOLS = ("-", "+")

# operators & their respective operation
OPERATORS = {
    "^": lambda p, q: p**q,
    "*": lambda p, q: p * q,
    "/": lambda p, q: p / q,
    "+": lambda p, q: p + q,
    "-": lambda p, q: p - q,
}


def parse_token(token: str | float) -> float | str:
    """
    Converts the given data to the appropriate number if it is indeed a number, else
    returns the data as it is with a False flag. This function also serves as a check
    of whether the input is a number or not.

    Parameters
    ----------
    token: The data that needs to be converted to the appropriate operator or number.

    Returns
    -------
    float or str
        Returns a float if `token` is a number or a str if `token` is an operator
    """
    if token in OPERATORS:
        return token
    try:
        return float(token)
    except ValueError:
        msg = f"{token} is neither a number nor a valid operator"
        raise ValueError(msg)


def evaluate(post_fix: list[str], verbose: bool = False) -> float:
    """
    Evaluate postfix expression using a stack.
    >>> evaluate(["0"])
    0.0
    >>> evaluate(["-0"])
    -0.0
    >>> evaluate(["1"])
    1.0
    >>> evaluate(["-1"])
    -1.0
    >>> evaluate(["-1.1"])
    -1.1
    >>> evaluate(["2", "1", "+", "3", "*"])
    9.0
    >>> evaluate(["2", "1.9", "+", "3", "*"])
    11.7
    >>> evaluate(["2", "-1.9", "+", "3", "*"])
    0.30000000000000027
    >>> evaluate(["4", "13", "5", "/", "+"])
    6.6
    >>> evaluate(["2", "-", "3", "+"])
    1.0
    >>> evaluate(["-4", "5", "*", "6", "-"])
    -26.0
    >>> evaluate([])
    0
    >>> evaluate(["4", "-", "6", "7", "/", "9", "8"])
    Traceback (most recent call last):
    ...
    ArithmeticError: Input is not a valid postfix expression

    Parameters
    ----------
    post_fix:
        The postfix expression is tokenized into operators and operands and stored
        as a Python list

    verbose:
        Display stack contents while evaluating the expression if verbose is True

    Returns
    -------
    float
        The evaluated value
    """
    if not post_fix:
        return 0
    # Checking the list to find out whether the postfix expression is valid
    valid_expression = [parse_token(token) for token in post_fix]
    if verbose:
        # print table header
        print("Symbol".center(8), "Action".center(12), "Stack", sep=" | ")
        print("-" * (30 + len(post_fix)))
    stack = []
    for x in valid_expression:
        if x not in OPERATORS:
            stack.append(x)  # append x to stack
            if verbose:
                # output in tabular format
                print(
                    f"{x}".rjust(8),
                    f"push({x})".ljust(12),
                    stack,
                    sep=" | ",
                )
            continue
        # If x is operator
        # If only 1 value is inside the stack and + or - is encountered
        # then this is unary + or - case
        if x in UNARY_OP_SYMBOLS and len(stack) < 2:
            b = stack.pop()  # pop stack
            if x == "-":
                b *= -1  # negate b
            stack.append(b)
            if verbose:
                # output in tabular format
                print(
                    "".rjust(8),
                    f"pop({b})".ljust(12),
                    stack,
                    sep=" | ",
                )
                print(
                    str(x).rjust(8),
                    f"push({x}{b})".ljust(12),
                    stack,
                    sep=" | ",
                )
            continue
        b = stack.pop()  # pop stack
        if verbose:
            # output in tabular format
            print(
                "".rjust(8),
                f"pop({b})".ljust(12),
                stack,
                sep=" | ",
            )

        a = stack.pop()  # pop stack
        if verbose:
            # output in tabular format
            print(
                "".rjust(8),
                f"pop({a})".ljust(12),
                stack,
                sep=" | ",
            )
        # evaluate the 2 values popped from stack & push result to stack
        stack.append(OPERATORS[x](a, b))  # type: ignore[index]
        if verbose:
            # output in tabular format
            print(
                f"{x}".rjust(8),
                f"push({a}{x}{b})".ljust(12),
                stack,
                sep=" | ",
            )
    # If everything is executed correctly, the stack will contain
    # only one element which is the result
    if len(stack) != 1:
        raise ArithmeticError("Input is not a valid postfix expression")
    return float(stack[0])


if __name__ == "__main__":
    # Create a loop so that the user can evaluate postfix expressions multiple times
    while True:
        expression = input("Enter a Postfix Expression (space separated): ").split(" ")
        prompt = "Do you want to see stack contents while evaluating? [y/N]: "
        verbose = input(prompt).strip().lower() == "y"
        output = evaluate(expression, verbose)
        print("Result = ", output)
        prompt = "Do you want to enter another expression? [y/N]: "
        if input(prompt).strip().lower() != "y":
            break


================================================
File: data_structures/stacks/prefix_evaluation.py
================================================
"""
Python3 program to evaluate a prefix expression.
"""

calc = {
    "+": lambda x, y: x + y,
    "-": lambda x, y: x - y,
    "*": lambda x, y: x * y,
    "/": lambda x, y: x / y,
}


def is_operand(c):
    """
    Return True if the given char c is an operand, e.g. it is a number

    >>> is_operand("1")
    True
    >>> is_operand("+")
    False
    """
    return c.isdigit()


def evaluate(expression):
    """
    Evaluate a given expression in prefix notation.
    Asserts that the given expression is valid.

    >>> evaluate("+ 9 * 2 6")
    21
    >>> evaluate("/ * 10 2 + 4 1 ")
    4.0
    """
    stack = []

    # iterate over the string in reverse order
    for c in expression.split()[::-1]:
        # push operand to stack
        if is_operand(c):
            stack.append(int(c))

        else:
            # pop values from stack can calculate the result
            # push the result onto the stack again
            o1 = stack.pop()
            o2 = stack.pop()
            stack.append(calc[c](o1, o2))

    return stack.pop()


# Driver code
if __name__ == "__main__":
    test_expression = "+ 9 * 2 6"
    print(evaluate(test_expression))

    test_expression = "/ * 10 2 + 4 1 "
    print(evaluate(test_expression))


================================================
File: data_structures/stacks/stack.py
================================================
from __future__ import annotations

from typing import Generic, TypeVar

T = TypeVar("T")


class StackOverflowError(BaseException):
    pass


class StackUnderflowError(BaseException):
    pass


class Stack(Generic[T]):
    """A stack is an abstract data type that serves as a collection of
    elements with two principal operations: push() and pop(). push() adds an
    element to the top of the stack, and pop() removes an element from the top
    of a stack. The order in which elements come off of a stack are
    Last In, First Out (LIFO).
    https://en.wikipedia.org/wiki/Stack_(abstract_data_type)
    """

    def __init__(self, limit: int = 10):
        self.stack: list[T] = []
        self.limit = limit

    def __bool__(self) -> bool:
        return bool(self.stack)

    def __str__(self) -> str:
        return str(self.stack)

    def push(self, data: T) -> None:
        """
        Push an element to the top of the stack.

        >>> S = Stack(2) # stack size = 2
        >>> S.push(10)
        >>> S.push(20)
        >>> print(S)
        [10, 20]

        >>> S = Stack(1) # stack size = 1
        >>> S.push(10)
        >>> S.push(20)
        Traceback (most recent call last):
        ...
        data_structures.stacks.stack.StackOverflowError

        """
        if len(self.stack) >= self.limit:
            raise StackOverflowError
        self.stack.append(data)

    def pop(self) -> T:
        """
        Pop an element off of the top of the stack.

        >>> S = Stack()
        >>> S.push(-5)
        >>> S.push(10)
        >>> S.pop()
        10

        >>> Stack().pop()
        Traceback (most recent call last):
            ...
        data_structures.stacks.stack.StackUnderflowError
        """
        if not self.stack:
            raise StackUnderflowError
        return self.stack.pop()

    def peek(self) -> T:
        """
        Peek at the top-most element of the stack.

        >>> S = Stack()
        >>> S.push(-5)
        >>> S.push(10)
        >>> S.peek()
        10

        >>> Stack().peek()
        Traceback (most recent call last):
            ...
        data_structures.stacks.stack.StackUnderflowError
        """
        if not self.stack:
            raise StackUnderflowError
        return self.stack[-1]

    def is_empty(self) -> bool:
        """
        Check if a stack is empty.

        >>> S = Stack()
        >>> S.is_empty()
        True

        >>> S = Stack()
        >>> S.push(10)
        >>> S.is_empty()
        False
        """
        return not bool(self.stack)

    def is_full(self) -> bool:
        """
        >>> S = Stack()
        >>> S.is_full()
        False

        >>> S = Stack(1)
        >>> S.push(10)
        >>> S.is_full()
        True
        """
        return self.size() == self.limit

    def size(self) -> int:
        """
        Return the size of the stack.

        >>> S = Stack(3)
        >>> S.size()
        0

        >>> S = Stack(3)
        >>> S.push(10)
        >>> S.size()
        1

        >>> S = Stack(3)
        >>> S.push(10)
        >>> S.push(20)
        >>> S.size()
        2
        """
        return len(self.stack)

    def __contains__(self, item: T) -> bool:
        """
        Check if item is in stack

        >>> S = Stack(3)
        >>> S.push(10)
        >>> 10 in S
        True

        >>> S = Stack(3)
        >>> S.push(10)
        >>> 20 in S
        False
        """
        return item in self.stack


def test_stack() -> None:
    """
    >>> test_stack()
    """
    stack: Stack[int] = Stack(10)
    assert bool(stack) is False
    assert stack.is_empty() is True
    assert stack.is_full() is False
    assert str(stack) == "[]"

    try:
        _ = stack.pop()
        raise AssertionError  # This should not happen
    except StackUnderflowError:
        assert True  # This should happen

    try:
        _ = stack.peek()
        raise AssertionError  # This should not happen
    except StackUnderflowError:
        assert True  # This should happen

    for i in range(10):
        assert stack.size() == i
        stack.push(i)

    assert bool(stack)
    assert not stack.is_empty()
    assert stack.is_full()
    assert str(stack) == str(list(range(10)))
    assert stack.pop() == 9
    assert stack.peek() == 8

    stack.push(100)
    assert str(stack) == str([0, 1, 2, 3, 4, 5, 6, 7, 8, 100])

    try:
        stack.push(200)
        raise AssertionError  # This should not happen
    except StackOverflowError:
        assert True  # This should happen

    assert not stack.is_empty()
    assert stack.size() == 10

    assert 5 in stack
    assert 55 not in stack


if __name__ == "__main__":
    test_stack()

    import doctest

    doctest.testmod()


================================================
File: data_structures/stacks/stack_using_two_queues.py
================================================
from __future__ import annotations

from collections import deque
from dataclasses import dataclass, field


@dataclass
class StackWithQueues:
    """
    https://www.geeksforgeeks.org/implement-stack-using-queue/

    >>> stack = StackWithQueues()
    >>> stack.push(1)
    >>> stack.push(2)
    >>> stack.push(3)
    >>> stack.peek()
    3
    >>> stack.pop()
    3
    >>> stack.peek()
    2
    >>> stack.pop()
    2
    >>> stack.pop()
    1
    >>> stack.peek() is None
    True
    >>> stack.pop()
    Traceback (most recent call last):
        ...
    IndexError: pop from an empty deque
    """

    main_queue: deque[int] = field(default_factory=deque)
    temp_queue: deque[int] = field(default_factory=deque)

    def push(self, item: int) -> None:
        self.temp_queue.append(item)
        while self.main_queue:
            self.temp_queue.append(self.main_queue.popleft())
        self.main_queue, self.temp_queue = self.temp_queue, self.main_queue

    def pop(self) -> int:
        return self.main_queue.popleft()

    def peek(self) -> int | None:
        return self.main_queue[0] if self.main_queue else None


if __name__ == "__main__":
    import doctest

    doctest.testmod()

    stack: StackWithQueues | None = StackWithQueues()
    while stack:
        print("\nChoose operation:")
        print("1. Push")
        print("2. Pop")
        print("3. Peek")
        print("4. Quit")

        choice = input("Enter choice (1/2/3/4): ")

        if choice == "1":
            element = int(input("Enter an integer to push: ").strip())
            stack.push(element)
            print(f"{element} pushed onto the stack.")
        elif choice == "2":
            popped_element = stack.pop()
            if popped_element is not None:
                print(f"Popped element: {popped_element}")
            else:
                print("Stack is empty.")
        elif choice == "3":
            peeked_element = stack.peek()
            if peeked_element is not None:
                print(f"Top element: {peeked_element}")
            else:
                print("Stack is empty.")
        elif choice == "4":
            del stack
            stack = None
        else:
            print("Invalid choice. Please try again.")


================================================
File: data_structures/stacks/stack_with_doubly_linked_list.py
================================================
# A complete working Python program to demonstrate all
# stack operations using a doubly linked list

from __future__ import annotations

from typing import Generic, TypeVar

T = TypeVar("T")


class Node(Generic[T]):
    def __init__(self, data: T):
        self.data = data  # Assign data
        self.next: Node[T] | None = None  # Initialize next as null
        self.prev: Node[T] | None = None  # Initialize prev as null


class Stack(Generic[T]):
    """
    >>> stack = Stack()
    >>> stack.is_empty()
    True
    >>> stack.print_stack()
    stack elements are:
    >>> for i in range(4):
    ...     stack.push(i)
    ...
    >>> stack.is_empty()
    False
    >>> stack.print_stack()
    stack elements are:
    3->2->1->0->
    >>> stack.top()
    3
    >>> len(stack)
    4
    >>> stack.pop()
    3
    >>> stack.print_stack()
    stack elements are:
    2->1->0->
    """

    def __init__(self) -> None:
        self.head: Node[T] | None = None

    def push(self, data: T) -> None:
        """add a Node to the stack"""
        if self.head is None:
            self.head = Node(data)
        else:
            new_node = Node(data)
            self.head.prev = new_node
            new_node.next = self.head
            new_node.prev = None
            self.head = new_node

    def pop(self) -> T | None:
        """pop the top element off the stack"""
        if self.head is None:
            return None
        else:
            assert self.head is not None
            temp = self.head.data
            self.head = self.head.next
            if self.head is not None:
                self.head.prev = None
            return temp

    def top(self) -> T | None:
        """return the top element of the stack"""
        return self.head.data if self.head is not None else None

    def __len__(self) -> int:
        temp = self.head
        count = 0
        while temp is not None:
            count += 1
            temp = temp.next
        return count

    def is_empty(self) -> bool:
        return self.head is None

    def print_stack(self) -> None:
        print("stack elements are:")
        temp = self.head
        while temp is not None:
            print(temp.data, end="->")
            temp = temp.next


# Code execution starts here
if __name__ == "__main__":
    # Start with the empty stack
    stack: Stack[int] = Stack()

    # Insert 4 at the beginning. So stack becomes 4->None
    print("Stack operations using Doubly LinkedList")
    stack.push(4)

    # Insert 5 at the beginning. So stack becomes 4->5->None
    stack.push(5)

    # Insert 6 at the beginning. So stack becomes 4->5->6->None
    stack.push(6)

    # Insert 7 at the beginning. So stack becomes 4->5->6->7->None
    stack.push(7)

    # Print the stack
    stack.print_stack()

    # Print the top element
    print("\nTop element is ", stack.top())

    # Print the stack size
    print("Size of the stack is ", len(stack))

    # pop the top element
    stack.pop()

    # pop the top element
    stack.pop()

    # two elements have now been popped off
    stack.print_stack()

    # Print True if the stack is empty else False
    print("\nstack is empty:", stack.is_empty())


================================================
File: data_structures/stacks/stack_with_singly_linked_list.py
================================================
"""A Stack using a linked list like structure"""

from __future__ import annotations

from collections.abc import Iterator
from typing import Generic, TypeVar

T = TypeVar("T")


class Node(Generic[T]):
    def __init__(self, data: T):
        self.data = data
        self.next: Node[T] | None = None

    def __str__(self) -> str:
        return f"{self.data}"


class LinkedStack(Generic[T]):
    """
    Linked List Stack implementing push (to top),
    pop (from top) and is_empty

    >>> stack = LinkedStack()
    >>> stack.is_empty()
    True
    >>> stack.push(5)
    >>> stack.push(9)
    >>> stack.push('python')
    >>> stack.is_empty()
    False
    >>> stack.pop()
    'python'
    >>> stack.push('algorithms')
    >>> stack.pop()
    'algorithms'
    >>> stack.pop()
    9
    >>> stack.pop()
    5
    >>> stack.is_empty()
    True
    >>> stack.pop()
    Traceback (most recent call last):
        ...
    IndexError: pop from empty stack
    """

    def __init__(self) -> None:
        self.top: Node[T] | None = None

    def __iter__(self) -> Iterator[T]:
        node = self.top
        while node:
            yield node.data
            node = node.next

    def __str__(self) -> str:
        """
        >>> stack = LinkedStack()
        >>> stack.push("c")
        >>> stack.push("b")
        >>> stack.push("a")
        >>> str(stack)
        'a->b->c'
        """
        return "->".join([str(item) for item in self])

    def __len__(self) -> int:
        """
        >>> stack = LinkedStack()
        >>> len(stack) == 0
        True
        >>> stack.push("c")
        >>> stack.push("b")
        >>> stack.push("a")
        >>> len(stack) == 3
        True
        """
        return len(tuple(iter(self)))

    def is_empty(self) -> bool:
        """
        >>> stack = LinkedStack()
        >>> stack.is_empty()
        True
        >>> stack.push(1)
        >>> stack.is_empty()
        False
        """
        return self.top is None

    def push(self, item: T) -> None:
        """
        >>> stack = LinkedStack()
        >>> stack.push("Python")
        >>> stack.push("Java")
        >>> stack.push("C")
        >>> str(stack)
        'C->Java->Python'
        """
        node = Node(item)
        if not self.is_empty():
            node.next = self.top
        self.top = node

    def pop(self) -> T:
        """
        >>> stack = LinkedStack()
        >>> stack.pop()
        Traceback (most recent call last):
            ...
        IndexError: pop from empty stack
        >>> stack.push("c")
        >>> stack.push("b")
        >>> stack.push("a")
        >>> stack.pop() == 'a'
        True
        >>> stack.pop() == 'b'
        True
        >>> stack.pop() == 'c'
        True
        """
        if self.is_empty():
            raise IndexError("pop from empty stack")
        assert isinstance(self.top, Node)
        pop_node = self.top
        self.top = self.top.next
        return pop_node.data

    def peek(self) -> T:
        """
        >>> stack = LinkedStack()
        >>> stack.push("Java")
        >>> stack.push("C")
        >>> stack.push("Python")
        >>> stack.peek()
        'Python'
        """
        if self.is_empty():
            raise IndexError("peek from empty stack")

        assert self.top is not None
        return self.top.data

    def clear(self) -> None:
        """
        >>> stack = LinkedStack()
        >>> stack.push("Java")
        >>> stack.push("C")
        >>> stack.push("Python")
        >>> str(stack)
        'Python->C->Java'
        >>> stack.clear()
        >>> len(stack) == 0
        True
        """
        self.top = None


if __name__ == "__main__":
    from doctest import testmod

    testmod()


================================================
File: data_structures/stacks/stock_span_problem.py
================================================
"""
The stock span problem is a financial problem where we have a series of n daily
price quotes for a stock and we need to calculate span of stock's price for all n days.

The span Si of the stock's price on a given day i is defined as the maximum
number of consecutive days just before the given day, for which the price of the stock
on the current day is less than or equal to its price on the given day.
"""


def calculation_span(price, s):
    n = len(price)
    # Create a stack and push index of fist element to it
    st = []
    st.append(0)

    # Span value of first element is always 1
    s[0] = 1

    # Calculate span values for rest of the elements
    for i in range(1, n):
        # Pop elements from stack while stack is not
        # empty and top of stack is smaller than price[i]
        while len(st) > 0 and price[st[0]] <= price[i]:
            st.pop()

        # If stack becomes empty, then price[i] is greater
        # than all elements on left of it, i.e. price[0],
        # price[1], ..price[i-1]. Else the price[i]  is
        # greater than elements after top of stack
        s[i] = i + 1 if len(st) <= 0 else (i - st[0])

        # Push this element to stack
        st.append(i)


# A utility function to print elements of array
def print_array(arr, n):
    for i in range(n):
        print(arr[i], end=" ")


# Driver program to test above function
price = [10, 4, 5, 90, 120, 80]
S = [0 for i in range(len(price) + 1)]

# Fill the span values in array S[]
calculation_span(price, S)

# Print the calculated span values
print_array(S, len(price))


================================================
File: data_structures/suffix_tree/suffix_tree.py
================================================
#  Created by: Ramy-Badr-Ahmed (https://github.com/Ramy-Badr-Ahmed)
#  in Pull Request: #11554
#  https://github.com/TheAlgorithms/Python/pull/11554
#
#  Please mention me (@Ramy-Badr-Ahmed) in any issue or pull request
#  addressing bugs/corrections to this file.
#  Thank you!

from data_structures.suffix_tree.suffix_tree_node import SuffixTreeNode


class SuffixTree:
    def __init__(self, text: str) -> None:
        """
        Initializes the suffix tree with the given text.

        Args:
            text (str): The text for which the suffix tree is to be built.
        """
        self.text: str = text
        self.root: SuffixTreeNode = SuffixTreeNode()
        self.build_suffix_tree()

    def build_suffix_tree(self) -> None:
        """
        Builds the suffix tree for the given text by adding all suffixes.
        """
        text = self.text
        n = len(text)
        for i in range(n):
            suffix = text[i:]
            self._add_suffix(suffix, i)

    def _add_suffix(self, suffix: str, index: int) -> None:
        """
        Adds a suffix to the suffix tree.

        Args:
            suffix (str): The suffix to add.
            index (int): The starting index of the suffix in the original text.
        """
        node = self.root
        for char in suffix:
            if char not in node.children:
                node.children[char] = SuffixTreeNode()
            node = node.children[char]
        node.is_end_of_string = True
        node.start = index
        node.end = index + len(suffix) - 1

    def search(self, pattern: str) -> bool:
        """
        Searches for a pattern in the suffix tree.

        Args:
            pattern (str): The pattern to search for.

        Returns:
            bool: True if the pattern is found, False otherwise.
        """
        node = self.root
        for char in pattern:
            if char not in node.children:
                return False
            node = node.children[char]
        return True


================================================
File: data_structures/suffix_tree/suffix_tree_node.py
================================================
#  Created by: Ramy-Badr-Ahmed (https://github.com/Ramy-Badr-Ahmed)
#  in Pull Request: #11554
#  https://github.com/TheAlgorithms/Python/pull/11554
#
#  Please mention me (@Ramy-Badr-Ahmed) in any issue or pull request
#  addressing bugs/corrections to this file.
#  Thank you!

from __future__ import annotations


class SuffixTreeNode:
    def __init__(
        self,
        children: dict[str, SuffixTreeNode] | None = None,
        is_end_of_string: bool = False,
        start: int | None = None,
        end: int | None = None,
        suffix_link: SuffixTreeNode | None = None,
    ) -> None:
        """
        Initializes a suffix tree node.

        Parameters:
            children (dict[str, SuffixTreeNode] | None): The children of this node.
            is_end_of_string (bool): Indicates if this node represents
                                     the end of a string.
            start (int | None): The start index of the suffix in the text.
            end (int | None): The end index of the suffix in the text.
            suffix_link (SuffixTreeNode | None): Link to another suffix tree node.
        """
        self.children = children or {}
        self.is_end_of_string = is_end_of_string
        self.start = start
        self.end = end
        self.suffix_link = suffix_link


================================================
File: data_structures/suffix_tree/example/example_usage.py
================================================
#  Created by: Ramy-Badr-Ahmed (https://github.com/Ramy-Badr-Ahmed)
#  in Pull Request: #11554
#  https://github.com/TheAlgorithms/Python/pull/11554
#
#  Please mention me (@Ramy-Badr-Ahmed) in any issue or pull request
#  addressing bugs/corrections to this file.
#  Thank you!

from data_structures.suffix_tree.suffix_tree import SuffixTree


def main() -> None:
    """
    Demonstrate the usage of the SuffixTree class.

    - Initializes a SuffixTree with a predefined text.
    - Defines a list of patterns to search for within the suffix tree.
    - Searches for each pattern in the suffix tree.

    Patterns tested:
        - "ana" (found) --> True
        - "ban" (found) --> True
        - "na" (found) --> True
        - "xyz" (not found) --> False
        - "mon" (found) --> True
    """
    text = "monkey banana"
    suffix_tree = SuffixTree(text)

    patterns = ["ana", "ban", "na", "xyz", "mon"]
    for pattern in patterns:
        found = suffix_tree.search(pattern)
        print(f"Pattern '{pattern}' found: {found}")


if __name__ == "__main__":
    main()


================================================
File: data_structures/suffix_tree/tests/test_suffix_tree.py
================================================
#  Created by: Ramy-Badr-Ahmed (https://github.com/Ramy-Badr-Ahmed)
#  in Pull Request: #11554
#  https://github.com/TheAlgorithms/Python/pull/11554
#
#  Please mention me (@Ramy-Badr-Ahmed) in any issue or pull request
#  addressing bugs/corrections to this file.
#  Thank you!

import unittest

from data_structures.suffix_tree.suffix_tree import SuffixTree


class TestSuffixTree(unittest.TestCase):
    def setUp(self) -> None:
        """Set up the initial conditions for each test."""
        self.text = "banana"
        self.suffix_tree = SuffixTree(self.text)

    def test_search_existing_patterns(self) -> None:
        """Test searching for patterns that exist in the suffix tree."""
        patterns = ["ana", "ban", "na"]
        for pattern in patterns:
            with self.subTest(pattern=pattern):
                assert self.suffix_tree.search(pattern), (
                    f"Pattern '{pattern}' should be found."
                )

    def test_search_non_existing_patterns(self) -> None:
        """Test searching for patterns that do not exist in the suffix tree."""
        patterns = ["xyz", "apple", "cat"]
        for pattern in patterns:
            with self.subTest(pattern=pattern):
                assert not self.suffix_tree.search(pattern), (
                    f"Pattern '{pattern}' should not be found."
                )

    def test_search_empty_pattern(self) -> None:
        """Test searching for an empty pattern."""
        assert self.suffix_tree.search(""), "An empty pattern should be found."

    def test_search_full_text(self) -> None:
        """Test searching for the full text."""
        assert self.suffix_tree.search(self.text), (
            "The full text should be found in the suffix tree."
        )

    def test_search_substrings(self) -> None:
        """Test searching for substrings of the full text."""
        substrings = ["ban", "ana", "a", "na"]
        for substring in substrings:
            with self.subTest(substring=substring):
                assert self.suffix_tree.search(substring), (
                    f"Substring '{substring}' should be found."
                )


if __name__ == "__main__":
    unittest.main()


================================================
File: data_structures/trie/radix_tree.py
================================================
"""
A Radix Tree is a data structure that represents a space-optimized
trie (prefix tree) in whicheach node that is the only child is merged
with its parent [https://en.wikipedia.org/wiki/Radix_tree]
"""


class RadixNode:
    def __init__(self, prefix: str = "", is_leaf: bool = False) -> None:
        # Mapping from the first character of the prefix of the node
        self.nodes: dict[str, RadixNode] = {}

        # A node will be a leaf if the tree contains its word
        self.is_leaf = is_leaf

        self.prefix = prefix

    def match(self, word: str) -> tuple[str, str, str]:
        """Compute the common substring of the prefix of the node and a word

        Args:
            word (str): word to compare

        Returns:
            (str, str, str): common substring, remaining prefix, remaining word

        >>> RadixNode("myprefix").match("mystring")
        ('my', 'prefix', 'string')
        """
        x = 0
        for q, w in zip(self.prefix, word):
            if q != w:
                break

            x += 1

        return self.prefix[:x], self.prefix[x:], word[x:]

    def insert_many(self, words: list[str]) -> None:
        """Insert many words in the tree

        Args:
            words (list[str]): list of words

        >>> RadixNode("myprefix").insert_many(["mystring", "hello"])
        """
        for word in words:
            self.insert(word)

    def insert(self, word: str) -> None:
        """Insert a word into the tree

        Args:
            word (str): word to insert

        >>> RadixNode("myprefix").insert("mystring")

        >>> root = RadixNode()
        >>> root.insert_many(['myprefix', 'myprefixA', 'myprefixAA'])
        >>> root.print_tree()
        - myprefix   (leaf)
        -- A   (leaf)
        --- A   (leaf)
        """
        # Case 1: If the word is the prefix of the node
        # Solution: We set the current node as leaf
        if self.prefix == word and not self.is_leaf:
            self.is_leaf = True

        # Case 2: The node has no edges that have a prefix to the word
        # Solution: We create an edge from the current node to a new one
        # containing the word
        elif word[0] not in self.nodes:
            self.nodes[word[0]] = RadixNode(prefix=word, is_leaf=True)

        else:
            incoming_node = self.nodes[word[0]]
            matching_string, remaining_prefix, remaining_word = incoming_node.match(
                word
            )

            # Case 3: The node prefix is equal to the matching
            # Solution: We insert remaining word on the next node
            if remaining_prefix == "":
                self.nodes[matching_string[0]].insert(remaining_word)

            # Case 4: The word is greater equal to the matching
            # Solution: Create a node in between both nodes, change
            # prefixes and add the new node for the remaining word
            else:
                incoming_node.prefix = remaining_prefix

                aux_node = self.nodes[matching_string[0]]
                self.nodes[matching_string[0]] = RadixNode(matching_string, False)
                self.nodes[matching_string[0]].nodes[remaining_prefix[0]] = aux_node

                if remaining_word == "":
                    self.nodes[matching_string[0]].is_leaf = True
                else:
                    self.nodes[matching_string[0]].insert(remaining_word)

    def find(self, word: str) -> bool:
        """Returns if the word is on the tree

        Args:
            word (str): word to check

        Returns:
            bool: True if the word appears on the tree

        >>> RadixNode("myprefix").find("mystring")
        False
        """
        incoming_node = self.nodes.get(word[0], None)
        if not incoming_node:
            return False
        else:
            matching_string, remaining_prefix, remaining_word = incoming_node.match(
                word
            )
            # If there is remaining prefix, the word can't be on the tree
            if remaining_prefix != "":
                return False
            # This applies when the word and the prefix are equal
            elif remaining_word == "":
                return incoming_node.is_leaf
            # We have word remaining so we check the next node
            else:
                return incoming_node.find(remaining_word)

    def delete(self, word: str) -> bool:
        """Deletes a word from the tree if it exists

        Args:
            word (str): word to be deleted

        Returns:
            bool: True if the word was found and deleted. False if word is not found

        >>> RadixNode("myprefix").delete("mystring")
        False
        """
        incoming_node = self.nodes.get(word[0], None)
        if not incoming_node:
            return False
        else:
            matching_string, remaining_prefix, remaining_word = incoming_node.match(
                word
            )
            # If there is remaining prefix, the word can't be on the tree
            if remaining_prefix != "":
                return False
            # We have word remaining so we check the next node
            elif remaining_word != "":
                return incoming_node.delete(remaining_word)
            # If it is not a leaf, we don't have to delete
            elif not incoming_node.is_leaf:
                return False
            else:
                # We delete the nodes if no edges go from it
                if len(incoming_node.nodes) == 0:
                    del self.nodes[word[0]]
                    # We merge the current node with its only child
                    if len(self.nodes) == 1 and not self.is_leaf:
                        merging_node = next(iter(self.nodes.values()))
                        self.is_leaf = merging_node.is_leaf
                        self.prefix += merging_node.prefix
                        self.nodes = merging_node.nodes
                # If there is more than 1 edge, we just mark it as non-leaf
                elif len(incoming_node.nodes) > 1:
                    incoming_node.is_leaf = False
                # If there is 1 edge, we merge it with its child
                else:
                    merging_node = next(iter(incoming_node.nodes.values()))
                    incoming_node.is_leaf = merging_node.is_leaf
                    incoming_node.prefix += merging_node.prefix
                    incoming_node.nodes = merging_node.nodes

                return True

    def print_tree(self, height: int = 0) -> None:
        """Print the tree

        Args:
            height (int, optional): Height of the printed node
        """
        if self.prefix != "":
            print("-" * height, self.prefix, "  (leaf)" if self.is_leaf else "")

        for value in self.nodes.values():
            value.print_tree(height + 1)


def test_trie() -> bool:
    words = "banana bananas bandana band apple all beast".split()
    root = RadixNode()
    root.insert_many(words)

    assert all(root.find(word) for word in words)
    assert not root.find("bandanas")
    assert not root.find("apps")
    root.delete("all")
    assert not root.find("all")
    root.delete("banana")
    assert not root.find("banana")
    assert root.find("bananas")

    return True


def pytests() -> None:
    assert test_trie()


def main() -> None:
    """
    >>> pytests()
    """
    root = RadixNode()
    words = "banana bananas bandanas bandana band apple all beast".split()
    root.insert_many(words)

    print("Words:", words)
    print("Tree:")
    root.print_tree()


if __name__ == "__main__":
    main()


================================================
File: data_structures/trie/trie.py
================================================
"""
A Trie/Prefix Tree is a kind of search tree used to provide quick lookup
of words/patterns in a set of words. A basic Trie however has O(n^2) space complexity
making it impractical in practice. It however provides O(max(search_string, length of
longest word)) lookup time making it an optimal approach when space is not an issue.
"""


class TrieNode:
    def __init__(self) -> None:
        self.nodes: dict[str, TrieNode] = {}  # Mapping from char to TrieNode
        self.is_leaf = False

    def insert_many(self, words: list[str]) -> None:
        """
        Inserts a list of words into the Trie
        :param words: list of string words
        :return: None
        """
        for word in words:
            self.insert(word)

    def insert(self, word: str) -> None:
        """
        Inserts a word into the Trie
        :param word: word to be inserted
        :return: None
        """
        curr = self
        for char in word:
            if char not in curr.nodes:
                curr.nodes[char] = TrieNode()
            curr = curr.nodes[char]
        curr.is_leaf = True

    def find(self, word: str) -> bool:
        """
        Tries to find word in a Trie
        :param word: word to look for
        :return: Returns True if word is found, False otherwise
        """
        curr = self
        for char in word:
            if char not in curr.nodes:
                return False
            curr = curr.nodes[char]
        return curr.is_leaf

    def delete(self, word: str) -> None:
        """
        Deletes a word in a Trie
        :param word: word to delete
        :return: None
        """

        def _delete(curr: TrieNode, word: str, index: int) -> bool:
            if index == len(word):
                # If word does not exist
                if not curr.is_leaf:
                    return False
                curr.is_leaf = False
                return len(curr.nodes) == 0
            char = word[index]
            char_node = curr.nodes.get(char)
            # If char not in current trie node
            if not char_node:
                return False
            # Flag to check if node can be deleted
            delete_curr = _delete(char_node, word, index + 1)
            if delete_curr:
                del curr.nodes[char]
                return len(curr.nodes) == 0
            return delete_curr

        _delete(self, word, 0)


def print_words(node: TrieNode, word: str) -> None:
    """
    Prints all the words in a Trie
    :param node: root node of Trie
    :param word: Word variable should be empty at start
    :return: None
    """
    if node.is_leaf:
        print(word, end=" ")

    for key, value in node.nodes.items():
        print_words(value, word + key)


def test_trie() -> bool:
    words = "banana bananas bandana band apple all beast".split()
    root = TrieNode()
    root.insert_many(words)
    # print_words(root, "")
    assert all(root.find(word) for word in words)
    assert root.find("banana")
    assert not root.find("bandanas")
    assert not root.find("apps")
    assert root.find("apple")
    assert root.find("all")
    root.delete("all")
    assert not root.find("all")
    root.delete("banana")
    assert not root.find("banana")
    assert root.find("bananas")
    return True


def print_results(msg: str, passes: bool) -> None:
    print(str(msg), "works!" if passes else "doesn't work :(")


def pytests() -> None:
    assert test_trie()


def main() -> None:
    """
    >>> pytests()
    """
    print_results("Testing trie functionality", test_trie())


if __name__ == "__main__":
    main()


================================================
File: docs/conf.py
================================================
from sphinx_pyproject import SphinxConfig

project = SphinxConfig("../pyproject.toml", globalns=globals()).name


================================================
File: web_programming/co2_emission.py
================================================
"""
Get CO2 emission data from the UK CarbonIntensity API
"""

from datetime import date

import requests

BASE_URL = "https://api.carbonintensity.org.uk/intensity"


# Emission in the last half hour
def fetch_last_half_hour() -> str:
    last_half_hour = requests.get(BASE_URL, timeout=10).json()["data"][0]
    return last_half_hour["intensity"]["actual"]


# Emissions in a specific date range
def fetch_from_to(start, end) -> list:
    return requests.get(f"{BASE_URL}/{start}/{end}", timeout=10).json()["data"]


if __name__ == "__main__":
    for entry in fetch_from_to(start=date(2020, 10, 1), end=date(2020, 10, 3)):
        print("from {from} to {to}: {intensity[actual]}".format(**entry))
    print(f"{fetch_last_half_hour() = }")


================================================
File: web_programming/covid_stats_via_xpath.py
================================================
"""
This is to show simple COVID19 info fetching from worldometers site using lxml
* The main motivation to use lxml in place of bs4 is that it is faster and therefore
more convenient to use in Python web projects (e.g. Django or Flask-based)
"""

from typing import NamedTuple

import requests
from lxml import html


class CovidData(NamedTuple):
    cases: int
    deaths: int
    recovered: int


def covid_stats(url: str = "https://www.worldometers.info/coronavirus/") -> CovidData:
    xpath_str = '//div[@class = "maincounter-number"]/span/text()'
    return CovidData(
        *html.fromstring(requests.get(url, timeout=10).content).xpath(xpath_str)
    )


fmt = """Total COVID-19 cases in the world: {}
Total deaths due to COVID-19 in the world: {}
Total COVID-19 patients recovered in the world: {}"""
print(fmt.format(*covid_stats()))


================================================
File: web_programming/crawl_google_results.py
================================================
import sys
import webbrowser

import requests
from bs4 import BeautifulSoup
from fake_useragent import UserAgent

if __name__ == "__main__":
    print("Googling.....")
    url = "https://www.google.com/search?q=" + " ".join(sys.argv[1:])
    res = requests.get(url, headers={"UserAgent": UserAgent().random}, timeout=10)
    # res.raise_for_status()
    with open("project1a.html", "wb") as out_file:  # only for knowing the class
        for data in res.iter_content(10000):
            out_file.write(data)
    soup = BeautifulSoup(res.text, "html.parser")
    links = list(soup.select(".eZt8xd"))[:5]

    print(len(links))
    for link in links:
        if link.text == "Maps":
            webbrowser.open(link.get("href"))
        else:
            webbrowser.open(f"https://google.com{link.get('href')}")


================================================
File: web_programming/crawl_google_scholar_citation.py
================================================
"""
Get the citation from google scholar
using title and year of publication, and volume and pages of journal.
"""

import requests
from bs4 import BeautifulSoup


def get_citation(base_url: str, params: dict) -> str:
    """
    Return the citation number.
    """
    soup = BeautifulSoup(
        requests.get(base_url, params=params, timeout=10).content, "html.parser"
    )
    div = soup.find("div", attrs={"class": "gs_ri"})
    anchors = div.find("div", attrs={"class": "gs_fl"}).find_all("a")
    return anchors[2].get_text()


if __name__ == "__main__":
    params = {
        "title": (
            "Precisely geometry controlled microsupercapacitors for ultrahigh areal "
            "capacitance, volumetric capacitance, and energy density"
        ),
        "journal": "Chem. Mater.",
        "volume": 30,
        "pages": "3979-3990",
        "year": 2018,
        "hl": "en",
    }
    print(get_citation("https://scholar.google.com/scholar_lookup", params=params))


================================================
File: web_programming/currency_converter.py
================================================
"""
This is used to convert the currency using the Amdoren Currency API
https://www.amdoren.com
"""

import os

import requests

URL_BASE = "https://www.amdoren.com/api/currency.php"


# Currency and their description
list_of_currencies = """
AED	United Arab Emirates Dirham
AFN	Afghan Afghani
ALL	Albanian Lek
AMD	Armenian Dram
ANG	Netherlands Antillean Guilder
AOA	Angolan Kwanza
ARS	Argentine Peso
AUD	Australian Dollar
AWG	Aruban Florin
AZN	Azerbaijani Manat
BAM	Bosnia & Herzegovina Convertible Mark
BBD	Barbadian Dollar
BDT	Bangladeshi Taka
BGN	Bulgarian Lev
BHD	Bahraini Dinar
BIF	Burundian Franc
BMD	Bermudian Dollar
BND	Brunei Dollar
BOB	Bolivian Boliviano
BRL	Brazilian Real
BSD	Bahamian Dollar
BTN	Bhutanese Ngultrum
BWP	Botswana Pula
BYN	Belarus Ruble
BZD	Belize Dollar
CAD	Canadian Dollar
CDF	Congolese Franc
CHF	Swiss Franc
CLP	Chilean Peso
CNY	Chinese Yuan
COP	Colombian Peso
CRC	Costa Rican Colon
CUC	Cuban Convertible Peso
CVE	Cape Verdean Escudo
CZK	Czech Republic Koruna
DJF	Djiboutian Franc
DKK	Danish Krone
DOP	Dominican Peso
DZD	Algerian Dinar
EGP	Egyptian Pound
ERN	Eritrean Nakfa
ETB	Ethiopian Birr
EUR	Euro
FJD	Fiji Dollar
GBP	British Pound Sterling
GEL	Georgian Lari
GHS	Ghanaian Cedi
GIP	Gibraltar Pound
GMD	Gambian Dalasi
GNF	Guinea Franc
GTQ	Guatemalan Quetzal
GYD	Guyanaese Dollar
HKD	Hong Kong Dollar
HNL	Honduran Lempira
HRK	Croatian Kuna
HTG	Haiti Gourde
HUF	Hungarian Forint
IDR	Indonesian Rupiah
ILS	Israeli Shekel
INR	Indian Rupee
IQD	Iraqi Dinar
IRR	Iranian Rial
ISK	Icelandic Krona
JMD	Jamaican Dollar
JOD	Jordanian Dinar
JPY	Japanese Yen
KES	Kenyan Shilling
KGS	Kyrgystani Som
KHR	Cambodian Riel
KMF	Comorian Franc
KPW	North Korean Won
KRW	South Korean Won
KWD	Kuwaiti Dinar
KYD	Cayman Islands Dollar
KZT	Kazakhstan Tenge
LAK	Laotian Kip
LBP	Lebanese Pound
LKR	Sri Lankan Rupee
LRD	Liberian Dollar
LSL	Lesotho Loti
LYD	Libyan Dinar
MAD	Moroccan Dirham
MDL	Moldovan Leu
MGA	Malagasy Ariary
MKD	Macedonian Denar
MMK	Myanma Kyat
MNT	Mongolian Tugrik
MOP	Macau Pataca
MRO	Mauritanian Ouguiya
MUR	Mauritian Rupee
MVR	Maldivian Rufiyaa
MWK	Malawi Kwacha
MXN	Mexican Peso
MYR	Malaysian Ringgit
MZN	Mozambican Metical
NAD	Namibian Dollar
NGN	Nigerian Naira
NIO	Nicaragua Cordoba
NOK	Norwegian Krone
NPR	Nepalese Rupee
NZD	New Zealand Dollar
OMR	Omani Rial
PAB	Panamanian Balboa
PEN	Peruvian Nuevo Sol
PGK	Papua New Guinean Kina
PHP	Philippine Peso
PKR	Pakistani Rupee
PLN	Polish Zloty
PYG	Paraguayan Guarani
QAR	Qatari Riyal
RON	Romanian Leu
RSD	Serbian Dinar
RUB	Russian Ruble
RWF	Rwanda Franc
SAR	Saudi Riyal
SBD	Solomon Islands Dollar
SCR	Seychellois Rupee
SDG	Sudanese Pound
SEK	Swedish Krona
SGD	Singapore Dollar
SHP	Saint Helena Pound
SLL	Sierra Leonean Leone
SOS	Somali Shilling
SRD	Surinamese Dollar
SSP	South Sudanese Pound
STD	Sao Tome and Principe Dobra
SYP	Syrian Pound
SZL	Swazi Lilangeni
THB	Thai Baht
TJS	Tajikistan Somoni
TMT	Turkmenistani Manat
TND	Tunisian Dinar
TOP	Tonga Paanga
TRY	Turkish Lira
TTD	Trinidad and Tobago Dollar
TWD	New Taiwan Dollar
TZS	Tanzanian Shilling
UAH	Ukrainian Hryvnia
UGX	Ugandan Shilling
USD	United States Dollar
UYU	Uruguayan Peso
UZS	Uzbekistan Som
VEF	Venezuelan Bolivar
VND	Vietnamese Dong
VUV	Vanuatu Vatu
WST	Samoan Tala
XAF	Central African CFA franc
XCD	East Caribbean Dollar
XOF	West African CFA franc
XPF	CFP Franc
YER	Yemeni Rial
ZAR	South African Rand
ZMW	Zambian Kwacha
"""


def convert_currency(
    from_: str = "USD", to: str = "INR", amount: float = 1.0, api_key: str = ""
) -> str:
    """https://www.amdoren.com/currency-api/"""
    # Instead of manually generating parameters
    params = locals()
    # from is a reserved keyword
    params["from"] = params.pop("from_")
    res = requests.get(URL_BASE, params=params, timeout=10).json()
    return str(res["amount"]) if res["error"] == 0 else res["error_message"]


if __name__ == "__main__":
    TESTING = os.getenv("CI", "")
    API_KEY = os.getenv("AMDOREN_API_KEY", "")

    if not API_KEY and not TESTING:
        raise KeyError(
            "API key must be provided in the 'AMDOREN_API_KEY' environment variable."
        )

    print(
        convert_currency(
            input("Enter from currency: ").strip(),
            input("Enter to currency: ").strip(),
            float(input("Enter the amount: ").strip()),
            API_KEY,
        )
    )


================================================
File: web_programming/current_stock_price.py
================================================
import requests
from bs4 import BeautifulSoup

"""
Get the HTML code of finance yahoo and select the current qsp-price
Current AAPL stock price is   228.43
Current AMZN stock price is   201.85
Current IBM  stock price is   210.30
Current GOOG stock price is   177.86
Current MSFT stock price is   414.82
Current ORCL stock price is   188.87
"""


def stock_price(symbol: str = "AAPL") -> str:
    """
    >>> stock_price("EEEE")
    '- '
    >>> isinstance(float(stock_price("GOOG")),float)
    True
    """
    url = f"https://finance.yahoo.com/quote/{symbol}?p={symbol}"
    yahoo_finance_source = requests.get(
        url, headers={"USER-AGENT": "Mozilla/5.0"}, timeout=10
    ).text
    soup = BeautifulSoup(yahoo_finance_source, "html.parser")

    if specific_fin_streamer_tag := soup.find("span", {"data-testid": "qsp-price"}):
        return specific_fin_streamer_tag.get_text()
    return "No <fin-streamer> tag with the specified data-testid attribute found."


# Search for the symbol at https://finance.yahoo.com/lookup
if __name__ == "__main__":
    from doctest import testmod

    testmod()

    for symbol in "AAPL AMZN IBM GOOG MSFT ORCL".split():
        print(f"Current {symbol:<4} stock price is {stock_price(symbol):>8}")


================================================
File: web_programming/current_weather.py
================================================
import requests

# Put your API key(s) here
OPENWEATHERMAP_API_KEY = ""
WEATHERSTACK_API_KEY = ""

# Define the URL for the APIs with placeholders
OPENWEATHERMAP_URL_BASE = "https://api.openweathermap.org/data/2.5/weather"
WEATHERSTACK_URL_BASE = "http://api.weatherstack.com/current"


def current_weather(location: str) -> list[dict]:
    """
    >>> current_weather("location")
    Traceback (most recent call last):
        ...
    ValueError: No API keys provided or no valid data returned.
    """
    weather_data = []
    if OPENWEATHERMAP_API_KEY:
        params_openweathermap = {"q": location, "appid": OPENWEATHERMAP_API_KEY}
        response_openweathermap = requests.get(
            OPENWEATHERMAP_URL_BASE, params=params_openweathermap, timeout=10
        )
        weather_data.append({"OpenWeatherMap": response_openweathermap.json()})
    if WEATHERSTACK_API_KEY:
        params_weatherstack = {"query": location, "access_key": WEATHERSTACK_API_KEY}
        response_weatherstack = requests.get(
            WEATHERSTACK_URL_BASE, params=params_weatherstack, timeout=10
        )
        weather_data.append({"Weatherstack": response_weatherstack.json()})
    if not weather_data:
        raise ValueError("No API keys provided or no valid data returned.")
    return weather_data


if __name__ == "__main__":
    from pprint import pprint

    location = "to be determined..."
    while location:
        location = input("Enter a location (city name or latitude,longitude): ").strip()
        if location:
            try:
                weather_data = current_weather(location)
                for forecast in weather_data:
                    pprint(forecast)
            except ValueError as e:
                print(repr(e))
                location = ""


================================================
File: web_programming/daily_horoscope.py
================================================
import requests
from bs4 import BeautifulSoup


def horoscope(zodiac_sign: int, day: str) -> str:
    url = (
        "https://www.horoscope.com/us/horoscopes/general/"
        f"horoscope-general-daily-{day}.aspx?sign={zodiac_sign}"
    )
    soup = BeautifulSoup(requests.get(url, timeout=10).content, "html.parser")
    return soup.find("div", class_="main-horoscope").p.text


if __name__ == "__main__":
    print("Daily Horoscope. \n")
    print(
        "enter your Zodiac sign number:\n",
        "1. Aries\n",
        "2. Taurus\n",
        "3. Gemini\n",
        "4. Cancer\n",
        "5. Leo\n",
        "6. Virgo\n",
        "7. Libra\n",
        "8. Scorpio\n",
        "9. Sagittarius\n",
        "10. Capricorn\n",
        "11. Aquarius\n",
        "12. Pisces\n",
    )
    zodiac_sign = int(input("number> ").strip())
    print("choose some day:\n", "yesterday\n", "today\n", "tomorrow\n")
    day = input("enter the day> ")
    horoscope_text = horoscope(zodiac_sign, day)
    print(horoscope_text)


================================================
File: web_programming/download_images_from_google_query.py
================================================
import json
import os
import re
import sys
import urllib.request

import requests
from bs4 import BeautifulSoup

headers = {
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36"
    " (KHTML, like Gecko) Chrome/70.0.3538.102 Safari/537.36 Edge/18.19582"
}


def download_images_from_google_query(query: str = "dhaka", max_images: int = 5) -> int:
    """
    Searches google using the provided query term and downloads the images in a folder.

    Args:
         query : The image search term to be provided by the user. Defaults to
        "dhaka".
        image_numbers : [description]. Defaults to 5.

    Returns:
        The number of images successfully downloaded.

    # Comment out slow (4.20s call) doctests
    # >>> download_images_from_google_query()
    5
    # >>> download_images_from_google_query("potato")
    5
    """
    max_images = min(max_images, 50)  # Prevent abuse!
    params = {
        "q": query,
        "tbm": "isch",
        "hl": "en",
        "ijn": "0",
    }

    html = requests.get(
        "https://www.google.com/search", params=params, headers=headers, timeout=10
    )
    soup = BeautifulSoup(html.text, "html.parser")
    matched_images_data = "".join(
        re.findall(r"AF_initDataCallback\(([^<]+)\);", str(soup.select("script")))
    )

    matched_images_data_fix = json.dumps(matched_images_data)
    matched_images_data_json = json.loads(matched_images_data_fix)

    matched_google_image_data = re.findall(
        r"\[\"GRID_STATE0\",null,\[\[1,\[0,\".*?\",(.*),\"All\",",
        matched_images_data_json,
    )
    if not matched_google_image_data:
        return 0

    removed_matched_google_images_thumbnails = re.sub(
        r"\[\"(https\:\/\/encrypted-tbn0\.gstatic\.com\/images\?.*?)\",\d+,\d+\]",
        "",
        str(matched_google_image_data),
    )

    matched_google_full_resolution_images = re.findall(
        r"(?:'|,),\[\"(https:|http.*?)\",\d+,\d+\]",
        removed_matched_google_images_thumbnails,
    )
    for index, fixed_full_res_image in enumerate(matched_google_full_resolution_images):
        if index >= max_images:
            return index
        original_size_img_not_fixed = bytes(fixed_full_res_image, "ascii").decode(
            "unicode-escape"
        )
        original_size_img = bytes(original_size_img_not_fixed, "ascii").decode(
            "unicode-escape"
        )
        opener = urllib.request.build_opener()
        opener.addheaders = [
            (
                "User-Agent",
                "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36"
                " (KHTML, like Gecko) Chrome/70.0.3538.102 Safari/537.36 Edge/18.19582",
            )
        ]
        urllib.request.install_opener(opener)
        path_name = f"query_{query.replace(' ', '_')}"
        if not os.path.exists(path_name):
            os.makedirs(path_name)
        urllib.request.urlretrieve(  # noqa: S310
            original_size_img, f"{path_name}/original_size_img_{index}.jpg"
        )
    return index


if __name__ == "__main__":
    try:
        image_count = download_images_from_google_query(sys.argv[1])
        print(f"{image_count} images were downloaded to disk.")
    except IndexError:
        print("Please provide a search term.")
        raise


================================================
File: web_programming/emails_from_url.py
================================================
"""Get the site emails from URL."""

from __future__ import annotations

__author__ = "Muhammad Umer Farooq"
__license__ = "MIT"
__version__ = "1.0.0"
__maintainer__ = "Muhammad Umer Farooq"
__email__ = "contact@muhammadumerfarooq.me"
__status__ = "Alpha"

import re
from html.parser import HTMLParser
from urllib import parse

import requests


class Parser(HTMLParser):
    def __init__(self, domain: str) -> None:
        super().__init__()
        self.urls: list[str] = []
        self.domain = domain

    def handle_starttag(self, tag: str, attrs: list[tuple[str, str | None]]) -> None:
        """
        This function parse html to take takes url from tags
        """
        # Only parse the 'anchor' tag.
        if tag == "a":
            # Check the list of defined attributes.
            for name, value in attrs:
                # If href is defined, not empty nor # print it and not already in urls.
                if name == "href" and value not in (*self.urls, "", "#"):
                    url = parse.urljoin(self.domain, value)
                    self.urls.append(url)


# Get main domain name (example.com)
def get_domain_name(url: str) -> str:
    """
    This function get the main domain name

    >>> get_domain_name("https://a.b.c.d/e/f?g=h,i=j#k")
    'c.d'
    >>> get_domain_name("Not a URL!")
    ''
    """
    return ".".join(get_sub_domain_name(url).split(".")[-2:])


# Get sub domain name (sub.example.com)
def get_sub_domain_name(url: str) -> str:
    """
    >>> get_sub_domain_name("https://a.b.c.d/e/f?g=h,i=j#k")
    'a.b.c.d'
    >>> get_sub_domain_name("Not a URL!")
    ''
    """
    return parse.urlparse(url).netloc


def emails_from_url(url: str = "https://github.com") -> list[str]:
    """
    This function takes url and return all valid urls
    """
    # Get the base domain from the url
    domain = get_domain_name(url)

    # Initialize the parser
    parser = Parser(domain)

    try:
        # Open URL
        r = requests.get(url, timeout=10)

        # pass the raw HTML to the parser to get links
        parser.feed(r.text)

        # Get links and loop through
        valid_emails = set()
        for link in parser.urls:
            # open URL.
            # read = requests.get(link)
            try:
                read = requests.get(link, timeout=10)
                # Get the valid email.
                emails = re.findall("[a-zA-Z0-9]+@" + domain, read.text)
                # If not in list then append it.
                for email in emails:
                    valid_emails.add(email)
            except ValueError:
                pass
    except ValueError:
        raise SystemExit(1)

    # Finally return a sorted list of email addresses with no duplicates.
    return sorted(valid_emails)


if __name__ == "__main__":
    emails = emails_from_url("https://github.com")
    print(f"{len(emails)} emails found:")
    print("\n".join(sorted(emails)))


================================================
File: web_programming/fetch_anime_and_play.py
================================================
import requests
from bs4 import BeautifulSoup, NavigableString, Tag
from fake_useragent import UserAgent

BASE_URL = "https://ww1.gogoanime2.org"


def search_scraper(anime_name: str) -> list:
    """[summary]

    Take an url and
    return list of anime after scraping the site.

    >>> type(search_scraper("demon_slayer"))
    <class 'list'>

    Args:
        anime_name (str): [Name of anime]

    Raises:
        e: [Raises exception on failure]

    Returns:
        [list]: [List of animes]
    """

    # concat the name to form the search url.
    search_url = f"{BASE_URL}/search/{anime_name}"

    response = requests.get(
        search_url, headers={"UserAgent": UserAgent().chrome}, timeout=10
    )  # request the url.

    # Is the response ok?
    response.raise_for_status()

    # parse with soup.
    soup = BeautifulSoup(response.text, "html.parser")

    # get list of anime
    anime_ul = soup.find("ul", {"class": "items"})
    if anime_ul is None or isinstance(anime_ul, NavigableString):
        msg = f"Could not find and anime with name {anime_name}"
        raise ValueError(msg)
    anime_li = anime_ul.children

    # for each anime, insert to list. the name and url.
    anime_list = []
    for anime in anime_li:
        if isinstance(anime, Tag):
            anime_url = anime.find("a")
            if anime_url is None or isinstance(anime_url, NavigableString):
                continue
            anime_title = anime.find("a")
            if anime_title is None or isinstance(anime_title, NavigableString):
                continue

            anime_list.append({"title": anime_title["title"], "url": anime_url["href"]})

    return anime_list


def search_anime_episode_list(episode_endpoint: str) -> list:
    """[summary]

    Take an url and
    return list of episodes after scraping the site
    for an url.

    >>> type(search_anime_episode_list("/anime/kimetsu-no-yaiba"))
    <class 'list'>

    Args:
        episode_endpoint (str): [Endpoint of episode]

    Raises:
        e: [description]

    Returns:
        [list]: [List of episodes]
    """

    request_url = f"{BASE_URL}{episode_endpoint}"

    response = requests.get(
        url=request_url, headers={"UserAgent": UserAgent().chrome}, timeout=10
    )
    response.raise_for_status()

    soup = BeautifulSoup(response.text, "html.parser")

    # With this id. get the episode list.
    episode_page_ul = soup.find("ul", {"id": "episode_related"})
    if episode_page_ul is None or isinstance(episode_page_ul, NavigableString):
        msg = f"Could not find any anime eposiodes with name {anime_name}"
        raise ValueError(msg)
    episode_page_li = episode_page_ul.children

    episode_list = []
    for episode in episode_page_li:
        if isinstance(episode, Tag):
            url = episode.find("a")
            if url is None or isinstance(url, NavigableString):
                continue
            title = episode.find("div", {"class": "name"})
            if title is None or isinstance(title, NavigableString):
                continue

            episode_list.append(
                {"title": title.text.replace(" ", ""), "url": url["href"]}
            )

    return episode_list


def get_anime_episode(episode_endpoint: str) -> list:
    """[summary]

    Get click url and download url from episode url

    >>> type(get_anime_episode("/watch/kimetsu-no-yaiba/1"))
    <class 'list'>

    Args:
        episode_endpoint (str): [Endpoint of episode]

    Raises:
        e: [description]

    Returns:
        [list]: [List of download and watch url]
    """

    episode_page_url = f"{BASE_URL}{episode_endpoint}"

    response = requests.get(
        url=episode_page_url, headers={"User-Agent": UserAgent().chrome}, timeout=10
    )
    response.raise_for_status()

    soup = BeautifulSoup(response.text, "html.parser")

    url = soup.find("iframe", {"id": "playerframe"})
    if url is None or isinstance(url, NavigableString):
        msg = f"Could not find url and download url from {episode_endpoint}"
        raise RuntimeError(msg)

    episode_url = url["src"]
    if not isinstance(episode_url, str):
        msg = f"Could not find url and download url from {episode_endpoint}"
        raise RuntimeError(msg)
    download_url = episode_url.replace("/embed/", "/playlist/") + ".m3u8"

    return [f"{BASE_URL}{episode_url}", f"{BASE_URL}{download_url}"]


if __name__ == "__main__":
    anime_name = input("Enter anime name: ").strip()
    anime_list = search_scraper(anime_name)
    print("\n")

    if len(anime_list) == 0:
        print("No anime found with this name")
    else:
        print(f"Found {len(anime_list)} results: ")
        for i, anime in enumerate(anime_list):
            anime_title = anime["title"]
            print(f"{i + 1}. {anime_title}")

        anime_choice = int(input("\nPlease choose from the following list: ").strip())
        chosen_anime = anime_list[anime_choice - 1]
        print(f"You chose {chosen_anime['title']}. Searching for episodes...")

        episode_list = search_anime_episode_list(chosen_anime["url"])
        if len(episode_list) == 0:
            print("No episode found for this anime")
        else:
            print(f"Found {len(episode_list)} results: ")
            for i, episode in enumerate(episode_list):
                print(f"{i + 1}. {episode['title']}")

            episode_choice = int(input("\nChoose an episode by serial no: ").strip())
            chosen_episode = episode_list[episode_choice - 1]
            print(f"You chose {chosen_episode['title']}. Searching...")

            episode_url, download_url = get_anime_episode(chosen_episode["url"])
            print(f"\nTo watch, ctrl+click on {episode_url}.")
            print(f"To download, ctrl+click on {download_url}.")


================================================
File: web_programming/fetch_bbc_news.py
================================================
# Created by sarathkaul on 12/11/19

import requests

_NEWS_API = "https://newsapi.org/v1/articles?source=bbc-news&sortBy=top&apiKey="


def fetch_bbc_news(bbc_news_api_key: str) -> None:
    # fetching a list of articles in json format
    bbc_news_page = requests.get(_NEWS_API + bbc_news_api_key, timeout=10).json()
    # each article in the list is a dict
    for i, article in enumerate(bbc_news_page["articles"], 1):
        print(f"{i}.) {article['title']}")


if __name__ == "__main__":
    fetch_bbc_news(bbc_news_api_key="<Your BBC News API key goes here>")


================================================
File: web_programming/fetch_github_info.py
================================================
#!/usr/bin/env python3
"""
Created by sarathkaul on 14/11/19
Updated by lawric1 on 24/11/20

Authentication will be made via access token.
To generate your personal access token visit https://github.com/settings/tokens.

NOTE:
Never hardcode any credential information in the code. Always use an environment
file to store the private information and use the `os` module to get the information
during runtime.

Create a ".env" file in the root directory and write these two lines in that file
with your token::

#!/usr/bin/env bash
export USER_TOKEN=""
"""

from __future__ import annotations

import os
from typing import Any

import requests

BASE_URL = "https://api.github.com"

# https://docs.github.com/en/free-pro-team@latest/rest/reference/users#get-the-authenticated-user
AUTHENTICATED_USER_ENDPOINT = BASE_URL + "/user"

# https://github.com/settings/tokens
USER_TOKEN = os.environ.get("USER_TOKEN", "")


def fetch_github_info(auth_token: str) -> dict[Any, Any]:
    """
    Fetch GitHub info of a user using the requests module
    """
    headers = {
        "Authorization": f"token {auth_token}",
        "Accept": "application/vnd.github.v3+json",
    }
    return requests.get(AUTHENTICATED_USER_ENDPOINT, headers=headers, timeout=10).json()


if __name__ == "__main__":  # pragma: no cover
    if USER_TOKEN:
        for key, value in fetch_github_info(USER_TOKEN).items():
            print(f"{key}: {value}")
    else:
        raise ValueError("'USER_TOKEN' field cannot be empty.")


================================================
File: web_programming/fetch_jobs.py
================================================
"""
Scraping jobs given job title and location from indeed website
"""

from __future__ import annotations

from collections.abc import Generator

import requests
from bs4 import BeautifulSoup

url = "https://www.indeed.co.in/jobs?q=mobile+app+development&l="


def fetch_jobs(location: str = "mumbai") -> Generator[tuple[str, str]]:
    soup = BeautifulSoup(
        requests.get(url + location, timeout=10).content, "html.parser"
    )
    # This attribute finds out all the specifics listed in a job
    for job in soup.find_all("div", attrs={"data-tn-component": "organicJob"}):
        job_title = job.find("a", attrs={"data-tn-element": "jobTitle"}).text.strip()
        company_name = job.find("span", {"class": "company"}).text.strip()
        yield job_title, company_name


if __name__ == "__main__":
    for i, job in enumerate(fetch_jobs("Bangalore"), 1):
        print(f"Job {i:>2} is {job[0]} at {job[1]}")


================================================
File: web_programming/fetch_quotes.py
================================================
"""
This file fetches quotes from the " ZenQuotes API ".
It does not require any API key as it uses free tier.

For more details and premium features visit:
    https://zenquotes.io/
"""

import pprint

import requests

API_ENDPOINT_URL = "https://zenquotes.io/api"


def quote_of_the_day() -> list:
    return requests.get(API_ENDPOINT_URL + "/today", timeout=10).json()


def random_quotes() -> list:
    return requests.get(API_ENDPOINT_URL + "/random", timeout=10).json()


if __name__ == "__main__":
    """
    response object has all the info with the quote
    To retrieve the actual quote access the response.json() object as below
    response.json() is a list of json object
        response.json()[0]['q'] = actual quote.
        response.json()[0]['a'] = author name.
        response.json()[0]['h'] = in html format.
    """
    response = random_quotes()
    pprint.pprint(response)


================================================
File: web_programming/fetch_well_rx_price.py
================================================
"""

Scrape the price and pharmacy name for a prescription drug from rx site
after providing the drug name and zipcode.

"""

from urllib.error import HTTPError

from bs4 import BeautifulSoup
from requests import exceptions, get

BASE_URL = "https://www.wellrx.com/prescriptions/{0}/{1}/?freshSearch=true"


def fetch_pharmacy_and_price_list(drug_name: str, zip_code: str) -> list | None:
    """[summary]

    This function will take input of drug name and zipcode,
    then request to the BASE_URL site.
    Get the page data and scrape it to the generate the
    list of lowest prices for the prescription drug.

    Args:
        drug_name (str): [Drug name]
        zip_code(str): [Zip code]

    Returns:
        list: [List of pharmacy name and price]

    >>> fetch_pharmacy_and_price_list(None, None)

    >>> fetch_pharmacy_and_price_list(None, 30303)

    >>> fetch_pharmacy_and_price_list("eliquis", None)

    """

    try:
        # Has user provided both inputs?
        if not drug_name or not zip_code:
            return None

        request_url = BASE_URL.format(drug_name, zip_code)
        response = get(request_url, timeout=10)

        # Is the response ok?
        response.raise_for_status()

        # Scrape the data using bs4
        soup = BeautifulSoup(response.text, "html.parser")

        # This list will store the name and price.
        pharmacy_price_list = []

        # Fetch all the grids that contains the items.
        grid_list = soup.find_all("div", {"class": "grid-x pharmCard"})
        if grid_list and len(grid_list) > 0:
            for grid in grid_list:
                # Get the pharmacy price.
                pharmacy_name = grid.find("p", {"class": "list-title"}).text

                # Get price of the drug.
                price = grid.find("span", {"p", "price price-large"}).text

                pharmacy_price_list.append(
                    {
                        "pharmacy_name": pharmacy_name,
                        "price": price,
                    }
                )

        return pharmacy_price_list

    except (HTTPError, exceptions.RequestException, ValueError):
        return None


if __name__ == "__main__":
    # Enter a drug name and a zip code
    drug_name = input("Enter drug name: ").strip()
    zip_code = input("Enter zip code: ").strip()

    pharmacy_price_list: list | None = fetch_pharmacy_and_price_list(
        drug_name, zip_code
    )

    if pharmacy_price_list:
        print(f"\nSearch results for {drug_name} at location {zip_code}:")
        for pharmacy_price in pharmacy_price_list:
            name = pharmacy_price["pharmacy_name"]
            price = pharmacy_price["price"]

            print(f"Pharmacy: {name} Price: {price}")
    else:
        print(f"No results found for {drug_name}")


================================================
File: web_programming/get_amazon_product_data.py
================================================
"""
This file provides a function which will take a product name as input from the user,
and fetch from Amazon information about products of this name or category.  The product
information will include title, URL, price, ratings, and the discount available.
"""

from itertools import zip_longest

import requests
from bs4 import BeautifulSoup
from pandas import DataFrame


def get_amazon_product_data(product: str = "laptop") -> DataFrame:
    """
    Take a product name or category as input and return product information from Amazon
    including title, URL, price, ratings, and the discount available.
    """
    url = f"https://www.amazon.in/laptop/s?k={product}"
    header = {
        "User-Agent": (
            "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36"
            "(KHTML, like Gecko)Chrome/44.0.2403.157 Safari/537.36"
        ),
        "Accept-Language": "en-US, en;q=0.5",
    }
    soup = BeautifulSoup(
        requests.get(url, headers=header, timeout=10).text, features="lxml"
    )
    # Initialize a Pandas dataframe with the column titles
    data_frame = DataFrame(
        columns=[
            "Product Title",
            "Product Link",
            "Current Price of the product",
            "Product Rating",
            "MRP of the product",
            "Discount",
        ]
    )
    # Loop through each entry and store them in the dataframe
    for item, _ in zip_longest(
        soup.find_all(
            "div",
            attrs={"class": "s-result-item", "data-component-type": "s-search-result"},
        ),
        soup.find_all("div", attrs={"class": "a-row a-size-base a-color-base"}),
    ):
        try:
            product_title = item.h2.text
            product_link = "https://www.amazon.in/" + item.h2.a["href"]
            product_price = item.find("span", attrs={"class": "a-offscreen"}).text
            try:
                product_rating = item.find("span", attrs={"class": "a-icon-alt"}).text
            except AttributeError:
                product_rating = "Not available"
            try:
                product_mrp = (
                    "₹"
                    + item.find(
                        "span", attrs={"class": "a-price a-text-price"}
                    ).text.split("₹")[1]
                )
            except AttributeError:
                product_mrp = ""
            try:
                discount = float(
                    (
                        (
                            float(product_mrp.strip("₹").replace(",", ""))
                            - float(product_price.strip("₹").replace(",", ""))
                        )
                        / float(product_mrp.strip("₹").replace(",", ""))
                    )
                    * 100
                )
            except ValueError:
                discount = float("nan")
        except AttributeError:
            continue
        data_frame.loc[str(len(data_frame.index))] = [
            product_title,
            product_link,
            product_price,
            product_rating,
            product_mrp,
            discount,
        ]
    data_frame.loc[
        data_frame["Current Price of the product"] > data_frame["MRP of the product"],
        "MRP of the product",
    ] = " "
    data_frame.loc[
        data_frame["Current Price of the product"] > data_frame["MRP of the product"],
        "Discount",
    ] = " "
    data_frame.index += 1
    return data_frame


if __name__ == "__main__":
    product = "headphones"
    get_amazon_product_data(product).to_csv(f"Amazon Product Data for {product}.csv")


================================================
File: web_programming/get_imdb_top_250_movies_csv.py
================================================
from __future__ import annotations

import csv

import requests
from bs4 import BeautifulSoup


def get_imdb_top_250_movies(url: str = "") -> dict[str, float]:
    url = url or "https://www.imdb.com/chart/top/?ref_=nv_mv_250"
    soup = BeautifulSoup(requests.get(url, timeout=10).text, "html.parser")
    titles = soup.find_all("td", attrs="titleColumn")
    ratings = soup.find_all("td", class_="ratingColumn imdbRating")
    return {
        title.a.text: float(rating.strong.text)
        for title, rating in zip(titles, ratings)
    }


def write_movies(filename: str = "IMDb_Top_250_Movies.csv") -> None:
    movies = get_imdb_top_250_movies()
    with open(filename, "w", newline="") as out_file:
        writer = csv.writer(out_file)
        writer.writerow(["Movie title", "IMDb rating"])
        for title, rating in movies.items():
            writer.writerow([title, rating])


if __name__ == "__main__":
    write_movies()


================================================
File: web_programming/get_imdbtop.py.DISABLED
================================================
import bs4
import requests


def get_movie_data_from_soup(soup: bs4.element.ResultSet) -> dict[str, str]:
    return {
        "name": soup.h3.a.text,
        "genre": soup.find("span", class_="genre").text.strip(),
        "rating": soup.strong.text,
        "page_link": f"https://www.imdb.com{soup.a.get('href')}",
    }


def get_imdb_top_movies(num_movies: int = 5) -> tuple:
    """Get the top num_movies most highly rated movies from IMDB and
    return a tuple of dicts describing each movie's name, genre, rating, and URL.

    Args:
        num_movies: The number of movies to get. Defaults to 5.

    Returns:
        A list of tuples containing information about the top n movies.

    >>> len(get_imdb_top_movies(5))
    5
    >>> len(get_imdb_top_movies(-3))
    0
    >>> len(get_imdb_top_movies(4.99999))
    4
    """
    num_movies = int(float(num_movies))
    if num_movies < 1:
        return ()
    base_url = (
        "https://www.imdb.com/search/title?title_type="
        f"feature&sort=num_votes,desc&count={num_movies}"
    )
    source = bs4.BeautifulSoup(requests.get(base_url).content, "html.parser")
    return tuple(
        get_movie_data_from_soup(movie)
        for movie in source.find_all("div", class_="lister-item mode-advanced")
    )


if __name__ == "__main__":
    import json

    num_movies = int(input("How many movies would you like to see? "))
    print(
        ", ".join(
            json.dumps(movie, indent=4) for movie in get_imdb_top_movies(num_movies)
        )
    )


================================================
File: web_programming/get_ip_geolocation.py
================================================
import requests


# Function to get geolocation data for an IP address
def get_ip_geolocation(ip_address: str) -> str:
    try:
        # Construct the URL for the IP geolocation API
        url = f"https://ipinfo.io/{ip_address}/json"

        # Send a GET request to the API
        response = requests.get(url, timeout=10)

        # Check if the HTTP request was successful
        response.raise_for_status()

        # Parse the response as JSON
        data = response.json()

        # Check if city, region, and country information is available
        if "city" in data and "region" in data and "country" in data:
            location = f"Location: {data['city']}, {data['region']}, {data['country']}"
        else:
            location = "Location data not found."

        return location
    except requests.exceptions.RequestException as e:
        # Handle network-related exceptions
        return f"Request error: {e}"
    except ValueError as e:
        # Handle JSON parsing errors
        return f"JSON parsing error: {e}"


if __name__ == "__main__":
    # Prompt the user to enter an IP address
    ip_address = input("Enter an IP address: ")

    # Get the geolocation data and print it
    location = get_ip_geolocation(ip_address)
    print(location)


================================================
File: web_programming/get_top_billionaires.py
================================================
"""
CAUTION: You may get a json.decoding error.
This works for some of us but fails for others.
"""

from datetime import UTC, date, datetime

import requests
from rich import box
from rich import console as rich_console
from rich import table as rich_table

LIMIT = 10
TODAY = datetime.now(tz=UTC)
API_URL = (
    "https://www.forbes.com/forbesapi/person/rtb/0/position/true.json"
    "?fields=personName,gender,source,countryOfCitizenship,birthDate,finalWorth"
    f"&limit={LIMIT}"
)


def years_old(birth_timestamp: int, today: date | None = None) -> int:
    """
    Calculate the age in years based on the given birth date.  Only the year, month,
    and day are used in the calculation.  The time of day is ignored.

    Args:
        birth_timestamp: The date of birth.
        today: (useful for writing tests) or if None then datetime.date.today().

    Returns:
        int: The age in years.

    Examples:
    >>> today = date(2024, 1, 12)
    >>> years_old(birth_timestamp=datetime(1959, 11, 20).timestamp(), today=today)
    64
    >>> years_old(birth_timestamp=datetime(1970, 2, 13).timestamp(), today=today)
    53
    >>> all(
    ...     years_old(datetime(today.year - i, 1, 12).timestamp(), today=today) == i
    ...     for i in range(1, 111)
    ... )
    True
    """
    today = today or TODAY.date()
    birth_date = datetime.fromtimestamp(birth_timestamp, tz=UTC).date()
    return (today.year - birth_date.year) - (
        (today.month, today.day) < (birth_date.month, birth_date.day)
    )


def get_forbes_real_time_billionaires() -> list[dict[str, int | str]]:
    """
    Get the top 10 real-time billionaires using Forbes API.

    Returns:
        List of top 10 realtime billionaires data.
    """
    response_json = requests.get(API_URL, timeout=10).json()
    return [
        {
            "Name": person["personName"],
            "Source": person["source"],
            "Country": person["countryOfCitizenship"],
            "Gender": person["gender"],
            "Worth ($)": f"{person['finalWorth'] / 1000:.1f} Billion",
            "Age": str(years_old(person["birthDate"] / 1000)),
        }
        for person in response_json["personList"]["personsLists"]
    ]


def display_billionaires(forbes_billionaires: list[dict[str, int | str]]) -> None:
    """
    Display Forbes real-time billionaires in a rich table.

    Args:
        forbes_billionaires (list): Forbes top 10 real-time billionaires
    """

    table = rich_table.Table(
        title=f"Forbes Top {LIMIT} Real-Time Billionaires at {TODAY:%Y-%m-%d %H:%M}",
        style="green",
        highlight=True,
        box=box.SQUARE,
    )
    for key in forbes_billionaires[0]:
        table.add_column(key)

    for billionaire in forbes_billionaires:
        table.add_row(*billionaire.values())

    rich_console.Console().print(table)


if __name__ == "__main__":
    from doctest import testmod

    testmod()
    display_billionaires(get_forbes_real_time_billionaires())


================================================
File: web_programming/get_top_hn_posts.py
================================================
from __future__ import annotations

import requests


def get_hackernews_story(story_id: str) -> dict:
    url = f"https://hacker-news.firebaseio.com/v0/item/{story_id}.json?print=pretty"
    return requests.get(url, timeout=10).json()


def hackernews_top_stories(max_stories: int = 10) -> list[dict]:
    """
    Get the top max_stories posts from HackerNews - https://news.ycombinator.com/
    """
    url = "https://hacker-news.firebaseio.com/v0/topstories.json?print=pretty"
    story_ids = requests.get(url, timeout=10).json()[:max_stories]
    return [get_hackernews_story(story_id) for story_id in story_ids]


def hackernews_top_stories_as_markdown(max_stories: int = 10) -> str:
    stories = hackernews_top_stories(max_stories)
    return "\n".join("* [{title}]({url})".format(**story) for story in stories)


if __name__ == "__main__":
    print(hackernews_top_stories_as_markdown())


================================================
File: web_programming/get_user_tweets.py.DISABLED
================================================
import csv

import tweepy

# Twitter API credentials
consumer_key = ""
consumer_secret = ""
access_key = ""
access_secret = ""


def get_all_tweets(screen_name: str) -> None:
    # authorize twitter, initialize tweepy
    auth = tweepy.OAuthHandler(consumer_key, consumer_secret)
    auth.set_access_token(access_key, access_secret)
    api = tweepy.API(auth)

    # initialize a list to hold all the tweepy Tweets
    alltweets = []

    # make initial request for most recent tweets (200 is the maximum allowed count)
    new_tweets = api.user_timeline(screen_name=screen_name, count=200)

    # save most recent tweets
    alltweets.extend(new_tweets)

    # save the id of the oldest tweet less one
    oldest = alltweets[-1].id - 1

    # keep grabbing tweets until there are no tweets left to grab
    while len(new_tweets) > 0:
        print(f"getting tweets before {oldest}")

        # all subsequent requests use the max_id param to prevent duplicates
        new_tweets = api.user_timeline(
            screen_name=screen_name, count=200, max_id=oldest
        )

        # save most recent tweets
        alltweets.extend(new_tweets)

        # update the id of the oldest tweet less one
        oldest = alltweets[-1].id - 1

        print(f"...{len(alltweets)} tweets downloaded so far")

    # transform the tweepy tweets into a 2D array that will populate the csv
    outtweets = [[tweet.id_str, tweet.created_at, tweet.text] for tweet in alltweets]

    # write the csv
    with open(f"new_{screen_name}_tweets.csv", "w") as f:
        writer = csv.writer(f)
        writer.writerow(["id", "created_at", "text"])
        writer.writerows(outtweets)


if __name__ == "__main__":
    # pass in the username of the account you want to download
    get_all_tweets("FirePing32")


================================================
File: web_programming/giphy.py
================================================
#!/usr/bin/env python3
import requests

giphy_api_key = "YOUR API KEY"
# Can be fetched from https://developers.giphy.com/dashboard/


def get_gifs(query: str, api_key: str = giphy_api_key) -> list:
    """
    Get a list of URLs of GIFs based on a given query..
    """
    formatted_query = "+".join(query.split())
    url = f"https://api.giphy.com/v1/gifs/search?q={formatted_query}&api_key={api_key}"
    gifs = requests.get(url, timeout=10).json()["data"]
    return [gif["url"] for gif in gifs]


if __name__ == "__main__":
    print("\n".join(get_gifs("space ship")))


================================================
File: web_programming/instagram_crawler.py
================================================
#!/usr/bin/env python3
from __future__ import annotations

import json

import requests
from bs4 import BeautifulSoup
from fake_useragent import UserAgent

headers = {"UserAgent": UserAgent().random}


def extract_user_profile(script) -> dict:
    """
    May raise json.decoder.JSONDecodeError
    """
    data = script.contents[0]
    info = json.loads(data[data.find('{"config"') : -1])
    return info["entry_data"]["ProfilePage"][0]["graphql"]["user"]


class InstagramUser:
    """
    Class Instagram crawl instagram user information

    Usage: (doctest failing on GitHub Actions)
    # >>> instagram_user = InstagramUser("github")
    # >>> instagram_user.is_verified
    True
    # >>> instagram_user.biography
    'Built for developers.'
    """

    def __init__(self, username):
        self.url = f"https://www.instagram.com/{username}/"
        self.user_data = self.get_json()

    def get_json(self) -> dict:
        """
        Return a dict of user information
        """
        html = requests.get(self.url, headers=headers, timeout=10).text
        scripts = BeautifulSoup(html, "html.parser").find_all("script")
        try:
            return extract_user_profile(scripts[4])
        except (json.decoder.JSONDecodeError, KeyError):
            return extract_user_profile(scripts[3])

    def __repr__(self) -> str:
        return f"{self.__class__.__name__}('{self.username}')"

    def __str__(self) -> str:
        return f"{self.fullname} ({self.username}) is {self.biography}"

    @property
    def username(self) -> str:
        return self.user_data["username"]

    @property
    def fullname(self) -> str:
        return self.user_data["full_name"]

    @property
    def biography(self) -> str:
        return self.user_data["biography"]

    @property
    def email(self) -> str:
        return self.user_data["business_email"]

    @property
    def website(self) -> str:
        return self.user_data["external_url"]

    @property
    def number_of_followers(self) -> int:
        return self.user_data["edge_followed_by"]["count"]

    @property
    def number_of_followings(self) -> int:
        return self.user_data["edge_follow"]["count"]

    @property
    def number_of_posts(self) -> int:
        return self.user_data["edge_owner_to_timeline_media"]["count"]

    @property
    def profile_picture_url(self) -> str:
        return self.user_data["profile_pic_url_hd"]

    @property
    def is_verified(self) -> bool:
        return self.user_data["is_verified"]

    @property
    def is_private(self) -> bool:
        return self.user_data["is_private"]


def test_instagram_user(username: str = "github") -> None:
    """
    A self running doctest
    >>> test_instagram_user()
    """
    import os

    if os.environ.get("CI"):
        return  # test failing on GitHub Actions
    instagram_user = InstagramUser(username)
    assert instagram_user.user_data
    assert isinstance(instagram_user.user_data, dict)
    assert instagram_user.username == username
    if username != "github":
        return
    assert instagram_user.fullname == "GitHub"
    assert instagram_user.biography == "Built for developers."
    assert instagram_user.number_of_posts > 150
    assert instagram_user.number_of_followers > 120000
    assert instagram_user.number_of_followings > 15
    assert instagram_user.email == "support@github.com"
    assert instagram_user.website == "https://github.com/readme"
    assert instagram_user.profile_picture_url.startswith("https://instagram.")
    assert instagram_user.is_verified is True
    assert instagram_user.is_private is False


if __name__ == "__main__":
    import doctest

    doctest.testmod()
    instagram_user = InstagramUser("github")
    print(instagram_user)
    print(f"{instagram_user.number_of_posts = }")
    print(f"{instagram_user.number_of_followers = }")
    print(f"{instagram_user.number_of_followings = }")
    print(f"{instagram_user.email = }")
    print(f"{instagram_user.website = }")
    print(f"{instagram_user.profile_picture_url = }")
    print(f"{instagram_user.is_verified = }")
    print(f"{instagram_user.is_private = }")


================================================
File: web_programming/instagram_pic.py
================================================
from datetime import UTC, datetime

import requests
from bs4 import BeautifulSoup


def download_image(url: str) -> str:
    """
    Download an image from a given URL by scraping the 'og:image' meta tag.

    Parameters:
        url: The URL to scrape.

    Returns:
        A message indicating the result of the operation.
    """
    try:
        response = requests.get(url, timeout=10)
        response.raise_for_status()
    except requests.exceptions.RequestException as e:
        return f"An error occurred during the HTTP request to {url}: {e!r}"

    soup = BeautifulSoup(response.text, "html.parser")
    image_meta_tag = soup.find("meta", {"property": "og:image"})
    if not image_meta_tag:
        return "No meta tag with property 'og:image' was found."

    image_url = image_meta_tag.get("content")
    if not image_url:
        return f"Image URL not found in meta tag {image_meta_tag}."

    try:
        image_data = requests.get(image_url, timeout=10).content
    except requests.exceptions.RequestException as e:
        return f"An error occurred during the HTTP request to {image_url}: {e!r}"
    if not image_data:
        return f"Failed to download the image from {image_url}."

    file_name = f"{datetime.now(tz=UTC).astimezone():%Y-%m-%d_%H:%M:%S}.jpg"
    with open(file_name, "wb") as out_file:
        out_file.write(image_data)
    return f"Image downloaded and saved in the file {file_name}"


if __name__ == "__main__":
    url = input("Enter image URL: ").strip() or "https://www.instagram.com"
    print(f"download_image({url}): {download_image(url)}")


================================================
File: web_programming/instagram_video.py
================================================
from datetime import UTC, datetime

import requests


def download_video(url: str) -> bytes:
    base_url = "https://downloadgram.net/wp-json/wppress/video-downloader/video?url="
    video_url = requests.get(base_url + url, timeout=10).json()[0]["urls"][0]["src"]
    return requests.get(video_url, timeout=10).content


if __name__ == "__main__":
    url = input("Enter Video/IGTV url: ").strip()
    file_name = f"{datetime.now(tz=UTC).astimezone():%Y-%m-%d_%H:%M:%S}.mp4"
    with open(file_name, "wb") as fp:
        fp.write(download_video(url))
    print(f"Done. Video saved to disk as {file_name}.")


================================================
File: web_programming/nasa_data.py
================================================
import shutil

import requests


def get_apod_data(api_key: str) -> dict:
    """
    Get the APOD(Astronomical Picture of the day) data
    Get your API Key from: https://api.nasa.gov/
    """
    url = "https://api.nasa.gov/planetary/apod"
    return requests.get(url, params={"api_key": api_key}, timeout=10).json()


def save_apod(api_key: str, path: str = ".") -> dict:
    apod_data = get_apod_data(api_key)
    img_url = apod_data["url"]
    img_name = img_url.split("/")[-1]
    response = requests.get(img_url, stream=True, timeout=10)

    with open(f"{path}/{img_name}", "wb+") as img_file:
        shutil.copyfileobj(response.raw, img_file)
    del response
    return apod_data


def get_archive_data(query: str) -> dict:
    """
    Get the data of a particular query from NASA archives
    """
    url = "https://images-api.nasa.gov/search"
    return requests.get(url, params={"q": query}, timeout=10).json()


if __name__ == "__main__":
    print(save_apod("YOUR API KEY"))
    apollo_2011_items = get_archive_data("apollo 2011")["collection"]["items"]
    print(apollo_2011_items[0]["data"][0]["description"])


================================================
File: web_programming/open_google_results.py
================================================
import webbrowser
from sys import argv
from urllib.parse import parse_qs, quote

import requests
from bs4 import BeautifulSoup
from fake_useragent import UserAgent

if __name__ == "__main__":
    query = "%20".join(argv[1:]) if len(argv) > 1 else quote(str(input("Search: ")))

    print("Googling.....")

    url = f"https://www.google.com/search?q={query}&num=100"

    res = requests.get(
        url,
        headers={"User-Agent": str(UserAgent().random)},
        timeout=10,
    )

    try:
        link = (
            BeautifulSoup(res.text, "html.parser")
            .find("div", attrs={"class": "yuRUbf"})
            .find("a")
            .get("href")
        )

    except AttributeError:
        link = parse_qs(
            BeautifulSoup(res.text, "html.parser")
            .find("div", attrs={"class": "kCrYT"})
            .find("a")
            .get("href")
        )["url"][0]

    webbrowser.open(link)


================================================
File: web_programming/random_anime_character.py
================================================
import os

import requests
from bs4 import BeautifulSoup
from fake_useragent import UserAgent

headers = {"UserAgent": UserAgent().random}
URL = "https://www.mywaifulist.moe/random"


def save_image(image_url: str, image_title: str) -> None:
    """
    Saves the image of anime character
    """
    image = requests.get(image_url, headers=headers, timeout=10)
    with open(image_title, "wb") as file:
        file.write(image.content)


def random_anime_character() -> tuple[str, str, str]:
    """
    Returns the Title, Description, and Image Title of a random anime character .
    """
    soup = BeautifulSoup(
        requests.get(URL, headers=headers, timeout=10).text, "html.parser"
    )
    title = soup.find("meta", attrs={"property": "og:title"}).attrs["content"]
    image_url = soup.find("meta", attrs={"property": "og:image"}).attrs["content"]
    description = soup.find("p", id="description").get_text()
    _, image_extension = os.path.splitext(os.path.basename(image_url))
    image_title = title.strip().replace(" ", "_")
    image_title = f"{image_title}{image_extension}"
    save_image(image_url, image_title)
    return (title, description, image_title)


if __name__ == "__main__":
    title, desc, image_title = random_anime_character()
    print(f"{title}\n\n{desc}\n\nImage saved : {image_title}")


================================================
File: web_programming/recaptcha_verification.py
================================================
"""
Recaptcha is a free captcha service offered by Google in order to secure websites and
forms.  At https://www.google.com/recaptcha/admin/create you can create new recaptcha
keys and see the keys that your have already created.
* Keep in mind that recaptcha doesn't work with localhost
When you create a recaptcha key, your will get two separate keys: ClientKey & SecretKey.
ClientKey should be kept in your site's front end
SecretKey should be kept in your site's  back end

# An example HTML login form with recaptcha tag is shown below

    <form action="" method="post">
        <h2 class="text-center">Log in</h2>
        {% csrf_token %}
        <div class="form-group">
            <input type="text" name="username" required="required">
        </div>
        <div class="form-group">
            <input type="password" name="password" required="required">
        </div>
        <div class="form-group">
            <button type="submit">Log in</button>
        </div>
        <!-- Below is the recaptcha tag of html -->
        <div class="g-recaptcha" data-sitekey="ClientKey"></div>
    </form>

    <!-- Below is the recaptcha script to be kept inside html tag -->
    <script src="https://www.google.com/recaptcha/api.js" async defer></script>

Below a Django function for the views.py file contains a login form for demonstrating
recaptcha verification.
"""

import requests

try:
    from django.contrib.auth import authenticate, login
    from django.shortcuts import redirect, render
except ImportError:
    authenticate = login = render = redirect = print


def login_using_recaptcha(request):
    # Enter your recaptcha secret key here
    secret_key = "secretKey"  # noqa: S105
    url = "https://www.google.com/recaptcha/api/siteverify"

    # when method is not POST, direct user to login page
    if request.method != "POST":
        return render(request, "login.html")

    # from the frontend, get username, password, and client_key
    username = request.POST.get("username")
    password = request.POST.get("password")
    client_key = request.POST.get("g-recaptcha-response")

    # post recaptcha response to Google's recaptcha api
    response = requests.post(
        url, data={"secret": secret_key, "response": client_key}, timeout=10
    )
    # if the recaptcha api verified our keys
    if response.json().get("success", False):
        # authenticate the user
        user_in_database = authenticate(request, username=username, password=password)
        if user_in_database:
            login(request, user_in_database)
            return redirect("/your-webpage")
    return render(request, "login.html")


================================================
File: web_programming/reddit.py
================================================
from __future__ import annotations

import requests

valid_terms = set(
    """approved_at_utc approved_by author_flair_background_color
author_flair_css_class author_flair_richtext author_flair_template_id author_fullname
author_premium can_mod_post category clicked content_categories created_utc downs
edited gilded gildings hidden hide_score is_created_from_ads_ui is_meta
is_original_content is_reddit_media_domain is_video link_flair_css_class
link_flair_richtext link_flair_text link_flair_text_color media_embed mod_reason_title
name permalink pwls quarantine saved score secure_media secure_media_embed selftext
subreddit subreddit_name_prefixed subreddit_type thumbnail title top_awarded_type
total_awards_received ups upvote_ratio url user_reports""".split()
)


def get_subreddit_data(
    subreddit: str, limit: int = 1, age: str = "new", wanted_data: list | None = None
) -> dict:
    """
    subreddit : Subreddit to query
    limit : Number of posts to fetch
    age : ["new", "top", "hot"]
    wanted_data : Get only the required data in the list
    """
    wanted_data = wanted_data or []
    if invalid_search_terms := ", ".join(sorted(set(wanted_data) - valid_terms)):
        msg = f"Invalid search term: {invalid_search_terms}"
        raise ValueError(msg)
    response = requests.get(
        f"https://reddit.com/r/{subreddit}/{age}.json?limit={limit}",
        headers={"User-agent": "A random string"},
        timeout=10,
    )
    if response.status_code == 429:
        raise requests.HTTPError(response=response)

    data = response.json()
    if not wanted_data:
        return {id_: data["data"]["children"][id_] for id_ in range(limit)}

    data_dict = {}
    for id_ in range(limit):
        data_dict[id_] = {
            item: data["data"]["children"][id_]["data"][item] for item in wanted_data
        }
    return data_dict


if __name__ == "__main__":
    # If you get Error 429, that means you are rate limited.Try after some time
    print(get_subreddit_data("learnpython", wanted_data=["title", "url", "selftext"]))


================================================
File: web_programming/search_books_by_isbn.py
================================================
"""
Get book and author data from https://openlibrary.org

ISBN: https://en.wikipedia.org/wiki/International_Standard_Book_Number
"""

from json import JSONDecodeError  # Workaround for requests.exceptions.JSONDecodeError

import requests


def get_openlibrary_data(olid: str = "isbn/0140328726") -> dict:
    """
    Given an 'isbn/0140328726', return book data from Open Library as a Python dict.
    Given an '/authors/OL34184A', return authors data as a Python dict.
    This code must work for olids with or without a leading slash ('/').

    # Comment out doctests if they take too long or have results that may change
    # >>> get_openlibrary_data(olid='isbn/0140328726')  # doctest: +ELLIPSIS
    {'publishers': ['Puffin'], 'number_of_pages': 96, 'isbn_10': ['0140328726'], ...
    # >>> get_openlibrary_data(olid='/authors/OL7353617A')  # doctest: +ELLIPSIS
    {'name': 'Adrian Brisku', 'created': {'type': '/type/datetime', ...
    """
    new_olid = olid.strip().strip("/")  # Remove leading/trailing whitespace & slashes
    if new_olid.count("/") != 1:
        msg = f"{olid} is not a valid Open Library olid"
        raise ValueError(msg)
    return requests.get(f"https://openlibrary.org/{new_olid}.json", timeout=10).json()


def summarize_book(ol_book_data: dict) -> dict:
    """
    Given Open Library book data, return a summary as a Python dict.
    """
    desired_keys = {
        "title": "Title",
        "publish_date": "Publish date",
        "authors": "Authors",
        "number_of_pages": "Number of pages:",
        "first_sentence": "First sentence",
        "isbn_10": "ISBN (10)",
        "isbn_13": "ISBN (13)",
    }
    data = {better_key: ol_book_data[key] for key, better_key in desired_keys.items()}
    data["Authors"] = [
        get_openlibrary_data(author["key"])["name"] for author in data["Authors"]
    ]
    data["First sentence"] = data["First sentence"]["value"]
    for key, value in data.items():
        if isinstance(value, list):
            data[key] = ", ".join(value)
    return data


if __name__ == "__main__":
    import doctest

    doctest.testmod()

    while True:
        isbn = input("\nEnter the ISBN code to search (or 'quit' to stop): ").strip()
        if isbn.lower() in ("", "q", "quit", "exit", "stop"):
            break

        if len(isbn) not in (10, 13) or not isbn.isdigit():
            print(f"Sorry, {isbn} is not a valid ISBN.  Please, input a valid ISBN.")
            continue

        print(f"\nSearching Open Library for ISBN: {isbn}...\n")

        try:
            book_summary = summarize_book(get_openlibrary_data(f"isbn/{isbn}"))
            print("\n".join(f"{key}: {value}" for key, value in book_summary.items()))
        except JSONDecodeError:  # Workaround for requests.exceptions.RequestException:
            print(f"Sorry, there are no results for ISBN: {isbn}.")


================================================
File: web_programming/slack_message.py
================================================
# Created by sarathkaul on 12/11/19

import requests


def send_slack_message(message_body: str, slack_url: str) -> None:
    headers = {"Content-Type": "application/json"}
    response = requests.post(
        slack_url, json={"text": message_body}, headers=headers, timeout=10
    )
    if response.status_code != 200:
        msg = (
            "Request to slack returned an error "
            f"{response.status_code}, the response is:\n{response.text}"
        )
        raise ValueError(msg)


if __name__ == "__main__":
    # Set the slack url to the one provided by Slack when you create the webhook at
    # https://my.slack.com/services/new/incoming-webhook/
    send_slack_message("<YOUR MESSAGE BODY>", "<SLACK CHANNEL URL>")


================================================
File: web_programming/test_fetch_github_info.py
================================================
import json

import requests

from .fetch_github_info import AUTHENTICATED_USER_ENDPOINT, fetch_github_info


def test_fetch_github_info(monkeypatch):
    class FakeResponse:
        def __init__(self, content) -> None:
            assert isinstance(content, (bytes, str))
            self.content = content

        def json(self):
            return json.loads(self.content)

    def mock_response(*args, **kwargs):
        assert args[0] == AUTHENTICATED_USER_ENDPOINT
        assert "Authorization" in kwargs["headers"]
        assert kwargs["headers"]["Authorization"].startswith("token ")
        assert "Accept" in kwargs["headers"]
        return FakeResponse(b'{"login":"test","id":1}')

    monkeypatch.setattr(requests, "get", mock_response)
    result = fetch_github_info("token")
    assert result["login"] == "test"
    assert result["id"] == 1


================================================
File: web_programming/world_covid19_stats.py
================================================
#!/usr/bin/env python3

"""
Provide the current worldwide COVID-19 statistics.
This data is being scrapped from 'https://www.worldometers.info/coronavirus/'.
"""

import requests
from bs4 import BeautifulSoup


def world_covid19_stats(url: str = "https://www.worldometers.info/coronavirus") -> dict:
    """
    Return a dict of current worldwide COVID-19 statistics
    """
    soup = BeautifulSoup(requests.get(url, timeout=10).text, "html.parser")
    keys = soup.findAll("h1")
    values = soup.findAll("div", {"class": "maincounter-number"})
    keys += soup.findAll("span", {"class": "panel-title"})
    values += soup.findAll("div", {"class": "number-table-main"})
    return {key.text.strip(): value.text.strip() for key, value in zip(keys, values)}


if __name__ == "__main__":
    print("\033[1m COVID-19 Status of the World \033[0m\n")
    print("\n".join(f"{key}\n{value}" for key, value in world_covid19_stats().items()))


