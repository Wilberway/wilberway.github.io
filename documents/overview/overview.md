# 前端的发展和趋势

##回顾

* 组件被用于构建复杂的UI，并由单一的文件构成，文件中同时包含HTML、CSS和JS。
* React、Redux、Webpack、ECMAScript2015和Babel被广泛采用。
* 在开发原生应用时，借助webview的混合式移动开发并不具备足够的优势，React Native和NativeScript开始替代webview开发。
* SASS继续受到欢迎，PostCSS（+CSSNext）开始发展。
* 开发者开始对HTML、JavaScript和CSS进行语法检查（ESLint替代了JShint）。
* Visual Studio Code成为了一个可以替代Sublime和Atom的编辑器。
* jQuery仍有热度，但是jQuery3没有人关注。
* Vue.js持续发展。
* JavaScript函数式编程和模式受到关注。
> 函数式编程相比指令时编程相比，函数式编程强调函数的计算比指令的执行重要。和过程化编程相比，函数式编程里，函数的计算可随时调用。
举例：

```javascript
function forEach(array, func){
    for(var i = 0; i < array.length; i++){
        func(array[i]);
    }
}
var a = ["a","b","c"];
forEach(a,function(obj){print(obj);});
forEach(a,function(obj){print(obj+1);});

/*
输出结果
a
b
c
a1
b1
c1
*/
```
```javascript
function reverse(func){
    return function(value){
        return !function(value);
    }
}

print(isNaN(NaN));
var isNotNaN = reverse(isNaN);
print(isNotNaN(NaN));
/*
输出结果
true
false
*/
```

* 离线开发和渐进式WEB应用（PWA）步入主流

>关于PWA：首先PWA是一个网页，可以通过Web技术编写出一个网页应用，随后添加上App Manifest和Service Worker来实现PWA的安装和离线等功能。

> 特点：
1. installability（可安装性）
2. App Shell
3. Offline（离线能力）
4. Re-engageable（通知推送）
缺点：
1. 门槛高（HTTPS、Service Worker）
2. 浏览器支持（Safari）
3. 用户习惯 

* 基于 web 技术，使用 NW.js 和 Electron 开发 windows，OSX 和 linux 原生应用的方式逐渐成型。

> NW.js是一个使用Web技术创建本地应用的框架，当你在使用普通的流程开发一个Web应用时，开发完成后，运行一个生成器，将所有东西编译成一个本地应用，它会像一个浏览器一样运行你的Web应用。

> Hybrid应用其优点不仅仅是可以使用熟悉的语言，还有以下几点：
1. 控制浏览器版本
2. 控制视窗，可以定义一个固定大小，或者最小化和最大化的视窗
3. 对本地文件的访问不会受同源策略的约束。

* 更多人开始重视自动化和测试
* 静态站点生成器被重视（JekyII、Hugo、Hexo、GitBook……）
* CSS网格布局（CSS Grid）势头正旺
> 就像表格一样，网格布局可以让Web设计师根据元素按列或行对齐排列，但他和表格不同，网格布局没有内容结构，从而使各种布局不可能与表格一样。

>CSS Grid和Flexbox：Flexbox是一维布局，他只能在一条直线上放置你的内容区块；而Grid是一个二维布局。

* NPM 受到来自 Yarn 的挑战。

> yarn为了解决一下问题：
1. 安装的时候无法保证速度/一致性
2. 安全问题，因为 npm 安装时允许运行代码

> yarn和npm的差异
1. 每次模块被添加时，Yarn 就会创建（或更新）yarn.lock 文件，这样你就可以保证其它机子也安装相同版本的包，同时包含了 package.json 中定义的一系列允许的版本。
2. 在 npm 中这些任务是按包的顺序一个个执行，这意味着必须等待上一个包被完整安装才会进入下一个；Yarn 则并行的执行这些任务，提高了性能。
3. 使用 npm install 时它会递归列出所有安装的信息；而 Yarn 则一点也不冗余，当可以使用其它命令时，它适当的使用 emojis 表情来减少信息（Windows 除外）。

* 下一代类 React 方案的演化通过 Preact、Deku、Rax 和 inferno 的形式展现，并伴随着少量 API 改动。这些库都相较React来说更加轻量并且更加注重性能。
* 此前大多数人学习接受 JSX，而如今他们已经享受其中。
* 一种可用的 CSS 模块模式（CSS encapsulation）已经实现并投入使用，因此对许多人来说，CSS in JS 成为一种切实可行的解决方案。

