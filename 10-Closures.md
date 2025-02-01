# Closures

- A function binds together with its lexical env.
- function along with its lexical scope forms a closure.

Let me explain the two examples shown:

Example 1:
```javascript
function x() {
    var a = 7;
    function y() {
        console.log(a);
    }
    y();
}
x();
```

Example 2:
```javascript
function x() {
    var a = 7;
    function y() {
        console.log(a)
    }
  return y;
}
var z = x();
console.log(z);
z();
```
Let me explain what's happening:

- When x() is called and assigned to z, we get back function y.
- Even after x() has finished executing, when we call z() (which is actually function y), it still has access to variable a.
- This is because y forms a closure - it maintains access to its lexical scope (including variable a) even after the parent function x has finished executing.

"Still z have value 'a' because of closure"



## Uses of Closures in JavaScript

### 1. Module Design Pattern
Closures enable the module pattern, allowing for private variables and methods while exposing only the intended public interface.

```javascript
const bankAccount = (function() {
    let balance = 0;  // private variable
    
    return {
        deposit: function(amount) {
            balance += amount;
            return `Balance: ${balance}`;
        },
        getBalance: function() {
            return balance;
        }
    };
})();
```

### 2. Currying
Closures help in creating curried functions, which transform a function with multiple arguments into a sequence of functions.

```javascript
function multiply(a) {
    return function(b) {
        return a * b;
    }
}
const multiplyByTwo = multiply(2);
// multiplyByTwo(4) returns 8
```

### 3. Functions like Once
Ensures a function is called only once, storing the state in closure.

```javascript
function once(fn) {
    let called = false;
    return function(...args) {
        if (!called) {
            called = true;
            return fn(...args);
        }
    }
}
```

### 4. Memoize
Caches function results for improved performance.

```javascript
function memoize(fn) {
    const cache = {};
    return function(...args) {
        const key = JSON.stringify(args);
        if (key in cache) {
            return cache[key];
        }
        const result = fn.apply(this, args);
        cache[key] = result;
        return result;
    }
}
```

### 5. Maintaining State in Async World
Preserves state across asynchronous operations.

```javascript
function createCounter() {
    let count = 0;
    return {
        increment: function() {
            return ++count;
        },
        getCount: function() {
            return count;
        }
    }
}
```

### 6. SetTimeout
Captures variables from outer scope in timer callbacks.

```javascript
function delayedGreeting(name) {
    setTimeout(function() {
        console.log(`Hello, ${name}!`);
    }, 1000);
}
```

### 7. Iterators
Creates iterator functions that maintain their own state.

```javascript
function createIterator(array) {
    let index = 0;
    return {
        next: function() {
            return index < array.length ?
                {value: array[index++], done: false} :
                {done: true};
        }
    };
}
```

### 8. And Many More...
- Data privacy
- Partial application
- Event handlers
- Factory functions
- Dependency injection
- Function composition
