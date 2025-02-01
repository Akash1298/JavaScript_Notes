# Hoisting in JavaScript

- Let's see the magic of JavaScript, observe the below code :-

```javascript
getName(); // Namaste JavaScript
console.log(x); // undefined
var x = 7;
function getName() {
  console.log("Namaste JavaScript");
}
```

- In most of the programming languages this would be a complete error, you can't access variable before you initialize it. But JavaScript is different in this scenario due to memory allocation phase.

- Hoisting is a phenomena in JavaScript, through which we can access the variables and the functions even before we initialize or assigns value to them without getting any error and this is due to the memory creation phase.

- When we use arrow functions they behave like a variables and doesn't stores a complete code like functions.

- Observe below examples of How Hoisting works :-

```javascript
getName(); // Namaste JavaScript
console.log(x); // Uncaught Reference: x is not defined.
console.log(getName); // f getName(){ console.log("Namaste JavaScript); }
function getName() {
  console.log("Namaste JavaScript");
}
```

```javascript
getName(); // Uncaught TypeError: getName is not a function
console.log(getName);
var getName = function () {
  console.log("Namaste JavaScript");
};
// The code won't execute as the first line itself throws an TypeError.|
```

```
10   test.js:8:11
100  test.js:13:11
1    test.js:4:9
```

## Code Flow:

- A **Global Execution Context (GEC)** is created, and that GEC is pushed into the CallStack.  
  **CallStack:** `[ GEC ]`

- In the first phase, memory is allocated to `x: undefined`, and for `a` and `b` functions, their entire values are initialized.

- In the second phase, `x` is assigned the value `1`, then `a()` is invoked, and a local execution context is created inside `GEC`.  
  **CallStack:** `[ GEC, a() ]`

- Now, in **Local Execution Context (LEC)**, a totally different `x` variable is assigned `undefined` in memory allocation. Then, during execution, the value of `x` is assigned in LEC as `10`, and `console.log(x)` prints `10`. After this, LEC is closed and removed from CallStack.  
  **CallStack:** `[ GEC ]`

- When the cursor moves to the next line, the same steps will repeat for `b()`.  
  **CallStack:** `[ GEC, b() ]`

- After printing `100` at line `13`, the LEC of `b()` is removed from CallStack.  
  **CallStack:** `[ GEC ]`

- Finally, the last `console.log(x)` prints the value of `x` from **GEC**, which is `1`, and then **GEC** is deleted and removed from CallStack.

