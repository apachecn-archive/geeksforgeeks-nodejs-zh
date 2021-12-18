# node . js zlib . createpincheraw()方法

> 原文:[https://www . geesforgeks . org/node-js-zlib-createpinieraw-method/](https://www.geeksforgeeks.org/node-js-zlib-createdeflateraw-method/)

方法是 zlib 模块的内置应用编程接口，用于创建一个新的平减对象。

**语法:**

```
zlib.createDeflateRaw( options )
```

**参数:**该方法接受单参数**选项**，这是一个保存 zlib 选项的可选参数。

**返回值:**返回一个新的平减对象。

以下示例说明了在 Node.js 中使用**zlib . createpincheraw()方法**:

**例 1:**

```
// Node.js program to demonstrate the     
// createDeflateRaw() method

// Including zlib and fs module
const zlib = require("zlib");
const fs = require('fs');

// Creating readable Stream
const inp = fs.createReadStream('input.txt');

// Creating writable stream
const out = fs.createWriteStream('input.txt.gz');

// Calling createDeflateRaw method
const defR = zlib.createDeflateRaw();

// Piping
inp.pipe(defR).pipe(out);
console.log("Program Completed!");
```

**输出:**

```
Program Completed!

```

**例 2:**

```
// Node.js program to demonstrate the     
// createDeflateRaw() method

// Including zlib and fs module
const zlib = require("zlib");
const fs = require('fs');

// Creating readable Stream
const inp = fs.createReadStream('input.txt');

// Creating writable stream
const out = fs.createWriteStream('input.txt.gz');

// Calling createDeflateRaw method
const defR = zlib.createDeflateRaw();

// Piping
inp.pipe(out).pipe(defR);
console.log("Program Completed!");
```

**输出:**

```
Error [ERR_STREAM_CANNOT_PIPE]: Cannot pipe, not readable
    at WriteStream.Writable.pipe (_stream_writable.js:243:24)
    at /home/runner/SomberMonumentalCad/index.js:19:15
    at Script.runInContext (vm.js:133:20)
    at Object. (/run_dir/interp.js:156:20)
    at Module._compile (internal/modules/cjs/loader.js:778:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:789:10)
    at Module.load (internal/modules/cjs/loader.js:653:32)
    at tryModuleLoad (internal/modules/cjs/loader.js:593:12)
    at Function.Module._load (internal/modules/cjs/loader.js:585:3)

```

在这里，管道没有按照正确的顺序进行，因此会出现错误。

**参考资料:**[https://nodejs . org/API/zlib . html # zlib _ zlib _ create deflate _ options](https://nodejs.org/api/zlib.html#zlib_zlib_createdeflateraw_options)