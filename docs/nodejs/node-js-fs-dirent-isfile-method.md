# Node.js fs。Dirent.isFile()方法

> 原文:[https://www . geesforgeks . org/node-js-fs-dirent-is file-method/](https://www.geeksforgeeks.org/node-js-fs-dirent-isfile-method/)

**fs。Dirent.isFile()** 方法是类 **fs 的内置应用编程接口。**文件系统**模块中的目录**，用于检查特定目录是否描述文件。

**语法:**

```js
const dirent.isFile()
```

**参数:**此方法不接受任何参数。
**返回值:**如果特定方向描述文件，则该方法返回真，否则返回假。
下面的程序说明了 **fs.dirent.isFile()** 方法在 node.js:
**中的使用示例 1:**
**文件名:index.js**

## java 描述语言

```js
// Node.js program to demonstrate the
// dirent.isFile() method
const fs = require('fs');

// Initiating asyn function
async function stop(path) {

  // Creating and initiating File's
  // underlying resource handle
  const dir = await fs.promises.opendir(path);

  // Synchronously reading the File's
  // underlying resource handle
  // using readSync() method
  for(var i = 0; i <= 3; i ++ ) {

    // Checking if the particular dirent is
    // File  or not by using isFile() method
    const value = (dir.readSync()).isFile();

    // Display the result
    console.log(dir.readSync());
    console.log(value);
  }
}

// Catching error
stop('./').catch(console.error);
```

使用以下命令运行 **index.js** 文件:

```js
node index.js
```

**输出:**

```js
Dirent { name: 'cert.cer', [Symbol(type)]: 1 }
true
Dirent { name: 'certificate1.cer', [Symbol(type)]: 1 }
true
Dirent { name: 'filename.txt', [Symbol(type)]: 1 }
false
Dirent { name: 'GFG.java', [Symbol(type)]: 1 }
true
```

**示例 2:**
**文件名:index.js**

## java 描述语言

```js
// Node.js program to demonstrate the
// dirent.isFile() method
const fs = require('fs');

// Initiating asyn function
async function stop(path) {

  let dir = null;

  try {

    // Creating and initiating directory's
    // underlying resource handle
    dir = await fs.promises.opendir(
        new URL('file:///F:/java/'));

    // Synchronously reading the File's
    // underlying resource handle
    // using readSync() method
    for(var i = 0; i <= 3; i ++ ) {

      // Checking if the particular dirent
      // is File or not by using isFile() method
      const value = (dir.readSync()).isFile();

      // Display the result
     console.log(dir.readSync());
     console.log(value);
    }
  } finally {

    if (dir) {

      // Display the result
      console.log("dir is closed successfully");

      // Synchronously closeSyncing the
      // directory's underlying resource
      // handle
      const promise = dir.closeSync();
    }
  }
}

// catching error
stop('./').catch(console.error);
```

使用以下命令运行 **index.js** 文件:

```js
node index.js
```

**输出:**

```js
Dirent { name: 'cert.cer', [Symbol(type)]: 1 }
true
Dirent { name: 'certificate1.cer', [Symbol(type)]: 1 }
true
Dirent { name: 'features', [Symbol(type)]: 2 }
true
Dirent { name: 'GFG.class', [Symbol(type)]: 1 }
true
dir is closed successfully
```

**参考:**[https://nodejs . org/dist/latest-v1 . x/docs/API/fs . html # fs _ dirent _ isfile](https://nodejs.org/dist/latest-v12.x/docs/api/fs.html#fs_dirent_isfile)