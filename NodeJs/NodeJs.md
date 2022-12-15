# Node Js

Node Js is a Javascript Runtime Environment.

## ECMA Script

Ecma Script is a Standard specification for scripting language that runs in the browser.

## Javascript Engine

Javascript Engine that converts javascript code to machine code.

- V8 engine is Chrome browser's Javascript Engine.
- SpiderMonkey is Firefox's Javascript Engine.
- JavaScript Core is Safari's Javascript Engine.
- Chakra is Internet Explorer's Javascript Engine.

### V8

V8 is Google's open source Javascript Engine. V8 can run standalone or be embedded into any C++ application. This enables you to write a program that can run javascript and additional features that you choose to incorporate.

## Javascript Runtime

![Browser Javascript Runtime](Images/javascript-runtime.png)

Just a javascript engine is not enough; because Javascript as we know it is ECMA Script plus all the web Apis (DOM, LocalStorage, Timers, ...etc)

## Development Environment

Download Node Js from [Here](https://nodejs.org/en/download/). Install the LTS version.
Run the installation file and stick to defaults.

## Hello World

Command to check Node Version: `node -v`

Start interactive node REPL: `node`

> Note
>
> - **R**ead **E**valudate **P**rint **L**oop
> - To exit interactive REPL: `Ctrl + C`

Run a javascript file in node js: `node <file-path>`
![Run a Javascript file using Node](Images/node-helloword.png)

> **Javascript in Node vs Browser**
>
> In Node we control the environment. We have access to filesystem and other apis provided by node, but we don't have access to the DOM.
> In Browser we do not control the environment and we have access to the DOM but we don't have access to apis provided by node.

## Modules

Node has three types of modules:
- Local Modules
- Built-in Modules
- Third Party Modules

### Creating a Local Module

**CommonJs** is a standard that states how a module should by structured and shared.

In NodeJs, each file is a module that is isolated by default. We can use the require function which is available in plain Javascript to load code from module.

Use `reuqire()` to import js module.

**add.js**
```javascript
const add = (a, b) => {
  return a + b
}
let sum = add(2, 3)
console.log(sum)

console.log("Completed loading add.js")
```

**index.js**
```javascript
require("./add.js")

console.log("Hello from index.js")
```

### Module Exports
If we want to export particular parts of our code from a file to another, we can use `module.exports` property in NodeJs.

#### Exmaple #1 Exporting 1 Objects

**add.js**
```javascript
const add = (a, b) => {
  return a + b;
}

module.exports = add;
```

**index.js**
```javascript
var addFn = require("add.js");
let sum = addFn(3, 5)
console.log(sum);

console.log("Hello from index.js")
```

The `require()` returns the `module.exports` object. Here in this example module exports returns `add` function.

The imported name need not be same as in the file where it was defined in. This is known as the **default import** functionality in NodeJs.

#### Exmaple #2 Exporting multiple Objects

**calculator.js**
```javascript
const add = (a, b) => {
  return a + b;
}
const sub = (a, b) => {
  return a - b;
}
const mul = (a, b) => {
  return a *+* b;
}
const div = (a, b) => {
  return a / b;
}

module.exports = {
  add,
  sub,
  mul,
  div
};
```

**index.js**
```javascript
var calFuncs = require("calculator.js");
let sum = calFuncs.add(3, 5)
console.log(sum);

let dif = calFuncs.sub(35, 5)
console.log(dif);

let prod = calFuncs.mul(3, 5)
console.log(prod);

let quo = calFuncs.div(15, 5)
console.log(quo);

console.log("Hello from index.js")
```
When we want to export multiple objects from a module; We essentially export an object that comprises of other objects and functions.

In this scenario, we export an object containing `add`, `sub`, `mul` and `div`. We import this object in `index.js` and use its key-names to get its values.

> [Tip]
>
> We can also destructure the object to directly use the inside values.


### Module Scope

In NodeJs each module has its own scope.

**batman.js**

```javaScript
const superHero = "Batman";
console.log(superhero);
```

**superman.js**

```javaScript
const superHero = "Superman";
console.log(superhero);
```

**index.js**

```javaScript
require("batman.js")
require("superman.js")
```

#### iife

Iife also known as Self Invoking function.

Before module code is executed NodeJs wraps it in a iife. This provides each module with its own scope. This also saves us from having to worry about conflicting variables or functions.

**iffe.js**

```javascript
(function() {
const superHero = "Batman";
console.log(superhero);
})()

(function() {
const superHero = "Superman";
console.log(superhero);
})()
```

NodeJs wraps each module with a function with 5 parameters.

```javascript
(function (exports, require, module, __filename, __dirname){
  // module code here.
})
```
- `exports` :
- `require` : Import function to require other modules.
- `module` : Refers to module object of the current module.
- `__filename` : Contains string path of the current module file.
- `__dirname` : Contains string path of the current directory where the module file is located.

### Module Caching

NodeJs loads and then caches a module when we require it for subsequent loading.

#### Example #1 ❌ Module Caching

**superHero.js**

```javascript
class SuperHero {
  contructor() {
    this.name = "Batman";
  }

  getName() {
    return this.name;
  }

  setName(newName) {
    this.name = newName;
  }
}

module.exports = new SuperHero();
```
In Example #1, if we are using `superHero.js` module in two or more places, all the of them will be reffering to the same object of `SuperHero`.

#### Example #2 ✔ Module Caching

**superHero.js**

```javascript
class SuperHero {
  contructor() {
    this.name = "Batman";
  }

  getName() {
    return this.name;
  }

  setName(newName) {
    this.name = newName;
  }
}

module.exports = SuperHero;
```
