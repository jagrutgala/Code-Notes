# Modules

Node has three types of modules:

- Local Modules: Modules that we make.
- Built-In Modules: Modules that NodeJs ships with
- Third Party Modules: Modules that we can install

## Creating a Local Module

**CommonJs** is a standard that states how a module should by structured and shared.

In NodeJs, each file is a module that is isolated by default. We can use the require function which is available in plain Javascript to load code from module.

Use `reuqire()` to import js module.

**add.js**

```javascript
const add = (a, b) => {
  return a + b;
};
let sum = add(2, 3);
console.log(sum);

console.log("Completed loading add.js");
```

**index.js**

```javascript
require("./add.js");

console.log("Hello from index.js");
```

**Output**
```
5
Completed loading add.js
Hello from index.js
```

## Module Exports

If we want to export particular parts of our code from a file to another, we can use `module.exports` property in NodeJs.

### Exmaple #1 Exporting 1 Objects

**add.js**

```javascript
const add = (a, b) => {
  return a + b;
};

module.exports = add;
```

**index.js**

```javascript
var addFn = require("add.js");
let sum = addFn(3, 5);
console.log(sum);

console.log("Hello from index.js");
```
**Output**
```
8
Hello from index.js
```

The `require()` returns the `module.exports` object. Here in this example module exports returns `add` function.

The imported name need not be same as in the file where it was defined in. This is known as the **default import** functionality in NodeJs.

### Exmaple #2 Exporting multiple Objects

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
let sum = calFuncs.add(3, 5);
console.log(sum);

let dif = calFuncs.sub(35, 5);
console.log(dif);

let prod = calFuncs.mul(3, 5);
console.log(prod);

let quo = calFuncs.div(15, 5);
console.log(quo);

console.log("Hello from index.js");
```
**Output**
```
8
30
15
3
Hello from index.js
```

When we want to export multiple objects from a module; We essentially export an object that comprises of other objects and functions.

In this scenario, we export an object containing `add`, `sub`, `mul` and `div`. We import this object in `index.js` and use its key-names to get its values.

> [Tip]
>
> We can also destructure the object to directly use the inside values.

## Module Scope

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
**Output**
```
Batman
Superman
```
### iife

Iife also known as Self Invoking function.

Before module code is executed NodeJs wraps it in a iife. This provides each module with its own scope. This also saves us from having to worry about conflicting variables or functions.

**iffe.js**

```javascript
(function () {
  const superHero = "Batman";
  console.log(superhero);
})()(function () {
  const superHero = "Superman";
  console.log(superhero);
})();
```

NodeJs wraps each module with a function with 5 parameters.

```javascript
(function (exports, require, module, __filename, __dirname) {
  // module code here.
});
```

- `exports` :
- `require` : Import function to require other modules.
- `module` : Refers to module object of the current module.
- `__filename` : Contains string path of the current module file.
- `__dirname` : Contains string path of the current directory where the module file is located.

## Module Caching

NodeJs loads and then caches a module when we require it for subsequent loading.

### Example #1 ❌ Module Caching

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

### Example #2 ✅ Module Caching

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

# ES Modules

_!Important_ : extension for es-module is `.mjs`

## ES Modules _Import Export Patterns_

Export Single object or function

**calculator.js**

```javascript
const add = (a, b) => {
  return a + b;
};

export default add;
```

Export Multiple object or function

**calculator.js**
```javascript
const add = (a, b) => {
  return a + b;
};
const sub = (a, b) => {
  return a - b;
};

export default { add, sub };
```

Inline Export

**calculator.js**
```javascript
export const add = (a, b) => {
  return a + b;
};
export const sub = (a, b) => {
  return a - b;
};
```

Importing default object
```javascript
import math from "./math.js";

console.log(math.add(2, 5));
```

Destructuring exported module object
```javascript
import { add, sub } from "./math.js";

console.log(add(2, 5));
```

## Import Json Objects

We can import json data as a javascript object directly using the require function.

**index.js**

```javascript
const data = require("./data.json");
```

> Note
>
> `.json` extension is not mandatory, but if not given Node will try to find `<filename>.js` file first and load that instead of `<filename.json` file.
> So it is a best practice to keep the `.json` extension.

# Built-In Modules

Built-In Modules: Modules that NodeJs ships with

## node Protocol

`node:` is called the node protocol. (It is a recently introduced feature in `V12`)
When importing a built-in module `node:` is optional.

Why to use node protocol?

- Makes it perfectly clear that it is a built-in module.
- It make import identifier a valid absolute url.


`node:` is called the node protocol. (It is a recently introduced feature)
When importing a built-in module `node:` is optional.

Why to use node protocol?
- Makes it perfectly clear that it is a built-in module.
- It make import identifier a valid absolute url.

# Next Steps
[<-- Node](NodeJs.md) | [Async Javascript -->](AsyncJavascript.md)

## Also see

Built-in modules
- [Events Module](Built-InModules/EventsModule.md)
- [File System Module (fs)](Built-InModules/FileSystemModule.md)
- [Path Module](Built-InModules/PathModule.md)
