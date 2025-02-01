# Shortest JS Program🔥, `window` & `this`

- The shortest JS program is an empty file. Even though the file is empty and has nothing to do, it still creates a Global Execution Context.

- `window` is a global object that is created along with the JS execution Context.

- When GEC is created, the JS engine also creates `window`, which is created in global space. `window` is a big object with a lot of functions and methods. We can access all these functions and methods anywhere in our JavaScript program.

- The JS engine also creates the `this` keyword, at the global level, this keyword points to the `window` object.

- In different engines, the name of the global object changes. It is a `window` in browsers, but in Node.js, it is called something else. At the global level, `this === window`.

- Anything that is not inside a function is in the global space.

- If we create any variable in the global scope, the variables get attached to the global object. Example:

```js
var x = 10;
console.log(x); // 10
console.log(this.x); // 10
console.log(window.x); // 10
```
