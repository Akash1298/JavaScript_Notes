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

