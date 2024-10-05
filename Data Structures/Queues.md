- lookup -> O(n)
- enqueue -> O(1)
- dequeue -> O(1)
- peek -> O(1)

**FIFO(First In First Out)**

- The first item inserted into a stack is the first one removed
- You can only access the first or last items of a stack

**Examples**

- Uber
- Restaurant apps
- Printer software

- DO NOT USE ARRAYS TO BUILD QUEUES, USE LINKED LISTS SINCE THE ENQUEUE/DEQUEUE OPERATION IS O(N) IN ARRAYS SINCE IT NEEDS TO REARRANGE THE INDEXES WHILE LINKED LISTS ARE O(1) SINCE YOU ONLY NEED TO CHANGE THE POINTER OF THE HEAD.