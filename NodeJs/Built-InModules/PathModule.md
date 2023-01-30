## Path Module

Path modules provides utilities for working with files and directory paths.

### \_\_filename

\_\_filename represents the full path of the current file

**index.js**

```javascript
const path = require("node:path");
console.log(__filename);
```

### \_\_dirname

\_\_dirname represents the full path of the current directory

**index.js**

```javascript
const path = require("node:path");
console.log(__dirname);
```

### basename

basename function returns the basename of a file or directory

**index.js**

```javascript
const path = require("node:path");
console.log(path.basename(__filename));
console.log(path.basename(__dirname));
```

### extname

extname function returns the extension of a file and empty string for directory

**index.js**

```javascript
const path = require("node:path");
console.log(path.extname(__filename));
console.log(path.extname(__dirname));
```

### parse

parses a path into a object with the following interface

```javascript
{
  root: root directory path
  dir: directory path from root
  base: base file or directory name
  ext: file extension
  name: current file or directory name without extension
}
```

**index.js**

```javascript
const path = require("node:path");
console.log(parse);
```

### isAbsolute

isAbsolute return true if the path is absolute

**index.js**

```javascript
const path = require("node:path");
console.log(path.isAbsolute(__dirname));
console.log(path.isAbsolute("./Images/javascript-runtime.png"));
```

### join

join function takes pieces of path and join them together into a normalized path.

**index.js**

```javascript
const path = require("node:path");

console.log(path.join("dir1", "//dir2", "file.txt"));
// output --> dir1/dir2/file.txt

console.log(path.join("dir1", "//dir2", "../file.txt"));
// output --> dir1/file.txt
```

### resolve

**index.js**

```javascript
const path = require("node:path");
console.log(resolve);
```
