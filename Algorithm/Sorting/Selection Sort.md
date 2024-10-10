- O(n²) on time
- O(1) on space
- Works by selecting the smallest number while iterating through the list and at the end it puts it on the beginning of the list
```
[3,8,2,9]

it checks 3 as the smallest one and it has a pointer keeping track of the next item

3 < 8 so it keeps it in place

3 > 2 so now 2 is the smallest item

2 < 9 and the iteration is over so it puts 2 at the beginning of the array

[2,3,8,9]

now the array is sorted, but if it wasn't it would keep checking the smallest item from 2 and setting them in the next position

```