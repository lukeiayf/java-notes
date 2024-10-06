- Parent -> child relationship
- Unidirectional
- Parent can have more than one child
- The first node is also called "root"
- The children are also called "leafs"
- The connection between nodes are called "edges"

**Examples of trees:**

- DOM(from websites)
- Old school chess computers
- Facebook comments or any comment that allow comments on the comment
- Abstract syntax tree for computing

**Binary Trees**

- lookup -> O(log N)
- insert -> O(log N)
- delete -> O(log N)

- Each node can have either zero, one or nodes
- Each child can only have one parent
- "**Perfect Binary Trees**" have all their nodes with two children, very efficient and desirable
	- In this way the number of nodes double in each level of the tree
	- The number of nodes on the bottom is equal to the number of all previous nodes + 1
- "**Full Binary Trees**" have either zero or two children on their nodes 
- You can calculate the number of nodes of a binary tree by  doing:`(2 ^ L) - 1`  where L is the level of the binary tree 

**Binary Search Tree**

- lookup -> O(log N)
- insert -> O(log N)
- delete -> O(log N)

- All child nodes in the right are greater than the current node
- The opposite applies to the left, all nodes are lesser than the current node
- A node can ONLY have up to two children
- Optimized for searching

**Balanced and Unbalanced BST**

- An unbalanced BST starts to look like a Linked List instead and their Big O becomes:
	- lookup -> O(n)
	- insert -> O(n)
	- delete -> O(n)
- There are specific algorithms to keep a BST and most languages apply them automatically
- Balanced Trees:
	- AVL Tree
	- Red Black Tree

**Pros**
- Better than O(n)
- Ordered
- Flexible size
**Cons**
- No O(1) operations

**Binary Heap**

- Memory Heap != Heap Data Structure

- lookup -> O(n)
- insert -> O(log n)
- delete -> O(log n)

- Can only have to children from a node
- On a heap every node on the top level has a greater value than the nodes on the levels down
- Left and right can be any value as long as its less than the top value
- They are really good at doing comparing operations

**Priority Queue**

- In this case each "node" has a weight
- Cascading prioritizes the nodes with greater priority than the rest
- Insertion is done left to right in a tree
- Example: A queue for boarding an airplane
		Captain -> Steward -> Passengers
	The order of arrival doesnt matter in this case, since each have their own priority in the queue

**Trie**

- Tries allow to see if a word or part of a word is in a body of text
- Used for searching engines/ dictionaries
- Searching in a Trie is O(length of the word)