- Not technically an algorithm, but a pattern
- Recursive function is a function that refers to itself
```
function recursion(){
	recursion()
}
```
- BE CAREFUL WITH STACK OVERFLOW WHEN USING RECURSION
- Every recursion needs to have a base case where it stops running and always make sure you return otherwise the return value will not bubble up
```
let counter = 0;
function recursion(){
	if(counter > 3){
		return 'done';
	}
	counter++
	return recursion()
}
```

- 1 -  identify the base case
- 2 - identify the recursive case
- 3 - return when needed

- Anything that can be implemented with a recursion can be implemented with a loop

**Recursion vs Loops**

- Recursion keeps DRY(don't repeat yourself) and is more readable
- But in downside it requires a large memory stack to operate

**When to use recursion**

- If using a tree or converting something into a tree, consider recursion
- Divide and Conquer(Like binary search) using recursion