> 以前前端遵守一个规则，就是“关注点分离”，即不要写"行内样式"（inline style）和"行内脚本"（inline script）。React出现以后这个规则就不适用了。React 是组件结构，强制要求把 HTML、CSS、JavaScript 写在一起。随着 React 的走红和组件模式深入人心，这种"关注点混合"的新写法逐渐成为主流。

> 由于 CSS 的封装非常弱，导致了一系列的第三方库，用来加强 React 的 CSS 操作。它们统称为 CSS in JS，意思就是使用 JS 语言写 CSS。

* 越来越多人着手进行 UI 的功能性、整合性测试，其中包含例如可视化 CSS 和 RWD（译注：响应式网页设计，全称 Responsive web design）回归测试的概念。
* 得益于老版本 IE 使用、开发程度的大幅度降低，为浏览器 API 一致性而战的时代已离我们远去。
* 几乎人人都意识到开发网页的时候必须考虑多设备适配策略。
* 使用其他语言的开发者持续涌入 JS 领域，他们也带来了一些东西：例如类型检测，和对类语法以及面向对象思想的执念。

> Flow: 一个开源的 JavaScript 静态类型检查器，旨在发现 JS 程序中的类型错误，以提高程序员的效率和代码质量。

* 前端开发引入了热模块替换技术和时间旅行调试。

> 热模块替换（Hot Module ReplaceMent, HMR），再运行中对程序的模块进行更新。这个功能主要是用于开发过程中，对生产环境没有任何帮助，效果上就是界面的无刷新更新。

> Redux时间旅行：Redux 使用对象来表示状态，并使用纯函数计算下一个应用程序状态。这些特征使 Redux 成为了一个可预测 的状态容器，这意味着如果给定一个特定应用程序状态和一个特定操作，那么应用程序的下一个状态将始终完全相同。这种可预测性使得实现时间旅行变得很容易 — 能够在应用程序以前的状态中前后移动，并实时查看结果。

* 原生 JS 浏览器模块加载器更受期待了。
* Enforcing CSS 和 JS 格式规范变得更受重视（就 ES3 到 ES6 编码以及 CSS 预处理语法两者的变化而论）。（stylelint和eslint）
* 少部分开发者开始在 JS 上跑极限学习机（Extreme Learning Machine）算法，这足以引起注意。

> 极限学习机（extreme learning machine）ELM是一种简单易用、有效的单隐层前馈神经网络SLFNs学习算法。2004年由南洋理工大学黄广斌副教授提出。传统的神经网络学习算法（如BP算法）需要人为设置大量的网络训练参数，并且很容易产生局部最优解。极限学习机只需要设置网络的隐层节点个数，在算法执行过程中不需要调整网络的输入权值以及隐元的偏置，并且产生唯一的最优解，因此具有学习速度快且泛化性能好的优点。

* TypeScript 被正式使用在一些地方，并且圈了一些粉。
* aurelia 成为企业级开发者的明智之选（也就是说受到支持！）。
* Webpack 采取措施并巩固了优势地位，更胜一筹的 JSPM 解决方案暂居其下。
* HTTPS，嗯，这个我们很重视。
* BASH 在 windows 系统上展露头脚。
* 通知功能 API 可以被使用了，并在 chrome 上有些滥用，但这只会发生在你授予它权限之后。

> Notifications API 允许网页或应用程序在系统级别发送在页面外部显示的通知;这样即使应用程序空闲或在后台，Web应用程序也会向用户发送信息。

* FireBug 调试工具退出历史舞台。
* 2016年，CSS 20 岁了。
* Immutability 概念发展势头正旺。

> 不可变性(Immutability)是函数式编程的核心原则，在面向对象编程里也有大量应用。它的意思是，创建之后，就再也不能被修改了。

> 每当你想添加点东西到一个不可变(Immutable)对象里时，她一定是先拷贝以存在值到新实例里，然后再给新实例添加内容，最后返回新实例。相比可变对象，这势必会有更多内存、计算量消耗。

> 因为不可变(Immutable)对象永远不变，实际上有一种实现策略叫“结构共享”，使得她的内存消耗远比你想象的少。虽然和内置的array、object的“变化”相比仍然会有额外的开销，但这个开始恒定，绝对可以被不可变性(Immutability)带来的其它众多优势所消磨、减少。在实践中，不可变性(Immutability)带来的优势可以极大的优化程序的整体性能，即使其中的某些个别操作开销变大了。