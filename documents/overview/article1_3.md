# JavaScript 姿势提升简略

## 组织代码

1. 分离JavaScript和HTML

2. 框架：使用框架讲网站重写为一个单页应用，使用MVC或者MVVM等。

3. 设计模式：设计模式在抽象层面上是有意义的，但是在实际工作中，没有什么用。在实际项目的环境下，挑选并应用设计模式是件很困难的事情。

4. 模块：模块模式是最简单也是最容易应用到现有代码里的。

纵而览之，模块模式就是一系列代码之外加了个包装。你抽取出一系列功能相关的代码扔到一个模块里，决定需要暴露的部分，也可以把一个模块里的代码放到不同的文件里。然后建立一个易于在项目之间共享的代码黑匣。

举例：
```javascript
var counterModule = (function() {
  var counter = 0;

  return {
    incrementCounter: function () {
      return counter++;
    },
    resetCounter: function () {
      console.log("counter value prior to reset: " + counter );
      counter = 0;
    }
  };

}());
```

模块化不是什么高深的东西，但它使我们的代码更干净，更简单 ，这绝对是件好事。

## 代码检验

代码检验表示使用最佳实践和一些避免出错的规则对代码进行检查。


不同用途的代码检验器有 JavaScript(ESLint、JSLint和 JSHint)，HTML(HTMLHint和 W3C Validator)和CSS (CSSLint)

## 测试

你也许听过 TDD (测试驱动开发)。说的是在写具体代码之前先把单元测试写好。本质上是测试主导你的开发。写下代码并看它通过测试的时候，这些通过的测试能让你确保自己没有走错路。

关于测试框架我选择 Jasmine。Jasmine 的测试易于编写和运行。最快的使用方法是下载这个库。解压后你会发现 SpecRunner.html 文件。此文件负责引入我们的代码，引入测试，而后运行测试和生成漂亮的报告。

关于日期和时间的牛库 Moment.js，不是我骗你，有超过五万七千多个测试。

JavaScript 测试框架的其他选择有 QUnit和 Mocha。和代码检验一样，你能使用 Grunt 之类的工具自动化测试，甚至可以往全栈靠一点，使用 Selenium 测试浏览器。