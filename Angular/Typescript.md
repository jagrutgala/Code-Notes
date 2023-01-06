# Typescript

Typescript is a scripting language, that builds on top of javascript.
It is pre-processed/ compiled using the Typescript Compiler (tsc) into javascript.
Browsers cannot understand typescript so the need of typescript to be compiled.

Typescript added static type checking and annotations to javascript.

> Note
>
> Any Javascript code is valid Typescript, not the other way around.

## Getting started with Typescript

```
npm install typescript
```

**index.ts**

```typescript
const msg: string = "Hello World";
console.log(msg);
```

```
tsc index.ts
```

```
node index.js
```

## Typescript Annotations

In typescript you use color(`:`) as the annotation separator.

**variables**

You specify the variable type annotation after the variable name.

```typescript
let name: string = "Mario";
let age: number = "Name";
let isAlive: boolean = true;
```

**function arguments**

You specify argument type after the argument name.

```typescript
function printName(name: string) {
  console.log(name);
}
```

**function return type**

You can specify return type of the function after the end of argument list.

```typescript
function snakeString(msg: string): string {
  return msg.replace(" ", "_");
}
```

**object**

Object refers to any JavaScript value with properties. To define an object type, we simply list its properties and their types.

```typescript
function printCoord(pt: { x: number; y: number }) {
  console.log("The coordinate's x value is " + pt.x);
  console.log("The coordinate's y value is " + pt.y);
}
printCoord({ x: 3, y: 7 });
```

**optional properties**

In object type you can specify optional properties using a `?`. When you read from an optional property, you’ll have to check for undefined before using it.

```typescript
function printName(obj: { first: string; last?: string }) {
  // Error - might crash if 'obj.last' wasn't provided!
  console.log(obj.last.toUpperCase());

  if (obj.last !== undefined) {
    console.log(obj.last.toUpperCase()); // OK
  }

  // A safe alternative using modern JavaScript syntax:
  console.log(obj.last?.toUpperCase());
}
```

## Typescript Datatypes

- array -> to specify array you use syntax like `number[]`, `string[]`.

```typescript
let numArr: number[] = [31];
numArr.push(32);

numArr.push("Hallo");
// Not Allowed - string type is not assignable to number.
```

- tuple -> A tuple type is another sort of `Array` type that knows exactly how many elements it contains, and exactly which types it contains at specific positions.

```typescript
function doSomething(pair: [string, number]) {
  const a = pair[0];
  const b = pair[1];

  console.log(`string- ${a}, number- ${b}`);
}

doSomething(["hello", 42]);
```

- void
- any -> represents `any` type. Whenever used it disables type checking for that value.

```typescript
function print(msg: any) {
  console.log(msg);
}

print(42); // Ok
print("Meaning of life!"); // OK
```

- unknown

**Any vs Unknown**

<!-- Table Here -->

- union
- enum

## Interface & Alias

## Typescript Generics
