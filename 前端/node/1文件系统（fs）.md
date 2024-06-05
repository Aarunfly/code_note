# 了解如何读取、写入和操作文件。

在 Node.js 中，操作文件主要通过内置的 fs 模块（文件系统模块）来实现。fs 模块提供了许多方法来读取、写入和操作文件，支持同步和异步两种方式。下面是一些常用的文件操作方法及其示例。

## 引入 fs 模块
首先，需要引入 fs 模块：
`const fs = require('fs');
`
## 异步文件操作
异步文件操作不会阻塞主线程，非常适合处理高并发任务。

### 读取文件
` fs.readFile('example.txt', 'utf8', (err, data) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log(data);
});
`
### 写入文件
`fs.writeFile('example.txt', 'Hello, World!', 'utf8', (err) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log('File has been written.');
});
`
### 追加内容到文件
`fs.appendFile('example.txt', ' This is an appended text.', 'utf8', (err) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log('Content has been appended.');
});
`
### 删除文件
`fs.unlink('example.txt', (err) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log('File has been deleted.');
});
`
## 同步文件操作
同步文件操作会阻塞主线程，适合简单任务或脚本编写。

### 读取文件
`
try {
  const data = fs.readFileSync('example.txt', 'utf8');
  console.log(data);
} catch (err) {
  console.error(err);
}
`
### 写入文件
`
try {
  fs.writeFileSync('example.txt', 'Hello, World!', 'utf8');
  console.log('File has been written.');
} catch (err) {
  console.error(err);
}
`
### 追加内容到文件
`
try {
  fs.appendFileSync('example.txt', ' This is an appended text.', 'utf8');
  console.log('Content has been appended.');
} catch (err) {
  console.error(err);
}
`
### 删除文件
`
try {
  fs.unlinkSync('example.txt');
  console.log('File has been deleted.');
} catch (err) {
  console.error(err);
}
`
## 使用 Promises 和 async/await
为了使异步代码更加简洁和易读，可以使用 Promises 或 async/await。'fs' 模块的 promise 版本在 'fs/promises' 模块中。

`
const fs = require('fs').promises;

async function performFileOperations() {
  try {
    // 读取文件
    const data = await fs.readFile('example.txt', 'utf8');
    console.log(data);

    // 写入文件
    await fs.writeFile('example.txt', 'Hello, World!', 'utf8');
    console.log('File has been written.');

    // 追加内容到文件
    await fs.appendFile('example.txt', ' This is an appended text.', 'utf8');
    console.log('Content has been appended.');

    // 删除文件
    await fs.unlink('example.txt');
    console.log('File has been deleted.');
  } catch (err) {
    console.error(err);
  }
}

performFileOperations();
`
## 其他文件操作
### 重命名文件
`
fs.rename('oldName.txt', 'newName.txt', (err) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log('File has been renamed.');
});
`
### 检查文件是否存在
`
fs.access('example.txt', fs.constants.F_OK, (err) => {
  console.log(err ? 'File does not exist' : 'File exists');
});
`
### 创建目录
`
fs.mkdir('newDirectory', { recursive: true }, (err) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log('Directory has been created.');
});
`
### 读取目录
`fs.readdir('directoryPath', (err, files) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log('Directory contents:', files);
});
`
# 学习同步和异步文件操作的区别。
