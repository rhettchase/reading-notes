# Class 15 Reading Notes - Trees

**Trees**
- Trees are hierarchical data structures that consist of nodes connected by edges.
- Commonly used for various data storage and searching applications.
- Nodes in a tree can contain values/data and references to other nodes.

**Common Terminology**
- Node: A component in a tree that may contain values/data and references to other nodes.
- Root: The topmost node in a tree.
- K: A number specifying the maximum number of children a node can have (k-ary tree).
- Left: Reference to a child node on the left side (binary tree).
- Right: Reference to a child node on the right side (binary tree).
- Edge: A link between a parent and child node.
- Leaf: A node with no children.
- Height: The number of edges from the root to the furthest leaf.

**Sample Tree**
- A visual representation of a tree structure with nodes and edges.

**Traversals**
- Tree traversals involve visiting nodes in a specific order.
- Two categories: Depth First and Breadth First.

**Depth First Traversals**
- Priority is given to exploring the depth (height) of the tree.
- Three methods: Pre-order, In-order, Post-order.

**Pre-order Traversal**
- Visit root, left subtree, right subtree.

**In-order Traversal**
- Visit left subtree, root, right subtree.
- Typically used for binary search trees (BST) to retrieve elements in sorted order.

**Post-order Traversal**
- Visit left subtree, right subtree, root.

**Breadth First Traversal**
- Iterates through the tree level by level.
- Uses a queue to explore nodes.

**Pseudocode for Pre-order Traversal**
```
ALGORITHM preOrder(root)
  OUTPUT <-- root.value
  if root.left is not NULL
      preOrder(root.left)
  if root.right is not NULL
      preOrder(root.right)
```

**Binary Tree Vs K-ary Trees**
- Binary Tree: Each node has at most two children (left and right).
- K-ary Tree: Each node can have up to K children.

**Breadth First Traversal in K-ary Trees**
- Uses a queue to traverse nodes at each level.
- Enqueue children for processing.

**Pseudocode for Breadth First Traversal**
```
ALGORITHM breadthFirst(root)
  Queue breadth <-- new Queue()
  breadth.enqueue(root)
  while !breadth.is_empty()
    node front = breadth.dequeue()
    OUTPUT <-- front.value
    for child in front.children
        breadth.enqueue(child)
```

**Adding a Node**
- Nodes can be added anywhere in a tree.
- Use breadth-first traversal to insert nodes level by level.

**Big O**
- Insertion and search in binary trees: O(height).
- In a balanced tree, height is log(n); in an unbalanced tree, it can be n.
- Space complexity for search: O(1).

**Binary Search Trees (BST)**
- A type of binary tree with a specific structure.
- Nodes are organized such that left child < parent < right child.

**Searching a BST**
- Efficient search by comparing values with the root node.
- Traverse left for smaller values and right for larger values.

**Big O for BST**
- Insertion and search: O(height).
- In a balanced BST, height is log(n).

Feel free to use this cheat sheet as a reference for understanding and working with tree data structures.