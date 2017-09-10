# 5分钟看完ECMAScript 2016

> ECMAScript标准制定过程包含四个阶段：提议(Proposal)、草案(Draft)、候选(Candidate)、完成(Finished)。每个新特性在进入标准前都必须走完这四个阶段。因此，只有进入最后一个阶段的特性能被包含在下一版本的JavaScript。

从 ES2016 开始，ECMAScript标准的制定原则是成文标准要从事实标准中诞生，实现先于标准存在。ECMAScript 2016的deadline是1月28日，虽然当时有22个处于不同阶段的特性，但仅有2个进入完成（Finished）阶段（我们期待的Async由于主流引擎还未完善并缺少足够的测试，只能在ES2017中看到了...）：**Array.prototype.includes**和**幂运算符**(Exponentiation Operator）。所以在1月底的TC39的会议中，只有这两个部分进入了ECMAScript 2016的标准当中。

## Array.prototype.includes

这是个数组方法，遍历整个数组，若数组中存在该参数，则返回true，否则返回false。

举个栗子：

```javascript
[1, 2, 3].includes(2);     // true
[1, 2, 3].includes(4);     // false
[1, 2, 3].includes(3, 3);  // false
[1, 2, 3].includes(3, -1); // true
[1, 2, NaN].includes(NaN); // true
```

浏览器的支持情况： 

![pic1][1]

## 幂运算符

幂运算符（exponentiation operator）返回第一个操作数做底数，第二个操作数做指数的乘方。

operater： **var1 ** var2**

幂运算符是右结合的。a ** b ** c 等同于 a ** (b ** c)。

举个栗子：

```javascript
var a = 4;
var b = 3;
var c = 2;
a ** b;         //64
a ** b ** c;    //262144，相当于 4**(3**2)
```

目前只有Firefox 42以上的版本支持幂运算符。

 [1]: ./1.png