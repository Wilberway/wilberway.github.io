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

## 展望

* Web Assembly 有望达到一个新的高度。

> Web Assembly主要是为了解决JavaScript性能不够理想，以及语言本身的一堆坑（这个大家都懂）。WebAssembly 将是一个编译型语言，WebAssembly 将是一个编译型语言。

> WebAssembly 都更贴近机器码，所以它更快，使它更快的原因有几个：
1. 在编译优化代码之前，它不需要提前运行代码以知道变量都是什么类型。
2. 编译器不需要对同样的代码做不同版本的编译。
3. 很多优化在 LLVM 阶段就已经做完了，所以在编译和优化的时候没有太多的优化需要做。

* 有望在 `<script></script>` 中使用 import 进行模块懒加载。

* JavaScript 同构解决方案持续增长，致敬服务器端输出前端内容的时代（即：页面直出到浏览器）

>基于React和服务器的Web应用的框架Next.js和基于Vue的服务器渲染工具Nuxt.js。

* 响应式编程继续茁壮成长。

> RxJS: Javascript的响应式扩展, 响应式的思路是把随时间不断变化的数据、状态、事件等等转成可被观察的序列(Observable Sequence)，然后订阅序列中那些Observable对象的变化，一旦变化，就会执行事先安排好的各种转换和操作。 RxJS适用于异步场景，即前端交互中接口请求、浏览器事件以及自定义事件。
1. 统一异步编程的规范，不管是Promise、ajax还是事件，通通封装成序列(Observable Sequence)，一旦有异步环节发生变更，观察序列即可截获发生变更的信息。
2. 前端业务层和展现层解耦，比如展现层不需要关系指定事件触发时和DOM无关的处理逻辑。同时业务层也能组装异步操作中多个异步逻辑之间的关系，无需暴露给展现层。展现层关心的是：异步操作其中环节的数据变化。
rxjs开发业务层具有高弹性，高稳定性，高实时性等特点。
3. 废话不多说，此篇文档结合模拟场景的例子，通过傻瓜式的描述来说明rxjs常用的方法以及组合关系。

> MobX 是一个简单、方便扩展、久经考验的状态管理解决方案。MobX 是一个独立的库，不过大多数人都把它和 React 一起使用。相比redux来说，更简单，更灵活。

* React，尤其是它倡导的概念继续占有支配地位。而 React 本身会被彻底重写（React Fiber）或者进化（Inferno）。

* Angular 终于决定遵循 SEMVER 规范，所以 Angular4（甚至于 Angular5）有望在 2017 年发布。

> 语义化版本控制规范(SemVer)
> 标准的版本号必须采用 XYZ 的格式，其中 X、Y 和 Z 为非负的整数，且禁止在数字前方补零。X 是主版本号、Y 是次版本号、而 Z 为修订号。每个元素必须以数值来递增。例如：1.9.1 -> 1.10.0 -> 1.11.0。

* 简单的网站即 Web 1.0 可能会重新流行，但会建立在 2017 年新工具的基础上。
* RESTful JSON APIs 会更有竞争力
* 2017 可能是 VueJS 的丰收年。
* 越来越多的开发者在做静态站点以及 API CMS tools 时开始抛弃传统的 CMS 解决方案。
* 更多的人从 Sass 转向 PostCSS + CSSNext。
* 越来越多地见到 HTTP2 和 HTTPS 的身影。
* Web Components 继续潜伏等待开发者们助力实现前所未有的大爆发。

> 组件化给前端开发带来了极大的效率提升，组件化的UI框架也因此层出不穷，从EXTJs、YUI到 jQuery UI ，再到 Bootstrap、React、Ratchet、Ionic等等等等等等，几乎每年都有很多新的UI框架冒出来，它们或者借鉴或者颠覆其他已存在的框架。简单对比一下就会发现这些框架的很大一部分模块在功能上是重合的，但也仅仅在功能层面重合，代码层面确完全不兼容。
> 组件框架目前无序、缺乏标准以及低效复用方面的问题需要通过组件标准化来解决，而Web Components则是标准化的一个很好的选择。
> 面向未来的组件标准Web Components 的出现给组件标准化带来了很好的契机：
1. WEB组件目前仍然依靠各种类似”Hack”的方式来模拟，模拟方式也各有不同，很难统一和标准化，而 Web Components 则直接提供了标准化的组件定义方式，这是组件标准化的基石，使得未来的组件能够统一创建、方法调用、事件监听、属性访问等。
2. 基于标准化的组件定义方式，我们便可以像W3C等标准组织一样来定义组件标准，无需再依赖、等待“内置”组件，这也使得我们获得了“渔”的能力。

* 无框架的框架势头正猛。
> Svelte: 的核心思想在于『通过静态编译减少框架运行时的代码量』。举例来说，当前的框架无论是 React Angular 还是 Vue，不管你怎么编译，使用的时候必然需要『引入』框架本身，也就是所谓的运行时 (runtime)。但是用 Svelte 就不一样，一个 Svelte 组件编译了以后，所有需要的运行时代码都包含在里面了，除了引入这个组件本身，你不需要再额外引入一个所谓的框架运行时！

* JavaScript 标准即将尘埃落定，同时期待 CSS 也能迎来大爆发，并早日稳定下来， 否则开发者们始终惶惶不可终日。
* 相对于开放的 Web，对于 App Store 的仇恨与日俱增。
* Redux 继续接受来自竞争对手的激烈挑战。(例如MobX)
* YARN 将赢得更多的粉丝。
* "Front-end apps"、"Thick Client apps"、"Static apps"、"No Backend app"、"SPA's"、"Front-end driven app" 这些理念可以归结为一个概念："JAM Stack"。