# Node.js dns.resolveNs()方法

> 原文:[https://www.geeksforgeeks.org/node-js-dns-resolvens-method/](https://www.geeksforgeeks.org/node-js-dns-resolvens-method/)

**dns.resolveNs()方法**是 dns 模块的内置应用编程接口，用于使用 dns 协议解析指定主机名的 ns 或名称服务器记录。

**语法:**

```js
dns.resolveNs( hostname, callback )
```

**参数:**该方法有两个参数，如上所述，如下所述:

*   **Hostname:** This parameter specifies a string that represents the hostname to be resolved.
*   **Callback:** Specifies the function to be called after DNS resolution of the host name.
    *   **Error:** The specified generation error.
    *   **Address:** It is a string array representing the name server record of the returned host name.

**返回值:**此方法返回错误，通过回调函数寻址。这些数据作为参数传递给回调函数。

下面的例子说明了在 Node.js 中使用 dns.resolveNs()方法:

**例 1:**

```js
// Node.js program to demonstrate the   
// dns.resolveNs() method

// Accessing dns module
const dns = require('dns');

// Calling dns.resolveNs() method for hostname
// geeksforgeeks.org and displaying them in
// console as a callback
dns.resolveNs('geeksforgeeks.org', (err, 
    addresses) => console.log('NS records: %j', addresses));
```

**输出:**

```js
NS records: [
    "ns-1520.awsdns-62.org",
    "ns-1569.awsdns-04.co.uk",
    "ns-245.awsdns-30.com",
    "ns-869.awsdns-44.net"
]

```

**例 2:**

```js
// Node.js program to demonstrate the   
// dns.resolveNs() method

// Accessing dns module
const dns = require('dns');

// Calling dns.resolveNs() method for
// hostname google.com and displaying
// them in console as a callback
dns.resolveNs('google.com', (err, 
    addresses) => console.log('NS records: %j', addresses));
```

**输出:**

```js
NS records: [
    "ns3.google.com",
    "ns2.google.com",
    "ns4.google.com",
    "ns1.google.com"
]

```

**注意:**以上程序使用`node index.js`命令编译运行。

**参考:**[https://nodejs . org/API/DNS . html # DNS _ DNS _ resolvens _ hostname _ callback](https://nodejs.org/api/dns.html#dns_dns_resolvens_hostname_callback)