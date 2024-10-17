# Linear Search
Linear search is a simple searching algorithm that checks each element in a list one by one, from the beginning to the end, until the desired element is found or the list ends.

## Algorithm
1. Start from the first element of the array.
2. Compare the current element with the target value.
3. If the current element matches the target, return its index.
4. If not, move to the next element.
5. Repeat steps 2-4 until the end of the array is reached.
6. If the target element is not found, return `null`.

## Implementation:
```php
function linearSearch(array $input, $target): ?int
{
    foreach ($input as $index => $element) {
        if ($element === $target) {
            return $index;
        }
    }
    return null;
}
```

## Performance Analysis
| Complexity | Best Case | Average Case | Worst Case | Space Complexity |
| ---------- | --------- | ------------ | ---------- | ---------------- |
| **Time**   | O(1)      | O(n)         | O(n)       | O(1)             |
