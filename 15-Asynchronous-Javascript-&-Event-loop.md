# Asynchronous JavaScript & EVENT LOOP

- So, JS is a single synchronous single-threaded language.
- It has `Call Stack`, it can do one thing at a time.

- Browser has `JS engine` which has `Call Stack` which has `Global Execution Context` and other `local execution contexts`.
- Browser has other superpowers also like `local storage`, `Timer`, `Bluetooth access`, `location access `, and so on.
- To access those superpowers Js needs to connect the callstack with all these superpowers. This is done using Web APIs.

### WebAPIs
None of the below are part of Javascript! These are extra superpowers that browser has. Browser gives access to JS callstack to use these powers.
- setTimeout()
- DOM APIs
- fetch()
- localStorage()
- console
- location

- Browser gave access inside Callstack/JS engine to all these superpowers, because of the global object.
- This global object is `keyword: window`

- Let's understand the below code with example:
<img width="482" alt="{BF3D739E-00CD-4B0C-9FA3-8D01B4845258}" src="https://github.com/user-attachments/assets/056570eb-3364-438f-b21f-c31f3c679e38" />

  ```js
    console.log("start");
    setTimeout(function cb() {
      console.log("timer");
    }, 5000);
    console.log("end");
    // start end timer
  ```
  - First a GEC is created and put inside call stack.
  - console.log("Start"); // this calls the console web api (through window) which internally actually modifies values in console.
  - setTimeout(function cb() { //this calls the setTimeout web api which gives access to timer feature. It stores the callback cb() and starts timer. console.log("Callback");}, 5000);
  - console.log("End"); // calls console api and logs in console window. After this GEC pops from call stack.
  - While all this is happening, the timer is constantly ticking. After it becomes 0, the callback cb() has to run.
  - Now we need this cb to go into call stack. Only then will it be executed. For this we need **event loop** and **Callback queue**
