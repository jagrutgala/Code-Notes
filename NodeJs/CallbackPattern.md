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
