# 一些jQuery的小技巧

### 检查jQuery是否加载

在使用jQuery进行任何操作之前，你需要先确认它已经加载：

```javascript
if (typeof jQuery == 'undefined') {
  console.log('jQuery hasn\'t loaded');
} else {
  console.log('jQuery has loaded');
}
```

### 预加载图片

如果你的网页使用了大量并非立即可见的图片（例如悬停鼠标出发的图片），那么预加载这些图片就显得很有意义了：

```javascript
$.preloadImages = function () {
  for (var i = 0; i < arguments.length; i++) {
    $('<img>').attr('src', arguments[i]);
  }
};

$.preloadImages('img/hover-on.png', 'img/hover-off.png');
```

### 自动修复失效的图片
```javascript
$('img').on('error', function () {
  if(!$(this).hasClass('broken-image')) {
    $(this).prop('src', 'img/broken.png').addClass('broken-image');
  }
});
```

### 通过文本查找元素

通过使用 jQuery 的 contains() 选择器，你能够查找元素内容中的文本。若文本不存在，该元素将被隐藏：

```javascript
var search = $('#search').val();
$('div:not(:contains("' + search + '"))').hide();
```

### Ajax 调用错误处理

当一个 Ajax 调用返回 404 或 500 错误时，错误处理程序将被执行。若错误处理未被定义，其它 jQuery 代码可能不再有效。所以定义一个全局的 Ajax 错误处理：

```javascript
$(document).ajaxError(function (e, xhr, settings, error) {
  console.log(error);
});
```

### 链式插件调用

jQuery 允许通过“链式”插件调用的方法，来缓解反复查询 DOM 和创建多个 jQuery 对象的过程。

```javascript
$('#elem')
  .show()
  .html('bla')
  .otherStuff();
```

另一种方法是在变量（以 $ 为前缀）中，对元素进行缓存：

```javascript
var $elem = $('#elem');
$elem.hide();
$elem.html('bla');
$elem.otherStuff();
```