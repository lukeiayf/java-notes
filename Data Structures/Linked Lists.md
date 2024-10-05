- Composed of nodes, which have a value and a pointer, that points to other nodes
- The first node is called HEAD, and the last on is TAIL
- Fast insertions, you do  need to shift any items, just point to the next item

- prepend(add to the beginning) -> O(1)
- append(add to the end ) -> O(1)
- lookup -> O(n)
- insert -> O(n)
- delete -> O(n)

**Pointer**

- A reference to an object, a node, etc
- A pointer to the location in memory

**Doubly Linked List**

- Contains an additional pointer to the previous node;
- Allows to iterate over the list backwards;
- In downside it uses more memory;

**What/When to use**

- Need fast insertion/deletion but not much searching -> single linked list
- When you need good operation for searching elements -> doubly linked list