# JavaScript Block Scope & Shadowing

## What is a block in JS?
* A block is defined by curly braces
* Block also known as compound statement
* A block combines multiple statements so we can use where JS expects one statement

### Examples:
```javascript
// Single statement example
if (true) true;

// Multiple statement example
if (true) {
    var a = 10;
    console.log(a);
}
```

## Block Scope
* All variables we can access in a block is called block scope.
* When checking scope in this case:
- `var` declarations have global scope
- `let` and `const` declarations have block scope, meaning they are stored in a reserved memory space called block

## Example : 
```javascript
{
  var a = 10;    // you can access it outside
  let b = 20;    // you can't access this
  const c = 30;  // you can't access this
  
  console.log(a);  // 10
  console.log(b);  // 20
  console.log(c);  // 30
}
console.log(a);  // 10
console.log(b);  // Uncaught Reference Error: b is not defined
console.log(c);  // Uncaught Reference Error: c is not defined
```


## Shadowing
In `var`, if we update variable inside block, it shadows var value outside function also.

### Behavior with let
In case of `let`, the value which is in block is used & then outside block the value of let will be same initialized above block. As let is block scope.
Same case will be with `const`.

### Important Note
* You can shadow `let` with `var` but `var` cannot be shadowed by `let`
