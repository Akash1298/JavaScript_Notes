# Callback Functions in Javascript ft. Event Listeners

### Callback Functions

- Functions are first-class citizens.
- When we take a function Y and pass it to another function X. Here, Y is a callback function.
- This callback function gives us the access to whole `Asynchronous` world in the `Synchronous` world.

```js
  function x(y) {
    console.log("x");
    y();
  }
  x(function y() {
    console.log("y");
  });
```

- JS is a synchronous and single threaded language. But due to callbacks, we can do async things in JS.

- ```js
  setTimeout(function () {
    console.log("timer");
  }, 5000);
  function x(y) {
    console.log("x");
    y();
  }
  x(function y() {
    console.log("y");
  });
  // x y timer
  ```
  - The first function x & y is executed in the call stack then after 5 seconds we can see the setTimeout function shows anonymous in the call stack.
  - If an operation blocks the call stack it is called blocking the main thread.

### Event Listener

- We will create a button in HTML and attach an event to it.

  ```js
  // index.html
  <button id="clickMe">Click Me!</button>;

  // in index.js
  document.getElementById("clickMe").addEventListener("click", function xyz() {
    //when event click occurs, this callback function (xyz) is called into callstack
    console.log("Button clicked");
  });
  ```

- Implement a increment counter button.
  - Using global variable (not good as anyone can change it)
    ```js
    let count = 0;
    document
      .getElementById("clickMe")
      .addEventListener("click", function xyz() {
        console.log("Button clicked", ++count);
      });
    ```
  - Use closures for data abstraction
    ```js
    function attachEventList() {
      //creating new function for closure
      let count = 0;
      document
        .getElementById("clickMe")
        .addEventListener("click", function xyz() {
          console.log("Button clicked", ++count); //now callback function forms closure with outer scope(count)
        });
    }
    attachEventList();
    ```

### Garbage Collection and remove eventlisteners

- Event listeners are heavy as they form closures.
- So even when the call stack is empty, EventListener won't free up memory allocated to count as it doesn't know when it may need to count again.
- So we remove event listeners when we don't need them (garbage collected) onClick, onHover, and onScroll all in a page can slow it down heavily.
