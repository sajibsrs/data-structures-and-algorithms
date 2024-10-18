# Selection Sort Algorithm
Selection Sort is a comparison-based algorithm that repeatedly compares and selects the smallest element from the unsorted part and swaps it with the first unsorted element from the left side, thus growing the sorted part.

> Worst case: When all elements are sorted in reverse order.

## How it works
This implementation sorts values in ascending order (small to large).

Input:
```txt
8, 5, 7, 2, 6
```

Steps:
```txt
minimum: 8
compared: 5 and 8
new minimum: 5
compared: 7 and 5
compared: 2 and 5
new minimum: 2
compared: 6 and 2
swapped: 8 and 2

minimum: 5
compared: 7 and 5
compared: 8 and 5
compared: 6 and 5

minimum: 7
compared: 8 and 7
compared: 6 and 7
new minimum: 6
swapped: 7 and 6

minimum: 8
compared: 7 and 8
new minimum: 7
swapped: 8 and 7
```

Analysis:
```txt
comparisons: 10
swaps: 3
```

Result:
```txt
2, 5, 6, 7, 8
```

## Implementation
Definition:
```php
function selectionSort(array &$arr): void
{
    $n = count($arr);

    for ($i = 0; $i < $n; $i++) {
        $min = $i;

        for ($j  = $i + 1; $j < $n; $j++) {
            if ($arr[$j] < $arr[$min]) {
                $min = $j;
            }
        }

        if ($min !== $i) {
            [$arr[$i], $arr[$min]] = [$arr[$min], $arr[$i]];
        }
    }
}
```

Usage:
```php
$arr = [8, 5, 7, 2, 6];

selectionSort($arr);
```

Output:
```txt
2, 5, 6, 7, 8
```

## Implementation

## Performance Analysis
| Operation        | Time Complexity | Space Complexity |
| ---------------- | --------------- | ---------------- |
| **Best Case**    | O(n²)           | O(1)             |
| **Average Case** | O(n²)           | O(1)             |
| **Worst Case**   | O(n²)           | O(1)             |
