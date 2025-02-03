# setTimeout + Closures 

> **Time, tide and Javascript wait for none.**

### Example 1
```js
  function x() {
    var i = 1;
    setTimeout(function () {
      console.log(i);
    }, 3000);
    console.log("Namaste Javascript");
  }
  x();
  // Output:
  // Namaste Javascript
  // 1 // after waiting 3 seconds
  ```

- We expect JS to wait 3 sec, print 1, and then print the string. But instead:
- JS sees setTimeout, creates closure (remembers i), starts 3s timer, and moves ahead without waiting
- Prints "Namaste JavaScript" immediately
- After the 3s timer expires, JS takes the callback function, puts it in the call stack, and runs it, printing 1

That's why the output is:
"Namaste JavaScript" → (3s wait) → 1
The closure ensures that the callback remembers i=1 even after waiting for 3s.

### Example 2

  ```js
  function x() {
    for (var i = 1; i <= 5; i++) {
      setTimeout(function () {
        console.log(i);
      }, i * 1000);
    }
    console.log("Namaste Javascript");
  }
  x();
  // Output:
  // Namaste Javascript
  // 6
  // 6
  // 6
  // 6
  // 6
  ```
   - Because of closures. When setTimeout stores the function somewhere and attaches the timer to it, the function remembers its reference to i, `not value of i`. All 5 copies of the function point to the same reference of i. JS stores these 5 functions, prints string, and then comes back to the functions. By then the timer has run fully. And due to looping, the i value became 6. And when the callback fun runs the variable `i = 6`. So the same 6 is printed in each log

   - To avoid this, we can use `let` instead of `var` as let has Block scope. For each iteration, the `i` is a new variable altogether(new copy of i). Every time setTimeout is run, the inside function forms a closure with new variable i.
   - If the interviewer asks us a solution for using `var`?

```js
    function x() {
      for (var i = 1; i <= 5; i++) {
        function close(i) {
          setTimeout(function () {
            console.log(i);
          }, i * 1000);
          // put the setT function inside new function close()
        }
        close(i); // everytime you call close(i) it creates new copy of i. Only this time, it is with var itself!
      }
      console.log("Namaste Javascript");
    }
    x();
```
