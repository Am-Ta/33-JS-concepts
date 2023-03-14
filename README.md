# Call Stack

- [MDN Web Docs](https://developer.mozilla.org/en-aUS/docs/Glossary/Call_stack)

A **call stack** is a mechanism for an interpreter (like the JavaScript interpreter in a web browser) to keep track of its place in a script that calls multiple functions — what function is currently being run and what functions are called from within that function, etc.

```javascript
function greeting() {
  // [1] Some code here
  sayHi();
  // [2] Some code here
}
function sayHi() {
  return "Hi!";
}

// Invoke the `greeting` function
greeting();

// [3] Some code here
```

1. Ignore all functions, until it reaches the `greeting()` function invocation.
2. Add the `greeting()` function to the call stack list.

> Call stack list: - **greeting**

3. Execute all lines of code inside the `greeting()` function.
4. Get to the `sayHi()` function invocation.
5. Add the `sayHi()` function to the call stack list.

> Call stack list: - **sayHi** - **greeting**

6. Execute all lines of code inside the `sayHi()` function, until reaches its end.
7. Return execution to the line that invoked `sayHi()` and continue executing the rest of the `greeting()` function.
8. Delete the `sayHi()` function from our call stack list.

> Call stack list: - **greeting**

9. When everything inside the `greeting()` function has been executed, return to its invoking line to continue executing the rest of the JS code.
10. Delete the `greeting()` function from the call stack list.

> Call stack list: EMPTY

> In summary, then, we start with an empty Call Stack. Whenever we invoke a function, it is automatically added to the Call Stack. Once the function has executed all of its code, it is automatically removed from the Call Stack. Ultimately, the Stack is empty again.
- - -

- [Understanding Javascript Function Executions — Call Stack, Event Loop , Tasks & more](https://medium.com/@gaurav.pandvia/understanding-javascript-function-executions-tasks-event-loop-call-stack-more-part-1-5683dea1f5ec)

![call stack](https://miro.medium.com/v2/resize:fit:640/1*E3zTWtEOiDWw7d0n7Vp-mA.gif "call stack")

There is a limit on the size of the stack which is 16,000 frames , more than that it will just kill things for you and throw *Max Stack Error* Reached.

![Max Stack Error](https://miro.medium.com/v2/resize:fit:720/format:webp/1*tqkykdU69DFrxi82JOWLbQ.png "Max Stack Error")
- - -

- [The JavaScript Call Stack - What It Is and Why It's Necessary](https://www.freecodecamp.org/news/understanding-the-javascript-call-stack-861e41ae61d4)

The call stack is primarily used for function call. Since the call stack is single, function(s) execution, is done, one at a time, from top to bottom. *It means the call stack is synchronous*.

What is the call stack? 

At the most basic level, a call stack is a data structure that uses the **Last In, First Out (LIFO)** principle to **temporarily store** and manage function call.

> **LIFO**: it means that the last function that gets pushed into the stack is the first to be pop out, when the function returns.

> **temporarily store**: When a function is called, the function, its parameters, and variables are pushed into the call stack to form a stack frame. This stack frame is a memory location in the stack. The memory is cleared when the function returns as it is pop out of the stack.

> **Manage function call**: The call stack maintains a record of the position of each stack frame. It knows the next function to be executed (and will remove it after execution). This is what makes code execution in JavaScript synchronous.

> **stack overflow**: A stack overflow occurs when there is a recursive function (a function that calls itself) without an exit point. The browser (hosting environment) has a maximum stack call that it can accomodate before throwing a stack error.
```javascript
function callMyself(){
  callMyself();
}

callMyself();
```
- - -
- [What Is The Call Stack?](https://web.archive.org/web/20180701233338/https://www.valentinog.com/blog/js-execution-context-call-stack/#Javascript_What_Is_The_Execution_Context_What_Is_The_Call_Stack)

The first thing that gets pushed is *main()* (or global()), the main thread of execution of your Javascript program.