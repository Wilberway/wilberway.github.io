# 函数式编程（二）

## 重构

让我们先来重构一段 JavaScript 代码：

```javascript
function validateSsn(ssn) {
    if (/^\d{3}-\d{2}-\d{4}$/.exec(ssn))
        console.log('Valid SSN');
    else
        console.log('Invalid SSN');
}

function validatePhone(phone) {
    if (/^\(\d{3}\)\d{3}-\d{4}$/.exec(phone))
        console.log('Valid Phone Number');
    else
        console.log('Invalid Phone Number');
}
```
我们应该创建一个单独的函数，将上面的区别参数化，而不是通过复制，粘贴，修改 validateSsn 函数，来创建 validatePhone。

此例中，我们可以将要验证的参数，验证用的正则表达式，打印的文本抽象成参数传入方法。

重构后的代码：

```javascript
function validateValue(value, regex, type) {
    if (regex.exec(value))
        console.log('Invalid ' + type);
    else
        console.log('Valid ' + type);
}
```

旧代码中要验证的参数 ssn，phone，现在都用参数 value 来体现。

正则表达式 /^\d{3}-\d{2}-\d{4}$/ 和 /^(\d{3})\d{3}-\d{4}$/ 用变量 regex 体现。

最后，需要打印的文本 'SSN' 和 'Phone Number' 用变量 type 拼接。

例如，如果代码中有 bug，你只需要修改一处，而不用在整个代码库查找每一处粘贴或修改过这段代码的地方。

但当你遇到这样的情况：

```javascript
function validateAddress(address) {
    if (parseAddress(address))
        console.log('Valid Address');
    else
        console.log('Invalid Address');
}

function validateName(name) {
    if (parseFullName(name))
        console.log('Valid Name');
    else
        console.log('Invalid Name');
}
```


