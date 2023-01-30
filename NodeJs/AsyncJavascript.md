# Async Javascript

Javascript is a `synchronous` `blocking` `single threaded` language.

**Synchronous**
If we have two functions which log messages to the
console, code executes top down, with only one line
executing at any given time.

**Blocking**
No matter how long a previous process takes, the
subsequent processes won't kick off until the former
is completed.

This means if the previous code has execute a intensive part of the code javascript has to complete that before moving on to the next code.

**Single Threaded**

A thread is simply a process that your javascript
program can use to run a task.

Each thread can only do one task at a time.

JavaScript has just the one thread called the main
thread for executing any code.

### The problem

Task: Retrieve data from database and the display it.

```javascript
let response = fetchDataFromDB("endpoint");
displayDataFromDB(response);
```

`fetchDataFromDB('endpoint')` could take 1 second or even more. During that time, we can't run any further code.

JavaScript, if it simply proceeds to the next line without waiting, we have an error because data is not what we expect it to be.

### Solution

Just javascript is not enough.

In front-end Web Browsers come into play. In back-end Node Js comes into play.

Web browsers and Node define functions and APIs that we can use to register functions that should not be executed synchronously, instead should be executed asynchronously after some event occurs.


One way is using [callbacks](#callback-pattern).

# Callback Pattern

In Javascript functions are first-class objects. This means that functions can be passed around as arguments or returned from other functions.

```javascript
function greet(name) {
  console.log(`Hello ${name}`);
}

function greetNode(greetFn) {
  const name = "Node";
  greetFn(name);
}
```

Any function that is passed as argument to another function is called a Callback function.
And the other function that accepts a function as a argument is called a Higher order function.

## Types of callbacks

There are two types of callbacks:-
1. Synchronous
1. Asynchronous

### Synchronous Callbacks

A callback that is executed immediately is called a Synchronous Callback. A good example of this is the `map` and `filter ` functions in `ES6`. For map and filter the callback functions defines the logic the higher order functions needs to apply.

### Asynchronous Callbacks

A async callback is a callback that is used to resume code execution after an async operation has completed. A async callback is used to delay the execution of the code until a particular time or event has occurred. In Node Js most of the modules are async in nature to prevent blocking of execution.

For example reading data from file or handling a network request.


```javascript
const button = document.getElementById("mybtn");
button.addEventListener("click", function () {
  console.log("button was clicked");
})
```
