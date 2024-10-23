### **1.** **Difference between var, let and const**

- `var` is function scoped, it is only available within the function it was declared in, or globally if declared outside of a function
    
    - It **ignores block scope**, meaning variables declared with `var` inside a block (e.g., `if`, `for`) are accessible outside that block.
    - Variables declared with `var` are **hoisted** to the top of their scope (function or global) but are initialized as `undefined`. This means you can reference a `var`-declared variable before its actual declaration, but its value will be `undefined`.
    - The value of a `var`-declared variable can be reassigned.
- `let` is block-scoped, which means it is confined to the block in which it was declared
    
    - Like `var`, the value of a `let`-declared variable can be reassigned.
- `const` is also block-scoped, but needs to be initialized at declaration  
    - Variables declared with `let` and `const` are also hoisted, but they are placed in a **"temporal dead zone"** until the code execution reaches their declaration. This means you cannot access them before they are declared.  
    - `const` creates **immutable references**. Once a value is assigned to a `const` variable, it cannot be reassigned.  
    - Although the reference is immutable, if the `const` holds an object or array, the contents of that object/array can still be mutated.  
    Summary:
    
- **`var`:**
    
    - Function-scoped, hoisted, can be redeclared or reassigned.
- **`let`:**
    
    - Block-scoped, hoisted but not accessible before declaration, can be reassigned but not redeclared in the same scope.
- **`const`:**
    
    - Block-scoped, hoisted but not accessible before declaration, cannot be reassigned or redeclared, but properties of objects or arrays can be mutated. 

### 2. **What is the difference between `==` and `===` in JavaScript?**
- **`==` (Loose Equality):** Compares two values after performing type coercion, meaning it converts one or both values to a common type before comparison.
- **`===` (Strict Equality):** Compares both the value and the type without performing type coercion.
### 3. **What is Closure?**
-  When a function is declared inside another function, the inner function forms a closure.
- The inner function has access to variables in three scopes:
    1. **Its own local scope** (variables declared within the inner function)
    2. **The outer function's scope** (variables declared within the outer function)
    3. **The global scope** (variables declared globally)
### 4. **Explain `this` in JavaScript.**
**Answer:** The value of `this` depends on the **execution context** and how a function is invoked:

- In **global context**, `this` refers to the global object (`window` in browsers, `global` in Node.js).
- In a **method** (object function), `this` refers to the object that owns the method.
- In an **event handler**, `this` refers to the element that triggered the event.
- In an **arrow function**, `this` is lexically bound, meaning it inherits `this` from the surrounding code, instead of having its own context. 
### 5. **What is event delegation?**
**Answer:** **Event delegation** is a technique where you attach a single event listener to a parent element instead of attaching multiple listeners to individual child elements. The event listener uses the `event.target` property to detect which child element triggered the event. This is especially useful for dynamic content where child elements are added or removed after the event listeners have been attached.

### 6. **What is the difference between `call()`, `apply()`, and `bind()`?**

**Answer:** All three are used to explicitly set `this` in a function, but they differ in how they pass arguments:
- **`call()`**: Invokes the function immediately and allows passing arguments one by one.
- **`apply()`**: Invokes the function immediately but passes arguments as an array.
- **`bind()`**: Returns a new function with the specified `this` value but does not invoke the function immediately.
### 7. **What is hoisting in JavaScript?**

**Answer:** **Hoisting** is JavaScript's behavior of moving declarations (but not initializations) to the top of their scope before code execution. It applies to variables declared with `var` and to function declarations.

### 8. **What is the Event Loop in JavaScript?**

**Answer:** The **event loop** is responsible for managing the execution of asynchronous code in JavaScript. JavaScript has a single thread, but with asynchronous operations (like timers, I/O, promises), the event loop ensures non-blocking behavior by processing tasks from the **call stack** (for synchronous operations) and the **task queue** (for asynchronous operations).

```
console.log('Start');

setTimeout(() => {
  console.log('Timeout');
}, 0);

Promise.resolve().then(() => {
  console.log('Promise');
});

console.log('End');

```
1 - Start
2 - End
3 - Promise
4 - Timeout(since is async and waits to resolve)

### 9. **Explain the difference between synchronous and asynchronous JavaScript.**

**Answer:**

- **Synchronous code** is executed line by line, with each line blocking the execution of the next one until it finishes.
- **Asynchronous code** allows JavaScript to perform other tasks while waiting for operations like fetching data or waiting for a timer. Asynchronous functions (like `setTimeout`, Promises, and `async/await`) do not block the execution of other code.
### 10. **What are JavaScript Promises?**

**Answer:** A **Promise** is an object that represents the eventual completion (or failure) of an asynchronous operation. A promise can be in one of three states:

- **Pending**: The operation has not completed yet.
- **Fulfilled**: The operation has completed successfully, and a value is available.
- **Rejected**: The operation has failed, and a reason is available.
### 11. What are `null` and `undefined` in JavaScript?

- **`undefined`** means a variable has been declared but has **not been assigned a value** yet. It is the default value for variables that are declared but not initialized.
- **`null`** is an **intentional assignment** of a "nothing" or "empty" value. It is often used to explicitly indicate that a variable should be empty.

- `undefined` is of type `"undefined"`.
- `null` is of type `"object"` (this is a quirk in JavaScript's implementation, but conceptually, `null` represents the absence of an object or value).

- **Loose Equality (`==`)**: `null` and `undefined` are considered equal when using `==`, because both represent the absence of a value, but they are not strictly equal.
- **Strict Equality (`===`)**: When using strict equality, `null` and `undefined` are different because they are different types.