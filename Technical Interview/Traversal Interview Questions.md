#### Which kind of traversal(BFS and DFS) should you use in these situations?

- If you know a solution is not far from the root of the tree:
-> BFS
- If the tree is very deep and solutions are rare:
-> BFS since DFS will take a really long time in this type of tree
- If the tree is very wide:
-> DFS, since BFS is gonna take too much time and memory since it needs to keep track of the nodes in the current level
- If solutions are frequent but located deep in the tree:
-> DFS
- Determining wheter a path exists between two nodes:
-> DFS, it is what its built for
- Finding the shortest path:
-> BFS