# How JavaScript works?

- Everything in javascript happens inside an `Execution Context`.
- Execution contexts consist of two components:-
  - Memory component.
  - Code component.

| Memory component                                                                       | Code component                                                    |
| -------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| This is a place where all the variables and functions are stored as a key-value pairs. | This is a place where whole js code is executed on line at a time |

| `key: value`
a: 10
function: {\***\*\_\_\*\***} | |
| This memory component also known as variable environment. | This code component also known as Thread of execution. |

- JavaScript is a `SYNCHRONOUS SINGLE THREADED LANGUAGE` i.e. JavaScript can only execute one command at a time, in a specific order. So, that means it can only go to the next line once the current line is executed.
