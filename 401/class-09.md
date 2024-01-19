# Class 09 Reading Notes: Stacks and Queues Cheat Sheet

#### Stack Overview
- **Structure**: Collection of Nodes. Each node points to the next but not to the previous.
- **Key Operations**:
  - `Push`: Add a node to the top of the stack.
  - `Pop`: Remove a node from the top of the stack.
  - `Peek`: View the value of the top node.
  - `IsEmpty`: Check if the stack is empty.

#### Stack Concepts
- **FILO (First In Last Out)**: First item added is the last to be removed.
- **LIFO (Last In First Out)**: Last item added is the first to be removed.

#### Stack Operations
- **Push** (O(1)): 
  - Adds a node to the top.
  - Steps: Create node, set its next to current top, reassign top to new node.
- **Pop** (O(1)): 
  - Removes the top node.
  - Steps: Temporarily reference top, move top to next node, remove temp's next, return value.
- **Peek** (O(1)): 
  - Returns the value of the top node.
- **IsEmpty** (O(1)): 
  - Returns true if the stack is empty, otherwise false.

#### Queue Overview
- **Structure**: Ordered list of nodes with a front and rear.
- **Key Operations**:
  - `Enqueue`: Add a node to the rear of the queue.
  - `Dequeue`: Remove a node from the front of the queue.
  - `Peek`: View the value of the front node.
  - `IsEmpty`: Check if the queue is empty.

#### Queue Concepts
- **FIFO (First In First Out)**: First item added is the first to be removed.
- **LILO (Last In Last Out)**: Last item added is the last to be removed.

#### Queue Operations
- **Enqueue** (O(1)): 
  - Adds a node to the rear.
  - Steps: Assign next of current rear to new node, reassign rear to new node.
- **Dequeue** (O(1)): 
  - Removes the front node.
  - Steps: Temporarily reference front, move front to next node, remove temp's next, return value.
- **Peek** (O(1)): 
  - Returns the value of the front node.
- **IsEmpty** (O(1)): 
  - Returns true if the queue is empty, otherwise false.

#### Visualization
- **Stack**: Vertical structure. Top is always the last added node.
- **Queue**: Horizontal structure. Front and rear are the first and last nodes, respectively.

#### Practical Tips
- Always check if the stack or queue is empty (`IsEmpty`) before popping or dequeuing to avoid exceptions.
- In stacks, top changes with each push or pop. In queues, front changes with dequeue, rear changes with enqueue.