# node . js http 2 server response . connection 方法

> 原文:[https://www . geesforgeks . org/node-js-http2 server response-connection-method/](https://www.geeksforgeeks.org/node-js-http2serverresponse-connection-method/)

**http2 server response . connection**是 http2 模块内一个内置的类 Http2ServerRequest 的应用编程接口，用于获取网络的引用。套接字对象。

**语法:**

```js
const response.connection

```

**参数**:该方法不接受任何参数作为参数。

**返回值**:这个方法返回网的引用。套接字对象。

**如何生成私钥和公钥证书？**

**1。文件名:私钥**

打开记事本，复制粘贴以下密钥，将文件保存为 ***私钥. PEM***T0】

**2。文件名:公共证书**

打开记事本，复制粘贴以下密钥，将文件保存为 ***公共证书***T0】

**示例 1:Filename:index . js**

## Javascript

```js
// Node.js program to demonstrate the
// Http2ServerResponse.connection method

const http2 = require('http2');
const fs = require('fs');

// Private key and public certificate for access
const options = {
  key: fs.readFileSync('private-key.pem'),
  cert: fs.readFileSync('public-cert.pem'),
};

// Request and response handler
const http2Handlers = (request, response) => {

  // Getting reference of tls socket
  // by using response.connection method
  const value = response.connection;

  // Display the result
  console.log("local port of the tls socket :- " + 
  value.localPort)  
};

// Creating and initializing server
// by using http2.createServer() method
const server = http2.createServer(options,http2Handlers);

server.on('stream', (stream, requestheader) => {
  stream.respond({ 
    ':status': 200, 
    'content-type': 'text/plain' 
  });
  stream.write('hello ');

  // Getting all information of this http2stream
  // object by using state method
  const status = stream.state;

  stream.end("priority weight : " + status.weight);

  // Stopping the server
  // by using the close() method
  server.close(() => {
    console.log("server destroyed");
  })
});

server.listen(8000);

// Creating and initializing client
// by using tls.connect() method
const client = http2.connect(
    'http://localhost:8000');

const req = client.request({ 
  ':method': 'GET',
  ':path': '/name'
});

req.on('response', (responsesocket) => {
  console.log("status : " 
  + responsesocket[":status"]);
});

req.on('data', (data) => {
  console.log('Received: %s ',
  data.toString().replace(/(\n)/gm,""));
});

req.on('end', () => {
  client.close(() => {
    console.log("client destroyed");
  })
});
```

使用以下命令运行 **index.js** 文件:

```js
node index.js
```

**输出:**

```js
local port of the tls socket :- 8000
status : 200
Received: hello
Received: priority weight : 16
client destroyed
server destroyed

```

**示例 2:Filename:index . js**

## Javascript

```js
// Node.js program to demonstrate the
// Http2ServerResponse.connection method

const http2 = require('http2');
const fs = require('fs');

// Private key and public certificate for access
const options = {
  key: fs.readFileSync('private-key.pem'),
  cert: fs.readFileSync('public-cert.pem'),
};

// Request and response handler
const http2Handlers = (request, response) => {

  // Getting reference of tls socket
  // by using response.connection method
  const value = response.connection;

  // Display the result
  response.end("local port of the tls socket :- " +
  value.localAddress)
};

// Creating and initializing server
// by using http2.createServer() method
const server = http2.createServer(options,http2Handlers);

server.on('stream', (stream, requestHeaders) => {

  // Getting all information of this http2stream object
  // by using state method
  const status = stream.state;

  stream.end("The sum weight of all Http2Stream : " + 
  status.sumDependencyWeight);

  // Stopping the server
  // by using the close() method
  server.close(() => {
    console.log("server destroyed");
  })
});

server.listen(8000);

// Creating and initializing client
// by using tls.connect() method
const client = http2.connect('http://localhost:8000');

const req = client.request({ ':method': 'GET', 
':path': '/www.geeksforgeeks.org' });

req.on('data', (data) => {
  console.log('Received: %s ',
  data.toString().replace(/(\n)/gm,""));
});

req.on('end', () => {
  client.close(() => {
    console.log("client destroyed");
  })
});
```

使用以下命令运行 **index.js** 文件:

```js
node index.js
```

**输出:**

```js
Received: local port of the tls socket :- ::ffff:127.0.0.1
client destroyed
server destroyed

```

**参考**:[https://nodejs . org/dist/latest-v 12 . x/docs/API/https 2 . html # https 2 _ response _ connection](https://nodejs.org/dist/latest-v12.x/docs/api/http2.html#http2_response_connection)