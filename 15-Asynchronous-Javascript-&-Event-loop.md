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
