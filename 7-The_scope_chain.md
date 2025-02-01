# The Scope Chain, Scope & Lexical Environment

Scope in JavaScript is directly related to lexical environment.

## Basic Example of Scope Access

```javascript
function a() {
    console.log(b);
    //Somehow inside in function this b can access, the b which was outside this function
}
let b = 10;
a();
```

In the above example, function `a` can access `b` from global scope.

## Nested Function Scope Example

```javascript
function a() {
    c();
    function c() {
        console.log(b); //Output: 10
    }
}
let b = 10;
a();
```

In the above example, function `c` can also access `b` from global scope i.e. a nested function can also access a global scope.

## Execution Context and Call Stack

### Call Stack Structure:
- [ GEC, a(), b() ]

### Memory Storage in Execution Context:
- c() → [[lexical environment points to a()]]
- a() → [b:10, c: ƒ, [lexical environment points to GEC]]
- GEC → [a: ƒ, [lexical environment points to null]]

## Key Concepts

### Scope
- Defines where you can access a specific variable or function in our code.
- Determines the accessibility of variables and functions at different parts of code.

### Lexical Environment
- Created whenever an execution context is created
- Consists of the local memory along with the lexical environment of its parent
- Follows a hierarchical order

### Scope Chain
- Chain of all lexical environments and their parent references
- Known as Scope chain or Lexical environment chain
- Process involves going one by one to parent and checking for values
- The process of traversing through this chain is called scope chain lookup

## Important Note on Inner Functions

An inner function can access variables which are in outer functions even if the inner function is nested deep. In any other case, a function can't access variables not in its scope. This is a fundamental principle of JavaScript's lexical scoping.

```javascript
function a() {
    function c() {
        // code here
    }
    c(); // c is lexically inside a
} // a is lexically inside global execution
```

This concept demonstrates the power of closures and lexical scoping in JavaScript.
