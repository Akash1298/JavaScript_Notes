# JS Engine & Google's V8 Architecture 🚀

- JS runs everywhere from smart watches to robots to browsers because of the JavaScript Runtime Environment (JRE).
- JRE is like a big container with everything required to run JavaScript code.
- JRE consists of a JS Engine (heart of JRE), a set of APIs to connect with the outside environment, an event loop, a Callback queue, a Microtask queue, etc.
- The browser can execute JavaScript code because it has the JavaScript Runtime Environment.
- ECMAScript is the governing body of JS. It has a set of rules which are followed by all JS engines like Chakra(Internet Explorer), V8 Engine (Edge), Spidermonkey(Firefox)(the first JavaScript engine created by the JS creator himself), V8 (Chrome)
- JavaScript engine is not a machine. It's software written in low-level languages (eg, C++) that takes in high-level code in JS and spits out low-level machine code.
- Code inside Javascript Engine passes through 3 steps : **Parsing**, **Compilation** and **Execution**

  1. **Parsing** - Code is broken down into tokens. In "let a = 7" -> let, a, =, 7 are all tokens. Also we have a syntax parser that takes code and converts it into an AST (Abstract Syntax Tree) which is a JSON with all key values like type, start, end, body etc (looks like package.json but for a line of code in JS. Kinda unimportant)(Check out astexplorer.net -> converts line of code into AST).
  2. **Compilation** - JS has something called Just-in-time(JIT) Compilation - uses both interpreter & compiler. Compilation and execution go hand in hand. The AST(Abstract Syntax Tree) from the previous step goes to the interpreter, which converts high-level code to bytecode and moves to execution. While interpreting, the compiler also works hand in hand to compile and form optimized code during runtime. **Does JavaScript compile?** The answer is a loud **YES**. JS used to be only interpreter in old times, but now has both to compile and interpreter code and this make JS a JIT compiled language, its like best of both world.
  3. **Execution** - Needs 2 components ie. Memory heap(place where all memory is stored) and Call Stack(same call stack from previous episodes). There is also a garbage collector. It uses an algorithm called **Mark and Sweep**.
     ![JS Engine Demo](assets/JS_16-1.png)

- Companies use different JS engines and each tries to make theirs the best.
  - V8 of Google has an Interpreter called Ignition, a compiler called Turbo Fan, and a garbage collector called Orinoco
  - V8 architecture:
    ![JS Engine Demo](assets/JS_16-2.png)


