# Stack Data Structure
A stack is a linear data structure that follows the Last In, First Out (LIFO) principle. The most recently added element is the first one to be removed.

Operations:
- **Push:** Adds an element to the top of the stack.
- **Pop:** Removes and returns the top element.
- **Peek:** Returns the top element without removing it.

## Implementation
```php
class Stack
{
    private array $stack = [];

    public function push(mixed $item): void
    {
        $this->stack[] = $item;
    }

    public function pop(): mixed
    {
        if ($this->isEmpty()) {
            throw new UnderflowException("Stack is empty.");
        }

        return array_pop($this->stack);
    }

    public function peek(): mixed
    {
        if ($this->isEmpty()) {
            throw new UnderflowException("Stack is empty.");
        }

        return end($this->stack);
    }

    public function size(): int
    {
        return count($this->stack);
    }

    public function isEmpty(): bool
    {
        return empty($this->stack);
    }
}
```

Usage:
```php
$stack = new Stack();

$stack->push(10);
$stack->push(20);

echo $stack->peek();
```

Result:
```txt
20
```

## Performance Analysis

| Operation   | Time Complexity | Space Complexity |
| ----------- | --------------- | ---------------- |
| **Push**    | O(1)            | O(1)             |
| **Pop**     | O(1)            | O(1)             |
| **Peek**    | O(1)            | O(1)             |
| **IsEmpty** | O(1)            | O(1)             |
