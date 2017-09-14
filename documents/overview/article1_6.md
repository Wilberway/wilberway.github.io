# 关于Nodejs你要知道的几件事

## 什么是错误优先的回调函数？

错误优先的回调函数用于传递错误和数据。第一个参数始终应该是一个错误对象， 用于检查程序是否发生了错误。其余的参数用于传递数据。例如：

```javascript
fs.readFile(filePath, function(err, data) {  
    if (err) {
        //handle the error
    }
    // use the data object
});
```

## 如何避免回调地狱

你可以有如下几个方法：

* 模块化：将回调函数分割为独立的函数

* 使用Promises

* 使用yield

* 来计算生成器或Promise

## 如何用Node监听80端口

在类Unix系统中你不应该尝试去监听80端口，因为这需要超级用户权限。 因此不推荐让你的应用直接监听这个端口。

目前，如果你一定要让你的应用监听80端口的话，你可以有通过在Node应用的前方再增加一层反向代理 （例如nginx）来实现，如下图所示。否则，建议你直接监听大于1024的端口。

> 反向代理指的是以代理服务器来接收Internet上的连接请求，然后将请求转发给内部网络上的服务器， 并且将服务器返回的结果发送给客户端。

## 什么是事件循环

Node采用的是单线程的处理机制（所有的I/O请求都采用非阻塞的工作方式），至少从Node.js开发者的角度是这样的。 而在底层，Node.js借助libuv来作为抽象封装层， 从而屏蔽不同操作系统的差异，Node可以借助livuv来来实现多线程。下图表示了Node和libuv的关系。

![pic1][1]

Libuv库负责Node API的执行。它将不同的任务分配给不同的线程，形成一个事件循环， 以异步的方式将任务的执行结果返回给V8引擎。可以简单用下面这张图来表示。

![pic2][2]

每一个I/O都需要一个回调函数——一旦执行完便推到事件循环上用于执行。

## 哪些工具可以用来保证一致性的代码风格

你可以选择如下的工具：

* JSLint

* JSHint

* ESLint

* JSCS - 推荐

在团队开发中，这些工具对于编写代码非常的有帮助，能够帮助团队开发者强制执行规定的风格指南， 还能够通过静态分析捕获常见的错误。

## 运算错误与程序错误的区别

运算错误并不是bug，这是和系统相关的问题，例如请求超时或者硬件故障。而程序员错误就是所谓的bug。

## 使用NPM有哪些好处？

通过NPM，你可以安装和管理项目的依赖，并且能够指明依赖项的具体版本号。 对于Node应用开发而言，你可以通过package.json文件来管理项目信息，配置脚本， 以及指明项目依赖的具体版本。

## 什么是Stub？举个使用场景

Stub是用于模拟一个组件或模块的函数或程序。在测试用例中， 简单的说，你可以用Stub去模拟一个方法，从而避免调用真实的方法， 使用Stub你还可以返回虚构的结果。你可以配合断言使用Stub。

举个例子，在一个读取文件的场景中，当你不想读取一个真正的文件时：

```javascript
var fs = require('fs');

var readFileStub = sinon.stub(fs, 'readFile', function (path, cb) {  
    return cb(null, 'filecontent');
});

expect(readFileStub).to.be.called;  
readFileStub.restore();
```
> 在单元测试中：Stub是完全模拟一个外部依赖，而Mock常用来判断测试通过还是失败。

## 什么是测试金字塔？

测试金字塔指的是： 当我们在编写测试用例时，底层的单元测试应该远比上层的端到端测试要多。

当我们谈到HTTP API时，我们可能会涉及到：

* 有很多针对模型的底层单元测试

* 但你需要测试模型间如何交互时，需要减少集成测试

[1]: http://upload-images.jianshu.io/upload_images/675733-c76f15bc26c1a062.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240

[2]: http://upload-images.jianshu.io/upload_images/675733-f7b7aa3c83231f54.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240

