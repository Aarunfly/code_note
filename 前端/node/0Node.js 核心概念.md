### 了解 Node.js 是什么，以及它的事件驱动和非阻塞 I/O 模型。

Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行时环境，主要用于构建高性能的服务器端应用程序。它将 JavaScript 从浏览器环境扩展到服务器端，允许开发者使用 JavaScript 编写全栈应用程序。

事件驱动和非阻塞 I/O 模型
Node.js 的核心特性之一是其事件驱动和非阻塞 I/O 模型。以下是详细解释：

# 1、事件驱动（Event-Driven）
1、事件循环（Event Loop）：

· Node.js 使用事件循环来处理事件。事件循环是一个无限循环，负责监听和处理事件。
· 当有事件发生时，Node.js 会触发相应的回调函数来处理这些事件。
2、事件发射器（EventEmitter）：

· Node.js 提供了一个内置的模块 events，用于创建和处理事件发射器。
· 事件发射器对象可以注册监听器（listener），当事件发生时，监听器会被触发。
`const EventEmitter = require('events');
const eventEmitter = new EventEmitter();

// 注册事件监听器
eventEmitter.on('greet', () => {
  console.log('Hello World!');
});

// 触发事件
eventEmitter.emit('greet');
`

非阻塞 I/O（Non-Blocking I/O）
1、异步操作：

· 在传统的阻塞 I/O 模型中，当执行 I/O 操作（如读取文件、网络请求）时，程序会等待操作完成后再继续执行后续代码。这会导致资源的浪费和性能的下降。
· Node.js 采用非阻塞 I/O 模型，通过异步操作来避免这种情况。在异步操作中，I/O 操作会在后台执行，程序可以继续执行其他代码。当操作完成时，会触发一个回调函数来处理结果。
2、回调函数：

· 在 Node.js 中，大多数 I/O 操作都是异步的，需要通过回调函数处理结果。
`const fs = require('fs');

// 异步读取文件
fs.readFile('example.txt', 'utf8', (err, data) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log(data);
});

console.log('This will run before reading the file.');
 `
3、Promise 和 async/await：

· 除了回调函数，Node.js 还支持 Promises 和 async/await 语法，使异步编程更加简洁和可读。
`
const fs = require('fs').promises;

async function readFile() {
  try {
    const data = await fs.readFile('example.txt', 'utf8');
    console.log(data);
  } catch (err) {
    console.error(err);
  }
}

readFile();

console.log('This will run before reading the file.');

`
Node.js 是一个基于事件驱动和非阻塞 I/O 模型的 JavaScript 运行时环境。事件驱动模型通过事件循环和事件发射器来处理事件，而非阻塞 I/O 模型通过异步操作来提高性能和资源利用率。这些特性使 Node.js 特别适合于构建高并发、低延迟的网络应用程序，如 Web 服务器、实时聊天应用等。

### 学习如何安装 Node.js 和使用 npm（Node Package Manager）。
看官网
