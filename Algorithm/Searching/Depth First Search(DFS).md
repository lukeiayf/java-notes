- O(n)
- If follows the children of the tree until it reaches the end, then it comes back to the ancestor and checks if there are any children left unchecked, it repeats this until it traverses the whole tree.
- Uses a lower memory requirement since its not necessary to keep a pointer for each children.
- Similar to walking through a maze, you keep going until you hit a wall and then you go back to the previous intersection and take another path until you traverse the entire maze

- You have three ways of displaying a DFS
```
//consider a tree
//      9  
//   4      20  
//1   6  15    170

//visits the node left->root->right
inOrder: 1,4,6,9,15,20,170

//visits the node root->left->right
preOrder: 9,4,1,6,20,15,170

//visits the node left->right->root
postOrder: 1,6,4,15,170,20,9
```
