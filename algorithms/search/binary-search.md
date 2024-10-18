# Binary Search
Binary search is an efficient algorithm used to find the position of a target value within a sorted array. It works by repeatedly dividing the search interval in half. If the target value is less than the middle element, the search continues on the left half, otherwise on the right half.

> Prerequisite: The array must be sorted.

## Algorithm
1. Set two pointers, low to the first index and high to the last index of the array.
2. Calculate the middle index.
3. Compare the middle element with the target.
   * If it matches, return the middle index.
   * If the target is less than the middle element, repeat the search in the left half.
   * If the target is greater, repeat in the right half.

4. If low exceeds high, the element is not found, return `-1`.

## Implementation
Definition:
```php
function binarySearch(array $arr, $target): int
{
    $low = 0;
    $high = count($arr) - 1;

    while ($low <= $high) {
        $mid = (int)(($low + $high) / 2);

        if ($arr[$mid] == $target) {
            return $mid;
        } elseif ($arr[$mid] < $target) {
            $low = $mid + 1;
        } else {
            $high = $mid - 1;
        }
    }

    return -1;
}
```

Usage:
```php
$arr = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
echo binarySearch($arr, 8);
```

Output:
```txt
8
```

## Performance Analysis
| Complexity | Best Case | Average Case | Worst Case | Space Complexity |
| ---------- | --------- | ------------ | ---------- | ---------------- |
| **Time**   | O(1)      | O(log n)     | O(log n)   | O(1)             |
