# File System Module

File system module in Node Js allows us to asynchronously access and manipulate the local file system.

But to understand the working of the fs module we need to understand. If you know these concepts or want to jump into working with fs module you can skip it.

1. [Character Set](#character-set)
1. [Encoding](#encoding)
1. [Buffer](#buffers)
1. [Streams](#streams)
1. [Async Javascript](#async-javascript)

## Reading data from file

`readFileSync()` reads a file of the given path and returns a buffer containing data from the file in a synchronous way. it takes 2 argument file-path and encoding.

"Sync" keyword here in the function name signifies that this function will block the code execution in javascript till the file contents are read.

**file.txt**

```
Hello Node Js
```

**index.js**

```javascript
const fs = require("node:fs");

const fileContent = fs.readFileSync("./file.txt", "utf-8");
console.log(fileContent);

fs.readFile("./file.txt", "utf-8", (error, data) => {
  if (error === null) {
    console.log("Error");
  } else {
    console.log(data);
  }
});
```

`readFile()` reads a file of the given path and returns a buffer containing data from the file in a asynchronous way. it takes 3 argument file-path, encoding [optional] and a callback function with arguments (error, data) respectively.

## Writing data to file

`writeFileSync()` writes a file of the given path and returns a buffer containing data from the file in a synchronous way. it takes 2 argument file-path and data to write.

"Sync" keyword here in the function name signifies that this function will block the code execution in javascript till the file contents are written.

**index.js**

```javascript
const fs = require("node:fs");

fs.writeFileSync("./file.txt", "Written using writeFileSync");

fs.writeFile("./file.txt", "Written using writeFile", (error, data) => {
  if (error === null) {
    console.log("Error");
  } else {
    console.log(data);
  }
});
```

`writeFile()` writes a file of the given path and returns a buffer containing data from the file in a asynchronous way. it takes 3 argument file-path, data to write and a callback function with arguments (error) respectively.

**file.txt**

```
Written using writeFile
```

### Appending data to file

We can use the writeFile method here as well but this time with a optional configuration argument with the `flag` set to `a`

**index.js**

```javascript
const fs = require("node:fs");

fs.writeFileSync("./file.txt", "\nAppending using FS Module");

fs.writeFile(
  "./file.txt", // file path
  "\nAppending using writeFile", // data to append
  { flag: "a" }, // configuration object [optional]
  (error, data) => {
    // callback
    if (error === null) {
      console.log("Error");
    } else {
      console.log(data);
    }
  }
);
```

**file.txt**

```
Hello Node Js
Appending using FS Module
Appending using writeFile
```

## Reading data from file (Promise Version)

Using `promises` we can now attach `then` and `catch` methods to the output of async operations.
OR
Using `promises` we can now attach `async` and `await` syntax to manage async operations.

**file.txt**

```
Hello Node Js
```

**index.js**

```javascript
const fs = require("node:fs/promises");

fs.readFile("./file.txt", "utf-8")
  .then((data) => {
    console.log(data);
  })
  .catch((err) => {
    console.log(err);
  });
```

## Writing data to file (Promise Version)

**index.js**

```javascript
const fs = require("node:fs");

fs.writeFile("./file.txt", "Writing using writeFile").catch((err) => {
  console.log(error);
});
```

## Appending data to file (Promise Version)

**index.js**

```javascript
const fs = require("node:fs");

fs.writeFile("./file.txt", "Appending using writeFile", {flag: "a"}).catch((err) => {
  console.log(error);
});
```

## Character Set

Computer stores and represents data in binary format which is `0s and 1s`. To work with a piece of data it needs to convert the data into its binary representation. With numbers it is simple math. For example:

```
4 = (2^2 * 1) + (2^1 * 0) + (2^0 * 0)
```

But how do you represent a character into binary? It ain't a number so you can apply math to it? The answer is that the computer first converts the character into a number first and then into binary. For example:

```
V = 86 = 1010110
```

The number representation of a character is called `character code`. But how do we know that V is 86. That is what a character set defines.

A Character set is a list of characters represented by numbers. Example of character sets is `Unicode` and `ASCII`.

**in browser console**

```
"V".charCodeAt()
```

## Encoding

Character Encoding dictates how to represent a number in a character set as binary before it can be stored in the computer. It dictates how may bits to use to represent the number.

Example: UTF-8 states that each character should be encoded in bytes (8 bits).

```
4 = 100 = 0000100
V = 1010110 = 01010110
```

> Note
>
> Similar guidelines also exist on how images, videos and audio should be encoded and stored in binary format.

## Streams

A stream is a sequence of data that is moved from one point to another point over a period of time.

Ex: a stream of data being transferred from one file to another.

The idea is that to process stream of data in chunks as they arrive instead of waiting for the entire data to be available before processing.

Ex: watching a video on YouTube. The data arrives in chunks and you watch the video in chunks while rest of the data arrives over time.

This prevents unnecessary data downloads and memory usage.

## Buffers

### Buffer Roller Coaster scenario

Roller Coaster capacity is 30 people.

**Scene 1**

100 people arrive -> 30 people ride + 70 people waiting in queue.

**Scene 2**

1 people arrive -> 1 person waiting in queue for more people to arrive.

> Bottom Line
>
> You cannot control the pace at which people arrive, but you can decide what is the best time to send people on the ride.

This area where people wait is known as the buffer.

**Buffer**: It is the waiting space allocated in memory.

Best example of buffer: streaming a video online.

If your internet connection is fast enough, the speed of the stream will be fast enough to
instantly fill up the buffer and send it out for processing. That will repeat till the stream is finished.

If your connection is slow, after processing the first chunk of data that arrived, the video
player will display a loading spinner which indicates it is waiting for more data to arrive.

Once the buffer is filled up and the data is processed, the video player shows the video.

While the video is playing, more data will continue to arrive and wait in the buffer.

### Working with buffers

Node Js provides the buffer feature globally without having to import it.

```javascript
const buffer = new Buffer.from("Hello Node Js");
console.log(buffer.toJSON());

// {
//  type: "Buffer",
//  data: [ character code list ]
// }

buffer.write("Code");
console.log(buffer.toString());

// "Codeo Node Js"
```

Overwriting of data happens because the buffer has limited memory.

## Async Javascript

> Note
>
> This section is covered in [Async Javascript](../AsyncJavascript.md#async-javascript)
