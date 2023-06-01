# How Javascript Code is executed? & Call Stack

- When a JS program is run, a global execution context is created.
- The execution context is created first when we run a JS program. In which it creates two phases.
  - Memory creation phase (Creation Phase)
  - Code execution phase
- For Ex-

```javascript
var n = 2;
function square(num) {
  var ans = num \* num;
  return ansi
}
var square2 = square(n);
var square4 = square (4);
```

- At first memory creation phase will work and allocates the memory to the variable and fuctions, for variable is stores undefined and for functions it stores the whole code of function.
- Undefined is like a placeholder in JS, a special keyword in JS.
- The output of first face looks like this:-

<table>
  <tr>
    <td> Memory creation </td>
    <td> Code Execution </td>
  </tr>
  <tr>
    <td> 
    ```javascript
      n: undefined
      square: {...}
      Square2: undefined
      Square 4: undefined
    ```
    </td>
    <td></td>
  </tr>
</table>
