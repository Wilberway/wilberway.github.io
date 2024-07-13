# 函数式编程（四）

##柯里化

如果你还记得第三部分内容的话，就会知道我们在组合 mult5 和 add 这两个函数时遇到问题的原因是：mult5 接收一个参数而 add 却接收两个。

其实只需要通过限制所有函数都只接收一个参数，就可以轻易地解决这个问题。

相信我，这并没有听起来那么糟糕。

我们只需要来写一个使用两个参数，但一次只接收一个参数的 add 函数。柯里函数允许我们这样做。

> 柯里函数是一种一次只接收单个参数的函数。

这就可以让我们在将 add 和 mult5 组合之前只传递第一个参数给 add。然后当调用（组合后的） mult5AfterAdd10 函数时，add 函数就将得到第二个参数。

在 JavaScript 里，可以通过改写 add 函数来实现这个功能：

```javascript
var add = x => y => x + y
```

这个版本的 add 函数现在就只接收一个参数，之后再接收另外一个参数。。

详细来讲，这个 add 函数接收单参数 x，然后返回一个接收单参数 y 的函数，而这个函数最终就会返回 x + y 的结果。

现在我们就可以使用这个版本的 add 函数来构建一个 mult5AfterAdd10 函数的可运行版本：

```javascript
var compose = (f, g) => x => f(g(x));
var mult5AfterAdd10 = compose(mult5, add(10));
```

这个组合函数接收两个参数，`f` 和 `g`，然后它返回一个接收单参数 `x` 的函数，这个函数在调用的时候就会将 `g` 函数作用于 `x`，然后再将 `f` 函数作用于上一步的结果。

实际上我们到底做了什么呢？好吧，我们其实是将旧的 `add` 函数进行了柯里化。这么做就让 `add` 函数变得更加灵活，因为我们可以先把10作为第一个参数传入，而最后的参数则可以在 `mult5AfterAdd10` 被调用的时候传入。

看到这里，你可能会想知道在 Elm 里怎么来改写这个 `add` 函数。答案是，不需要改写。在 Elm 和其他函数式（编程）语言里，所有的函数都会自动柯里化。

所以这个 `add` 函数看起来和之前是一样的：

```javascript
add x y =
    x + y
```

`mult5AfterAdd10` 函数曾经在第三部分怎么写，也还是一样：

```javascript
mult5AfterAdd10 =
    (mult5 << add 10)
```

语法上讲，Elm 其实打败了像 JavaScript 这样的命令式（编程）语言，因为它在函数式方面是做了优化的，就像柯里化和组合函数。

## 柯里化和重构

柯里化在重构的的时候也能发挥它闪亮的一面，当我们创建一个多参数通用版本的函数时，我们可以通过柯里化的方法用它来创建接收更少参数的特定版本的函数。

举个例子，当我们有下面两个方法，在一个字符串前后分别添加一对大括号和两对大括号。

```javascript
bracket str =
    "{" ++ str ++ "}"

doubleBracket str =
    "{{" ++ str ++ "}}"
```

下面是如何使用它们：

```javascript
bracketedJoe =
    bracket "Joe"

doubleBracketedJoe =
    doubleBracket "Joe"
```

我们可以通用化 `bracket` 和 `doubleBracket` 函数：

```javascript
generalBracket prefix str suffix =
    prefix ++ str ++ suffix
```

但现在每当我们使用 `generalBracket` 时，都必须传入大括号：

```javascript
bracketedJoe =
    generalBracket "{" "Joe" "}"

doubleBracketedJoe =
    generalBracket "{{" "Joe" "}}"
```

我们实际上想要的是两全其美。

如果我们重新对 `generalBracket` 函数的参数进行排序，就可以创建柯里化后的 `bracket` 和 `doubleBracket` 函数了。

```javascript
generalBracket prefix suffix str =
    prefix ++ str ++ suffix

bracket =
    generalBracket "{" "}"

doubleBracket =
    generalBracket "{{" "}}"
```

注意到通常将静态参数放到前面，如 prefix 和 suffix，而可变参数尽量放到最后，如 str，这样，就可以简单地创建出 generalBracket 函数的特定版本了。

> 参数顺序对全面柯里化来说非常重要。

还注意到 bracket 和 doubleBracket 函数都是免参数（point-free）写法，如 str 参数是隐式表明的。bracket 和 doubleBracket 函数都在等待最后参数的传入。

现在就可以像之前那样使用了：

```javascript
bracketedJoe =
    bracket "Joe"

doubleBracketedJoe =
    doubleBracket "Joe"
```

但这次我们使用的是通用化的柯里函数：`generalBracket`。

## 常用的功能函数

