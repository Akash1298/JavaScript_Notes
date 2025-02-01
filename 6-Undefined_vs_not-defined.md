# `undefined` vs `not defined`

- `undefined` is allocated to the variable in the memory allocation phase. `undefined` is like a placeholder for a variable when it is declared but not assigned any value.

- `not defined` occurs when we use some object/variable, and it is not declared/found in the memory allocation phase.

- `undefined` and `not defined` are totally different cases.

```js
console.log(x); // undefined
var x = 25;
console.log(x); // 25
console.log(a); // Uncaught ReferenceError: a is not defined
```

- JavaScript is a Loosely typed / Weakly typed language. It doesn't attach any data type to the variable. In the example below, we can see a can be assigned any data type value.

```js
var a;
console.log(a);
a = 10;
console.log(a);
a = "hello world!";
console.log(a);
```

- Never assign undefined to a variable manually; let it happen on its own.
