# Binary Search Tree Data Structure
A Binary Search Tree (BST) is a binary tree in which each node has at most two children. Additionally, it follows the binary search property:

- All levels are completely filled, except the last level.
- The last level is filled from left to right, with no gaps between nodes.

## Implementation
```php
class Node
{
    public ?Node $left = null;
    public ?Node $right = null;

    public function __construct(public int $data) {}
}

class BinarySearchTree
{
    public ?Node $root = null;

    public function insert(int $data): void
    {
        $this->root = $this->insertNode($this->root, $data);
    }

    private function insertNode(?Node $node, int $data): Node
    {
        if ($node === null) {
            return new Node($data);
        }

        if ($data < $node->data) {
            $node->left = $this->insertNode($node->left, $data);
        } elseif ($data > $node->data) {
            $node->right = $this->insertNode($node->right, $data);
        }

        return $node;
    }
}
```

## Adding Node
Base Case:

If the current node is null (i.e., we've reached an empty spot), create a new `Node` with the given data and return it.

Recursive Case:

- If the value to be inserted is less than the current node's value, recursively insert the value into the left subtree.
- If the value to be inserted is greater than the current node's value, recursively insert the value into the right subtree.

```php
$bst = new BinarySearchTree();

$bst->insert(50);
$bst->insert(30);
$bst->insert(70);
$bst->insert(20);
$bst->insert(40);
$bst->insert(60);
$bst->insert(80);
```

## Traversal
### Pre-order Traversal
```php
function preOrderTraversal(?Node $node): void
{
    if ($node === null) {
        return;
    }

    echo "{$node->data}, ";

    preOrderTraversal($node->left);
    preOrderTraversal($node->right);
}
```

Usage:
```php
preOrderTraversal($bst->root);
```

Output:
```txt
50, 30, 20, 40, 70, 60, 80,
```

## Removing Node
Base Case:

If the current node is null, the value isn't found in the tree, and the removal ends.

Recursive Search:

- If the value to be removed is less than the current node's value, search and remove from the left subtree.
- If the value to be removed is greater than the current node's value, search and remove from the right subtree.

Node Found:

- Case 1: Node has no children (a leaf node): Simply remove the node by returning null.
- Case 2: Node has one child: Replace the node with its child (either left or right).
- Case 3: Node has two children: Replace the node with its in-order successor (the smallest value in the right subtree). Then recursively remove the in-order successor from the right subtree.

Return the updated node:

After deletion, the updated subtree is returned to maintain the BST property.

```php
class Node
{
    public ?Node $left = null;
    public ?Node $right = null;

    public function __construct(public int $data) {}
}

class BinarySearchTree
{
    public ?Node $root = null;

    public function insert(int $data): void
    {
        $this->root = $this->insertNode($this->root, $data);
    }

    public function remove(int $data): void
    {
        $this->root = $this->removeNode($this->root, $data);
    }

    private function insertNode(?Node $node, int $data): Node
    {
        if ($node === null) {
            return new Node($data);
        }

        if ($data < $node->data) {
            $node->left = $this->insertNode($node->left, $data);
        } elseif ($data > $node->data) {
            $node->right = $this->insertNode($node->right, $data);
        }

        return $node;
    }

    private function removeNode(?Node $node, int $data): ?Node
    {
        if ($node === null) {
            return null;
        }

        if ($data < $node->data) {
            $node->left = $this->removeNode($node->left, $data);
        } elseif ($data > $node->data) {
            $node->right = $this->removeNode($node->right, $data);
        } else {
            if ($node->left === null) {
                return $node->right;
            } elseif ($node->right === null) {
                return $node->left;
            }
            $minNode = $this->getMin($node->right);
            $node->data = $minNode->data;
            $node->right = $this->removeNode($node->right, $minNode->data);
        }

        return $node;
    }

    private function getMin(Node $node): Node
    {
        while ($node->left !== null) {
            $node = $node->left;
        }

        return $node;
    }
}
```

Usage:
```php
$bst->remove(50);

preOrderTraversal($bst->root);
```

Output:
```txt
60, 30, 20, 40, 70, 80,
```

## Performance Analysis
| Operation  | Best Case (Balanced) | Average Case (Balanced) | Worst Case (Unbalanced) |
| ---------- | -------------------- | ----------------------- | ----------------------- |
| **Insert** | O(log n)             | O(log n)                | O(n)                    |
| **Remove** | O(log n)             | O(log n)                | O(n)                    |
| **Search** | O(log n)             | O(log n)                | O(n)                    |