让我们来看三个函数式（编程）语言里的常用函数。

但首先，来看看下面的 JavaScript 代码：

```javascript
for (var i = 0; i < something.length; ++i) {
    // do stuff
}
```

这段代码有一个主要的错误，但并不是 bug。问题在于这个代码是一个模板代码，就是那些一遍又一遍重复写的代码。

如果你是使用像 Java、C#、JavaScript、PHP 和 Python 等这样的命令式（编程）语言。你就会发现相比其他语言你会写更多这样的模板代码。

这就是这段代码的问题所在。

所以让我们来解决它。将它放到一个函数里（或者几个函数），然后再也不写 for 循环了。好吧，几乎不写，至少直到我们移步使用一个函数式（编程）语言。

首先从修改一个 things 数组来开始：

```javascript
var things = [1, 2, 3, 4];
for (var i = 0; i < things.length; ++i) {
    things[i] = things[i] * 10; // MUTATION ALERT !!!!
}
console.log(things); // [10, 20, 30, 40]
```

呃！！又是变量！

再试一次，这次不再去更改 `things` 数组了：

```javascript
var things = [1, 2, 3, 4];
var newThings = [];

for (var i = 0; i < things.length; ++i) {
    newThings[i] = things[i] * 10;
}
console.log(newThings); // [10, 20, 30, 40]
```

好了，我们没有更改 things 数组但技术上来说我们更改了 `newThings` 数组。目前为止，我们将忽略这个问题。毕竟我们在使用 JavaScript，一旦我们移步使用一个函数式语言，就不可以更改了。

这里的重点是弄明白这些函数是怎么工作的，以及它们怎么来帮助我们减少代码噪音（冗余等）。

来把这段代码放到一个函数里。接下来将调用我们第一个常用函数 `map`，它会将旧数组里的每个值映射成新值放到一个新的数组里。

```javascript
var map = (f, array) => {
    var newArray = [];

    for (var i = 0; i < array.length; ++i) {
        newArray[i] = f(array[i]);
    }
    return newArray;
};
```

注意到 `f` 函数，它作为参数传入，这样就可以让 `map` 函数对数组里的每一项进行任何我们想要的操作。

现在我们就可以使用 `map` 来改写之前的代码了：

```javascript
var things = [1, 2, 3, 4];
var newThings = map(v => v * 10, things);
```

看看，没有 for 循环，而且更简单易读，这就是（关于之前的代码错误）原因。

好吧，技术上来说，map 函数里是有 for 循环的，但至少我们不必再写一大堆模板代码了。

现在来写另外一个常用函数，从一个数组当中**过滤**一些数据：

```javascript
var filter = (pred, array) => {
    var newArray = [];

for (var i = 0; i  x % 2 !== 0;
var numbers = [1, 2, 3, 4, 5];
var oddNumbers = filter(isOdd, numbers);
console.log(oddNumbers); // [1, 3, 5]
```

使用新的 `filter` 函数比用 `for` 循环来手写实现简单太多了。

最后一个常用函数叫做 reduce。一般来说，它用来接收一个列表并将其减少到一个值，但实际上可以用它做更多的事情。

在函数式（编程）语言里这个函数通常叫做 `fold`。

```javascript
var reduce = (f, start, array) => {
    var acc = start;
    for (var i = 0; i < array.length; ++i)
        acc = f(array[i], acc); // f() takes 2 parameters
    return acc;
});
```

这个 `reduce` 函数接收一个（自定义）减少函数 `f`、一个初始 `start` 开始值和一个 `array` 数组。

注意到这个减少函数 `f`，接收两个参数，`array` 数组的当前项，以及累计器 `acc`。每次迭代，它都将使用这两个参数产生一个新的累计器，最后一次迭代得到的累计器将会被返回。

一个例子将帮助我们更好地来理解它如何工作：

```javascript
var add = (x, y) => x + y;
var values = [1, 2, 3, 4, 5];
var sumOfValues = reduce(add, 0, values);
console.log(sumOfValues); // 15
```

注意到 `add` 函数接收两个参数并把它们相加。而 `reduce` 函数正是期望一个接收两个参数的函数，所以它们可以一起正常运行。

我们将初始 `start` 值设为0，并将 values 数组传入进行计算。`reduce` 函数内部，`values` 数组各项的总值作为累计器循环计算。最后的累计值返回为 `sumOfValues`。

每个这些函数，`map、filter` 和 `reduce`，都让我们可以在不必写 `for` 循环的情况下对数组进行常用操作。

但是在函数式（编程）语言里，它们甚至更有用，因为没有循环体只有递归。迭代函数不只是非常有用，它们是必要的。