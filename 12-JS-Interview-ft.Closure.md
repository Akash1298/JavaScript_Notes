# Closure in JS

Closure is combination of function with its lexical env.

## Example:

```javascript
function outer() {
    var a = 10;
    function inner() {
        console.log(a);
    }
    return inner; // inner forms closure with outer env
} 
outer()(); // 10  // outer here first '()' will return inner function & then using second '()' to call inner function
```

## Will below code form closure :-

```javascript
function outer() {
    function inner() {
        console.log(a);
    }
    var a = 10;
    return inner;
}
outer()(); // 10
```
Yes, inner function will form closure with outer env sequence doesn't matter.

## Changing var to let, will it make any difference
```javascript
function outer() {
  let a = 10;
  function inner() {
    console.log(a);
  }
  return inner;
}
outer()(); // 10
```
No, It will still behave the same way.

## Will inner function have the access to outer function argument
```javascript
function outer(str) {
  let a = 10;
  function inner() {
    console.log(a, str);
  }
  return inner;
}
outer("Hello There")(); // 10 "Hello There"
```
Yes, Inner function will form closure and have access of both a and str.

## In below code, will inner form closure with outest
```javascript
function outest() {
  var c = 20;
  function outer(str) {
    let a = 10;
    function inner() {
      console.log(a, c, str);
    }
    return inner;
  }
  return outer;
}
outest()("Hello There")(); // 10 20 "Hello There"
```
Yes, inner will have access to all its outer environment.

## Output of below code and explaination?
```javascript
function outest() {
  var c = 20;
  function outer(str) {
    let a = 10;
    function inner() {
      console.log(a, c, str);
    }
    return inner;
  }
  return outer;
}
let a = 100;
outest()("Hello There")(); // 10 20 "Hello There"
```
Still the same output, the inner function will have reference to inner a, so conflicting name won't matter here. If it wouldn't have find a inside outer function then it would have went more outer to find a and thus have printed 100. So, it try to resolve variable in scope chain and if a wouldn't have been found it would have given reference error.


## Advantages of Closures in JavaScript

* Module Design Pattern
* Currying 
* Memoize
* Data hiding and encapsulation
* setTimeouts etc.


## Data hiding and encapsulation

```js
// without closures
var count = 0;
function increment(){
  count++;
}
// in the above code, anyone can access count and change it.

------------------------------------------------------------------

// (with closures) -> put everything into a function
function counter() {
  var count = 0;
  function increment(){
    count++;
  }
}
console.log(count); // this will give referenceError as count can't be accessed. So now we are able to achieve hiding of data

------------------------------------------------------------------

//(increment with function using closure) true function
function counter() {
  var count = 0;
  return function increment(){
    count++;
    console.log(count);
  }
}
var counter1 = counter(); //counter function has closure with count var.
counter1(); // increments counter

var counter2 = counter();
counter2(); // here counter2 is whole new copy of counter function and it wont impack the output of counter1

*************************

// Above code is not good and scalable for say, when you plan to implement decrement counter at a later stage.
// To address this issue, we use *constructors*

// Adding decrement counter and refactoring code:
function Counter() {
//constructor function. Good coding would be to capitalize first letter of constructor function.
  var count = 0;
  this.incrementCounter = function() { //anonymous function
    count++;
    console.log(count);
  }
   this.decrementCounter = function() {
    count--;
    console.log(count);
  }
}

var counter1 = new Counter();  // new keyword for constructor fun
counter1.incrementCounter();
counter1.incrementCounter();
counter1.decrementCounter();
// returns 1 2 1
```

## Disadvantage of closure

Overconsumption of memory when using closure, as every time those closed-over variables are not garbage collected till the program expires.
So when creating many closures, more memory is accumulated, which can create memory leaks if not handled.

**Garbage collector** : Program in JS engine or browser that frees up unused memory. In high level languages like C++ or JAVA, garbage collection is left to the programmer, but in JS engine it's done implicitly.

```js
function a() {
  var x = 0;
  return function b() {
    console.log(x);
  };
}

var y = a(); // y is a copy of b()
y();

// Once a() is called, its element x should be garbage collected ideally. But Function has closure over var x. So mem of x cannot be freed. Like this if more closures formed, it becomes an issue. To tacke this, JS engines like v8 and Chrome have smart garbage collection mechanisms. Say we have var x = 0, z = 10 in above code. When console log happens, x is printed as 0 but z is removed automatically.
