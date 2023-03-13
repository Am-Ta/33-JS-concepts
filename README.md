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

![call stack](https://miro.medium.com/v2/resize:fit:640/1*E3zTWtEOiDWw7d0n7Vp-mA.gif "call stack")