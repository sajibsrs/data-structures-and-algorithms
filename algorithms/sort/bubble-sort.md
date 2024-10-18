# Bubble Sort Algorithm
Bubble Sort is a simple comparison-based sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. The pass through the list is repeated until the list is sorted.

> Worst case: When all elements are sorted in reverse order.

## How it works
This implementation sorts values in ascending order (small to large).

Input:
```txt
8, 5, 7, 2, 6
```

Steps:
```txt
compared: 8 and 5
swapped: 5 and 8
compared: 8 and 7
swapped: 7 and 8
compared: 8 and 2
swapped: 2 and 8
compared: 8 and 6
swapped: 6 and 8

compared: 5 and 7
compared: 7 and 2
swapped: 2 and 7
compared: 7 and 6
swapped: 6 and 7

compared: 5 and 2
swapped: 2 and 5

compared: 5 and 6
compared: 2 and 5
```

Analysis:
```txt
comparisons: 10
swaps: 7
```

Result:
```txt
2, 5, 6, 7, 8
```

## Implementation
Definition:
```php
function bubbleSort(array &$arr): void
{
    $n = count($arr);

    do {
        for ($i = 0; $i < $n - 1; $i++) {
            $swapped = false;

            if ($arr[$i] > $arr[$i + 1]) {
                [$arr[$i], $arr[$i + 1]] = [$arr[$i + 1], $arr[$i]];  // List assignment or array destructure
                $swapped = true;
            }
        }
        $n--;
    } while ($swapped);
}
```

Usage:
```php
$arr = [8, 5, 7, 2, 6];

bubbleSort($arr);
```

Output:
```txt
2, 5, 6, 7, 8
```

## Implementation

## Performance Analysis
| Operation        | Time Complexity | Space Complexity |
| ---------------- | --------------- | ---------------- |
| **Best Case**    | O(n)            | O(1)             |
| **Average Case** | O(n²)           | O(1)             |
| **Worst Case**   | O(n²)           | O(1)             |

