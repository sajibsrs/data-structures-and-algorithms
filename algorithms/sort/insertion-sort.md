# Insertion Sort
Insertion Sort is a simple sorting algorithm that builds the sorted array one element at a time. It works similarly to how you would sort playing cards in your hand. The algorithm removes one element from the input array, finds the location it belongs in the sorted part, and inserts it there.

> Worst case: When all elements are sorted in reverse order.

## How it works
This implementation sorts values in ascending order (small to large).

Input:
```txt
8, 5, 7, 2, 6
```

Steps:
```txt
current value: 5
compared: 8 and 5
moved: 8 to position of 5
moved: 5 to position of 8
current value: 7
compared: 8 and 7
moved: 8 to position of 7
moved: 7 to position of 8
current value: 2
compared: 8 and 2
moved: 8 to position of 2
moved: 7 to position of 8
moved: 5 to position of 7
moved: 2 to position of 5
current value: 6
compared: 8 and 6
moved: 8 to position of 6
moved: 7 to position of 8
moved: 6 to position of 7
```

Analysis:
```txt
comparisons: 4
swaps: 11
```

Result:
```txt
2, 5, 6, 7, 8
```

## Implementation
Definition:
```php
function insertionSort(array &$arr): void
{
    $n = count($arr);

    for ($i = 1; $i < $n; $i++) {
        $key = $arr[$i];
        $j = $i - 1;

        while ($j >= 0 && $arr[$j] > $key) {
            $arr[$j + 1] = $arr[$j];
            $j--;
        }
        $arr[$j + 1] = $key;
    }
}
```

Usage:
```php
$arr = [8, 5, 7, 2, 6];

insertionSort($arr);
```

Output:
```txt
2, 5, 6, 7, 8
```

## Performance Analysis
| Operation        | Time Complexity | Space Complexity |
| ---------------- | --------------- | ---------------- |
| **Best Case**    | O(n)            | O(1)             |
| **Average Case** | O(n²)           | O(1)             |
| **Worst Case**   | O(n²)           | O(1)             |


