# 函数式编程（一）

## 函数式编程的特点

1. **纯粹**

函数式编程语言中的纯粹指的就是纯函数。

```javascript
var z = 10;
fucntion add(x,y){
    return x + y;
}
```

> 注意，add函数没有碰z变量。它既不读z也不写z。它只是读了 x 和 y 参数，然后返回了两者的和。如果 add 动了 z 变量，它就不再纯粹了。

```javascript
fucntion justTen(){
    return 10;
}
```

> 如果 justTen 是纯函数，它就只能返回一个常量。如果是纯函数，它就不能存取自身的输入参数之外的任何东西，所以它只能返回一个常量。

我们再回过头看看第一个 add 函数：

```javascript
function add(x, y) {
    return x + y;
}
console.log(add(1, 2)); // prints 3
console.log(add(1, 2)); // still prints 3
console.log(add(1, 2)); // WILL ALWAYS print 3
```

add(1, 2) 总是返回 3。结果不出所料，这毕竟是个纯函数。如果 add 函数用了其他外部值，就没法预测它的行为了。

> 纯函数对相同的输入总能产生相同的输出。

2. **不可变性**

```javascript
var x = 1;
x = x + 1;
```

但是在指令式编程中，这段代码表示将 x 的当前值加 1 再赋值回 x。

但是在函数式编程中 x = x + 1 是错误的。

> 函数式编程中没有变量

存储的值还是叫做变量，不过这是历史原因，它们其实是常量。比如一旦 x 有了一个值，这个变量就一直是这个值。

不要担心，x 通常是个局部变量，生命周期很短。但是只要它还在，值就不会变。

> 函数式编程的循环用递归实现

下面的代码展示了 Javascript 创建循环的两种方式：

```javascript
// simple loop construct
var acc = 0;
for (var i = 1; i <= 10; ++i)
    acc += i;
console.log(acc); // prints 55

// without loop construct or variables (recursion)
function sumRange(start, end, acc) {
    if (start > end)
        return acc;
    return sumRange(start + 1, end, acc + start)
}
console.log(sumRange(1, 10, 0)); // prints 55
```

看看函数式编程中的递归是如何实现 for 循环的：就是用新起始值(start + 1)和新累积值(acc + start)不断地调用自身。它没有修改旧值，而是使用由旧值计算出来的新值。

不幸的是，即使学过一段时间 JavaScript 你也很难用到这种写法，原因有二。第一，JavaScript 语法很繁琐，第二是你可能不习惯递归式思考。

不过一个显而易见的好处就是，如果对程序中的变量有访问权限，也只是只读权限，这也就是说，再也没人能改变这个值，哪怕是你自己。所以省去了很多意想不到的麻烦。

而且，如果是多线程程序，其他线程就无法干扰到当前线程。如果当前线程有一个常量而且其它线程试图改变它，其他线程只能用旧值复制一个新值出来。

> 不可变性使代码更简单，安全。