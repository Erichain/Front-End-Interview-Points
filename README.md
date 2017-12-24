## 前端知识点集锦
收集关于前端的各个方面的知识

### 关于前端是什么，以及需要学习什么，移步这里：

#### [Front-End Developer Handbook](https://github.com/FrontendMasters/front-end-handbook-2017)

---

### HTML部分

#### docType

- 混杂模式
	- 触发条件：不加文档类型声明
- 标准模式
	- 触发条件：`<!DOCTYPE html>`

#### 标签语义化

- 去掉或者丢失样式的时候能够让页面呈现出清晰的结构
- 有利于 SEO：和搜索引擎建立良好沟通，有助于爬虫抓取更多的有效信息：爬虫依赖于标签来确定上下文和各个关键字的权重
- 方便其他设备解析（如屏幕阅读器、盲人阅读器、移动设备）以意义的方式来渲染网页
- 便于团队开发和维护，语义化更具可读性，是下一步网页的重要动向，遵循 W3C 标准的团队都遵循这个标准，可以减少差异化

#### 替换元素和非替换元素

- 替换元素
	- `img, object, iframe, video` 等。即元素本身没有实际内容，通过元素的标签和属性来显示内容
- 非替换元素
	- 大多数标签属于非替换元素，这部分标签把标签里的内容直接告诉浏览器显示出来

#### meta 标签

- 如何在不使用JS的情况下刷新页面（`<meta http-equiv="refresh" content="time">`）
- 设置页面缓存（`<meta http-equiv="cache-control" content="no-cache">`）
- 移动端设置

#### HTML 代码优化

- 标签嵌套层级不要太深，标签尽量简洁化.如懒加载后将 data 属性去除
- 大量图片的懒加载策略，以及一些元素利用 ajax 在 onload 后实行延迟加载
- 对一些 js 的异步加载

#### 搜索引擎优化 SEO

#### 关于 HTML，CSS 的一些鲜为人知的知识

1、对于 `box-sizing`，最好将其设置为 `border-box`，这样，设置了宽高再设置 padding 的时候，它的尺寸就不会再变化了；

2、设置浮动的元素在 HTML 文档中需要排列在其余未设置浮动的元素之前，否则，浮动的元素默认就会一直在页面下方；

3、设置了浮动的元素默认会被设置为块级元素；

4、边距折叠只会发生在毗邻的元素上，定位或者浮动的元素不会发生边距折叠，同时，边距折叠只有纵向的，没有横向的；Flexbox 的子元素不会发生边距折叠；

5、对 button 要总是设置 type 属性，form 里面的 button 如果不设置 type 的话，默认为提交按钮；

6、对于 form，避免在 input 中按回车的时候提交表单，最好设置 form 的 `onsubmit` 属性为 `return false;`；

7、设置 fixed 定位的元素相对于浏览器窗口，但是，设置了 absolute 定位的元素不一定相对于其设置了 relative 定位的元素进行定位，而是相对于最近的设置的 position 属性不为 `static` 的父级元素进行定位；

8、CSS 属性不区分大小写；

#### `img` 标签的跨域设置

> 尤其是在使用 canvas 画图的时候会用到

``` vbscript-html
<img src="" alt="" crossOrigin="anonymous">
```

---

### CSS 部分

#### 浮动，清除浮动的方法和原理(4 种方法)

- 使用空标签设置 `clear: both;`（`clear` 有哪些值可以设置？应用在什么元素上？）
- 为父级元素设置 `overflow: hidden;` (利用 BFC 的原理，除了设置 `hidden`，还能设置其他的值吗？)
- 使用伪元素，为要清除浮动的元素添加 `.clearfix` 类(推荐，其原理可查看 http://nicolasgallagher.com/micro-clearfix-hack/)
- 使用 `min-height: contain-floats;` (不推荐，兼容性不好)

#### CSS 块级格式化上下文

- 触发条件
	- `position` 属性不为 `static` 或者 `relative`
	- `float` 属性不为 `none`
	- 非块级的块级元素 (inline-block, table-cell)
	- `overflow` 不为 `visible`
- 特性
	- 内部的 Box 会在垂直方向，从顶部开始一个接一个地放置
	- Box 垂直方向的距离由 margin 决定。属于同一个 BFC 的两个相邻 Box 的 margin 会发生叠加
	- BFC 的区域不会与 float box 叠加
	- BFC 就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素，反之亦然
	- 计算 BFC 的高度时，浮动元素也参与计算
- 用处
	- 解决 margin 边距叠加问题。为元素单独创建一个 BFC 来防止外边距的折叠
	- 清除浮动。为包含浮动元素的 container 创建 BFC 来清除浮动

#### 盒子模型（IE 盒子模型的区别）

- 总宽度 ＝ margin ＋ padding ＋ border ＋ content，IE 的盒子模型的宽度不计 padding 和 border
- css3 的 `box-sizing` 属性，详见 https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing
	- content-box，border 和 padding 不计算入 width 之内
	- border-box，border 和 padding 计算入 width 之内

#### position vs float

> 定位和浮动的区别？

> 什么时候使用定位，什么时候使用浮动？

> 如何使用定位或者浮动来进行布局？有什么优点或者缺点？

> 设置了定位或者浮动的元素对标准文档流有什么影响？

#### z-index 属性

> z-index 对哪些元素起作用？

> z-index 的层级关系是怎么样的？

- z-index 与 Stacking Context 相关，详见 https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context

#### 布局模型

- 两列(三种)和三列布局(五种方式)
	- [Columns-Layout](http://codepen.io/Erichain/pen/mOZNxE)
- 弹性布局
- 流式布局
- 瀑布流布局
- 多列布局等高

#### CSS 优先级

- 行内样式 > 内联样式 > 外部样式，ID > Class > Element
- 设置了 `!important` 的样式优先级更高

#### Flexbox

- [A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

> Flexbox 内部的元素会发生 margin collapse 吗？

> Flexbox 的子元素可以设置 z-index 吗？

#### 各个单位的区别（px, em, rem, 百分比, vw, vh, vmax, vmin）

- [Understanding Font sizing in CSS: em – px – pt – percent – rem](https://www.narga.net/understanding-font-sizing-in-css-em-px-pt-percent-rem/)
- [REM vs EM – The Great Debate](http://zellwk.com/blog/rem-vs-em/?utm_source=CSS-Weekly&utm_campaign=Issue-204&utm_medium=email)

> rem 所相对的根元素是指哪一个元素？

#### CSS Grid

- [A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)

#### 居中

- [CSS Center Complete](https://github.com/Erichain/css-center-complete)

#### CSS 工程化

- [OOCSS](http://oocss.org/)
- [BEM](http://getbem.com/)
- [SMACSS](https://smacss.com/)
- [ITCSS](https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture/)
- [styled-components](https://www.styled-components.com/)

[An Overview Of OOCSS BEM SMACSS](http://codetheory.in/an-overview-of-oocss-bem-smacss/)

> 样式文件结构如何组织？

**Some Questions**

#### 如何将 div 与图片设置等宽，inline-block 元素之间的空隙如何解决

- 设置父元素 `font-size` 为 0，再对里面的文字单独设置 `font-size`
- 全兼容的样式解决方法

``` scss
.finally-solve {
  // 根据不同字体字号或许需要做一定的调整
  letter-spacing: -4px;
  word-spacing: -4px;
  font-size: 0;
}

.finally-solve li {
  font-size: 16px;
  letter-spacing: normal;
  word-spacing: normal;
  display:inline-block;
  *display: inline;
  zoom:1;
}
```

#### `text-overflow` 可以用来设置文本省略显示，那么，多行文本的省略显示如何设置？

``` scss
.truncate-multiple-line($fontSize: 14px, $lineCount: 3, $lineHeight: 1.4) {
  font-size: $fontSize;
  line-height: $lineHeight;
  display: block;
  display: -webkit-box;
  overflow: hidden;
  max-height: calc($lineHeight * $lineCount * $fontSize);
  text-overflow: ellipsis;
  -webkit-line-clamp: $lineCount;
  -webkit-box-orient: vertical;
}
```

---

### JavaScript 部分

> JavaScript 的历史发展？

> 为什么要设计 JavaScript？为了解决什么问题？

#### 变量

- 使用 var 定义的全局变量不能使用 delete 删除
- 无 var 创建的全局变量可以使用 delete 删除（为什么可以删除？全局变量与 Object.prototype 有什么关系？）
- 隐式类型转换
	- 数字与字符串相加，结果为字符串
	- 数字与字符串相减，结果为数字
	- 比较变量的是否相同时，要采用 `===`，`==` 会发生隐式类型转换
	- NaN 与任何变量不相等（如何判断 `NaN` 呢？）

> 变量是如何初始化的？

> 类型转换的时候，如果同时存在 `toString` 和 `valueOf` 方法，会如何处理？

#### 类型检测

- `typeof`
- `instanceof`
- `Object.prototype.toString.apply()`（在 ES6 里面这个方法是否一定准确？）

#### 对象

> 对象可以怎么创建？有哪些方式？区别是什么？可以用到什么模式？

> 在对象创建的时候设置好属性与动态添加属性有什么区别？

- `hasOwnProperty, isPrototypeOf, propertyIsEnumerable`
- 配置属性 (`configurable, enumerable, writable, value`)
- 特性
	- 扩展: `isExtensible`, `preventExtensions` (是否可以添加新的属性)
	- 密封: `isSealed`, `seal` (是否可以删除属性，是否可以配置属性)
	- 冻结: `isFrozen`, `freeze` (所有属性是否可读可写)
- 定义属性
	- `defineProperty`, `defineProperties`

#### 函数

> 普通函数与 arrow function 的区别？

> 函数的默认参数和解构赋值的默认值工作机制？哪种情况下会采用默认值？

- 柯里化
	- 概念：部分求值（Partial Evaluation），是把接受多个参数的函数变换成接受一个单一参数（最初函数的第一个参数）的函数，并且返回接受余下的参数而且返回结果的新函数的技术（curry 的作用是什么？为什么需要 curry？）

``` javascript
function currying(fn) {
  const args = Array.prototype.slice.call(arguments, 1);
  
  return function () {
    const newArgs = args.concat(Array.prototype.slice.call(arguments));
    return fn.apply(null, newArgs);
  }
}
```
- JavaScript 函数不存在重载，后定义的函数会覆盖先定义的函数
- 函数调用模式
	- 方法调用
	- 函数调用
	- 构造器调用
	- apply 调用
- 高阶函数
	- 高阶函数与普通函数有什么区别？
	- 为什么需要高阶函数？

#### 作用域

> JavaScript 的作用域链是怎么工作的？

> JavaScript 的变量对象，活动对象，执行栈是怎么样的？与作用域有什么关系？

> ES6 之后的版本中的作用域是什么样的？

#### `new` 操作符的原理

使用 `new` 关键字来创建实例的时候，原理如下：

- 首先，在构造函数内部使用 `Object.create(constructor.prototype)` 创建一个对象继承自构造函数
- 然后，将构造函数的 `this` 指向改变到创建的对象
- 最后，返回创建的对象

``` javascript
function newFunc(ctor, ...args) {
  let proto = Object.create(ctor.prototype);
  ctor.call(proto, ...args);
  return proto;
}
```

#### 闭包

- 概念
- 作用
	- 创建匿名执行函数
	- 缓存变量，防止被垃圾回收
	- 实现函数的封装
- 应用场景
	- 内部函数访问外部函数的变量
	- 使用闭包代替全局变量
	- 封装相关功能
	- 回调函数
	- 创建私有变量和公有变量
- 特性

> 闭包函数内部的 this 值是如何变化的？

> arrow function 内部的 this 值是怎么样的？

#### this

- 函数的 `this` 的值永远绑定在调用此函数的对象上
- 可以使用 `apply`，`call` 或者 `bind` 改变 `this` 值的指向

#### 原型

- 原型链是如何工作的？
- `__proto__` 属性与 `prototype` 的关系？
- 原型链有终点吗？终点是什么？
- 如何设置对象的原型？

#### 继承

**借用构造函数**

``` javascript
function Person(name) {
  this.name = name;
}

function man() {
  // 继承自 Person，可以选择是否传入参数
  Person.call(this, 'Erichain');
}
```

**组合继承**

**原型式继承**

**寄生式继承**

**寄生组合式继承**

- `new Object()` 和 `Object.create()` 的区别
	- `Object.create` 创建的对象直接从他的第一个参数继承，而 `new Object` 所创建的对象是从对象的原型上继承
	- 使用 `Object.create`，可以创建一个不继承于任何东西的对象，但是，如果设置 `someConstructor.prototype = null`，那么，这个新创建的对象会继承自 `Object.prototype`
	
> 实例与构造函数与 Object.prototype 的原型之间的关系是怎么样的？
	
#### ES6 Class

> class 内部是如何处理原型和 this 值的绑定的？

> super 的原理是什么？

> static 关键字的原理？

> 属性是添加到对象的哪个地方？

#### 变量提升，函数声明提升

- 函数声明优于变量声明
- 函数声明会覆盖变量声明，但是不会覆盖变量赋值

> ES6 还有变量提升吗？TDZ 是怎么形成的？会造成什么样的影响？

#### 事件

> 如何将事件绑定到 document 上？

> React 是如何处理多个元素的事件的？

> React 的事件对象和原生事件对象有什么区别？

- 事件流的三个阶段
	- 事件捕获
	- 处于目标
	- 事件冒泡

**跨浏览器事件处理函数**

``` javascript
const EventUtil = {
  getEvent(event) {
    return event ? event : window.event;
  },
  getTarget(event) {
    return event.target || event.srcElement;
  },
  addHandler(elem, type, handler) {
    if (elem.addEventListener) {
      elem.addEventListener(type, handler, false);
    } else if (elem.attachEvent) {
      elem.attachEvent('on' + type, handler);
    } else {
      elem['on' + type] = handler;
    }
  },
  preventDefault(event) {
    if (event.preventDefault) {
      event.preventDefault();
    } else {
      event.returnValue = false;
    }
  },
  stopPropagation(event) {
    if (event.stopPropagation) {
      event.stopPropagation();
    } else {
      event.cancelable = true;
    }
  }
};
```

**事件代理**

``` vbscript-html
<ul id="links">
  <li id="link1">Link1</li>
  <li id="link2">Link2</li>
  <li id="link3">Link3</li>
</ul>
```

``` javascript
var links = document.getElementById('links');

// 使用之前定义的跨浏览器事件处理程序
EventUtil.addHandler(links, 'click', function (event) {
  const target = EventUtil.getTarget(event);
  event = EventUtil.getEvent(event);

  switch (target.id) {
    case 'link1':
      // do something
      break;
    case 'link2':
      // do something
      break;
    case 'link3':
      // do something
      break;
  }
});
```

> 为什么要使用事件代理？有什么好处？

- 事件函数的参数(注意 `addEventListener()` 的最后一个参数，如果为 false 表示在冒泡阶段获取事件，如果为  true，表示在事件捕获阶段获取事件)

#### promise

- [Javascript Promise 迷你书](http://liubin.org/promises-book/)
- [JavaScript Promise API](http://mp.weixin.qq.com/s?__biz=MzAxODE2MjM1MA==&mid=402552108&idx=1&sn=b0d4d986984a45276c6bbbf386c04790&scene=0#wechat_redirect)
- https://pouchdb.com/2015/05/18/we-have-a-problem-with-promises.html

> `.catch` 与 `.then(null, function () {})` 的区别？

> 在 `.then` 中返回一个函数与直接执行一个函数的区别？

> promise 的 `.then` 与 setTimeout 的回调的执行顺序？

> promise 有什么优缺点？

#### generator

> generator 用来干什么？

> 如何使用 generator 来创建异步行为？

> 使用 generator 实现 async 和 await？

> 在 yield 后面执行另外一个 generator 是怎么工作的？

#### async and await

#### Set && Map

> weak Set(Map) 与 Set(Map) 的区别？

> Map 与对象的区别？

> Set 与 Map 的适用场景？

#### Decorator

> 什么是 Decorator？如何使用？可以用来干什么？

> 原理是什么？

> 与 React 可以怎么结合？与其他框架呢？

#### JavaScript 中的 Event Loop，Job Queue 与 Task，MicroTask

> 什么是 Event Loop？什么是 Job Queue？什么是 Task，什么是 MicroTask？

> Event Loop 的工作流程是怎么样的？与执行栈的关系？

> Event Loop，Job，Task 的执行顺序是怎么样的？

#### 性能优化

> React 是怎么批量更新 DOM 的？

> CDN 是什么？如何应用？有什么好处？

- 操作 DOM 的时候一定要缓存变量，避免发生大量的重排重绘
- 异步加载 JavaScript 文件
	- 使用 `document.write()`
	- 动态改变已有 script 标签的 `src` 属性
	- 使用 DOM 方法动态创建 script 元素
	- 使用 Ajax 获取脚本内容再加载
	- 在 script 标签中使用 `defer` 以及 `async` 属性（defer 和 async 的区别？）
	- 按需加载
- 合并文件
- 图片懒加载
	- [懒加载——网页图片的加载技术](https://segmentfault.com/a/1190000003881643)
	- [Lazy Load Plugin for jQuery](https://github.com/tuupola/jquery_lazyload)
- 预加载
	- [3 Ways to Preload Images with CSS, JavaScript, or Ajax](https://perishablepress.com/3-ways-preload-images-css-javascript-ajax/)
	- [Prefetching, preloading, prebrowsing](https://css-tricks.com/prefetching-preloading-prebrowsing/)
- prefetch
	- [HTML5 Prefetch](https://medium.com/@luisvieira_gmr/html5-prefetch-1e54f6dda15d)
- 函数节流
	- [浅谈函数节流](http://mp.weixin.qq.com/s?__biz=MzAxODE2MjM1MA==&mid=402737833&idx=2&sn=c051cfa8a5ea025da9129295d666743a&scene=0#wechat_redirect)
- 函数式，抽象，组件复用，减少无用代码

#### 内存管理

> 引用计数是怎么工作的？有什么弊端？

- 引用计数

``` javascript
// 出现循环引用的例子
function loopRef() {
  const objectA = {};
  const objectB = {};

  objectA.someOtherObject = objectB;
  objectB.anotherObject = objectA;
}
```

- 标记清除，详细可查看 https://blog.sessionstack.com/how-javascript-works-memory-management-how-to-handle-4-common-memory-leaks-3f28b94cfbec

- 内存泄漏
    - setTimeout 的第一个参数使用字符串而非函数的话，会引发内存泄漏
    - 循环引用
    - DOM 元素的引用可能会触发内存无法被回收

#### XMLHttpRequest 对象

- 一段比较完整的使用原生 JavaScript 实现 ajax 请求方法

``` javascript
function createRequestObject() {
  if (window.XMLHttpRequest) {
    return new XMLHttpRequest();
  }

  // 针对IE
  else if (window.ActiveXObject) {
    return new ActiveXObject('Microsoft.XMLHTTP');
  }
}

// 请求的回调函数
function requestCallBack() {
  if (request.readyState === 4 && request.status === 200) {
    console.log(request.responseText);
  }
}

const request = createRequestObject();

request.onreadystatechange = requestCallBack;
// open 函数的三个参数分别是请求的方法, 请求的地址, 是否异步 (true 表示异步)
request.open('POST', url, true);
request.send(null);
```

#### `Array.prototype.slice.call()`原理

- [how does Array.prototype.slice.call() work?](http://stackoverflow.com/questions/7056925/how-does-array-prototype-slice-call-work)

#### RESTful

#### 尾递归

- [尾调用优化](http://es6.ruanyifeng.com/#docs/function#尾调用优化)

> 尾递归的原理是什么？为什么能够达到性能优化？

> 所有的函数都能进行尾递归优化吗？尾递归优化的条件是什么？

---

### 浏览器部分

#### 浏览器针对页面的渲染过程

- [How browsers work](http://taligarsiel.com/Projects/howbrowserswork1.htm#Introduction)

> 设置了 `display: none` 的元素节点会被渲染吗？设置了 `visible: hidden` 的元素呢？

> 外部 CSS，内联 CSS，行内 CSS 的加载顺序是怎么样的？

> 渲染分为哪几个阶段？每一个阶段具体做了什么？

> 重排和重绘的区别？

> 什么情况会触发重排？什么情况会触发重绘？

> 如何针对浏览器的渲染过程就进行优化？

#### 关于浏览器缓存

- [浅谈Web缓存](http://www.alloyteam.com/2016/03/discussion-on-web-caching/)
- cookie 由服务器生成，可设置失效时间。如果是浏览器端生成的 cookie，则在浏览器关闭之后失效；而 localStorage 除非被清除，否则永久保存，sessionStorage 则在关闭浏览器或者页面之后清除
- cookie 的大小为 4k 左右，localStorage 和 sessionStorage 的大小一般为5MB
- 与服务器通信的时候，cookie 每次都会携带在 http 头中，但是其他两个不参与服务器通信
- cookie 中最好不要放置任何的明文的东西，其他两个的数据如果提交到服务器一定要校验

> sessionStorage, cookie, localStorage 的适用场景？

---

### 前端安全

- 防止 XSS (跨站点脚本)攻击
	- [XSS Prevention Rules](https://www.owasp.org/index.php/XSS_(Cross_Site_Scripting)_Prevention_Cheat_Sheet#XSS_Prevention_Rules)
- 防止 CSRF (跨站点伪造请求攻击)
	- [CSRF Specific Defense](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)_Prevention_Cheat_Sheet#CSRF_Specific_Defense)
- 防止跨 iframe 攻击

---

### 构建工具

### Webpack

- css loader 与 style loader 的区别
- 减少 Webpack build 时间
- DllPlugin，HappyPack 的使用

> webpack 默认对代码的处理？

> DllPlugin 的工作原理？

> webpack 的性能可以怎么优化？

#### gulp 流与管道的概念

> Gulp 的工作原理

- Unix 流
- 管道
	- 管道是一个固定大小的缓冲区
	- 从管道读数据是一次性操作，数据一旦被读，它就从管道中被抛弃，释放空间以便写更多的数据
	- 可以把一个进程的标准输出流与另一个进程的标准输入流连接起来

> 构建系统如何选择？

> Webpack 和 Gulp 分别适用于什么样的项目？他们有什么区别？

---

### 网络知识部分

#### 同源策略

- 同源策略指的是：协议，域名，端口相同，同源策略是一种安全协议。指一段脚本只能读取来自同一来源的窗口和文档的属性

> 什么是同源？

#### 跨域处理 CORS (方法和区别)

- JSONP
- `document.domain`
- `window.name`
- HTML5 的 `window.postMessage` 和 `window.onmessage`

#### HTTP 基本知识

- [前端进阶--让你升级的网络知识](http://mp.weixin.qq.com/s?__biz=MjM5OTkwOTA5Mw==&mid=409908127&idx=1&sn=56a1110d6c22571c04ce13e889aeac87&scene=0#wechat_redirect)
- 三次握手
	- 客户端发起连接试探
	- 服务端接收到试探请求，向客户端发送确认消息
	- 客户端得到服务端的确认消息之后，再次向服务端发送确认消息
- 四次挥手
- 一次完整的 HTTP 请求是怎么样的
	- 域名解析
	- TCP 三次握手
	- 发起 http 请求
	- 服务器端响应 http 请求，客户端得到 html 代码
	- 浏览器解析 html 代码，并请求 html 代码中的资源
	- 浏览器对页面进行渲染呈现给用户
- Get 与 Post 的区别
	- [99%的人都理解错了 HTTP 中 GET 与 POST 的区别](http://mp.weixin.qq.com/s?__biz=MzI3NzIzMzg3Mw==&mid=100000054&idx=1&sn=71f6c214f3833d9ca20b9f7dcd9d33e4#rd&utm_source=tuicool&utm_medium=referral)
	
> cookie 工作机制是怎么样的？

> 如何在 header 中对浏览器的缓存进行设置？

> 重定向是如何工作的？

> 什么是长连接和短连接？

#### HTTPS

#### HTTP/2

> HTTP/2 有哪些特性？与 HTTP/1.1 的区别与联系？

#### WebSocket

> WebSocket 协议是什么？

> 如何通过原生的 WebSocket 来建立通信？

> WebSocket 通信的 Request Header 与 HTTP 有什么区别？

> WebSocket 的长连接和 HTTP/2 的长连接有什么区别？

---

### 框架相关知识

#### jQuery

- [jQuery Tips Everyone Should Know](https://github.com/Erichain/jquery-tips-everyone-should-know)
- 如何组织 jQuery 项目的代码结构
	- [Best Practice to Organize Javascript Library & CSS Folder Structure](http://stackoverflow.com/questions/24199004/best-practice-to-organize-javascript-library-css-folder-structure)

#### Vue

> 思考：

> 为什么要创建 Vue？

> Vue 的设计理念和其他框架有什么区别和联系？

> Vue 适用于什么样的项目？

> Vue 是否能够与其他框架或者库兼容？

> Vue 的性能怎么样？与其他框架对比呢？

> Vue 的基本原理，生命周期？

> Vuex 是怎么工作的？为什么要使用 Vuex？

> Vuex 与其他的状态管理工具的区别？

- `v-if`与`v-show`的区别
	- `v-show`控制节点的`display`属性，`v-if`为true的时候节点才会存在于DOM中
	- 频繁切换`v-show`较好，如果在运行时条件不大可能改变`v-if`较好
- Vue 如何为 input 的 onchange 事件添加延时
- `$emit`, `$broadcast`, `$dispatch` 的区别
	- 如何在两个同级的 component 之间通信
- Vuex

#### React

> 思考：

> 已经有那么多的前端框架了？为什么要设计 React？

> React 适用于什么样的项目？

> React 的性能如何？如何进行优化？

> React 的基本原理，生命周期？

> Redux 的设计理念？

> Redux 的原理？

> Redux 有什么替代品？

- Virtual DOM 如何实现？
- 生命周期
- 性能优化，如何减少不必要的更新
- 组件之间通信，数据流动
- `setState` 的用法，优点缺点
- `Container Component` 和 `Presentational Component`
- Redux 思想

> 多个框架之间如何选择？

> React，Vue，Angular 之间的对比和联系？

> Vue 的 DOM diff 与 React 的 Reconciler 有什么区别？

> 前端状态管理？

> MVC 与 MVVM 与 MVP？

---

### Practices

#### 浏览器的多个标签页之间如何通信

- [Javascript communication between browser tabs/windows](http://stackoverflow.com/questions/4079280/javascript-communication-between-browser-tabs-windows)

#### 数组降维

- [优雅的数组降维——Javascript中apply方法的妙用](http://mp.weixin.qq.com/s?__biz=MzAxODE2MjM1MA==&mid=402262046&idx=1&sn=bdcdcb93392c147a7b5449bd2d639a3b&scene=0#wechat_redirect)

#### 对象深度复制

``` javascript
function deepClone(resource) {
  if (Array.isArray(resource)) {
    let dest = [];
    let length = resource.length;
    while (length--) {
      console.log(length)
      dest[length] = deepClone(resource[length]) 
    }
    return dest
  } else if (typeof resource === 'object') {
    let dest = {} 
    for (let key in resource) {
      if (resource.hasOwnProperty(key)) {
        dest[key] = deepClone(resource[key]) 
      } 
    } 
    return dest
  }
  return resource
}
```

#### 排序

- 快速排序

``` javascript
function quickSort(list) {
  if (list.length < 2) {
    return list 
  }

  const base = list[0];
  const left = []
  const right = []

  for (let item of list.slice(1)) {
    if (item <= base) {
      left.push(item)
    } else {
      right.push(item) 
    } 
  }

  return quickSort(left).concat(base, quickSort(right))
}
```

- 冒泡排序

``` javascript
function bubbleSort(numSeries) {
  if (numSeries.length < 2) {
    return numSeries;
  }
  let len = numSeries.length;

  for (let i = 0; i < len - 1; i++) {
    for (let j = i; j < len - i - 1; j++) {
      if (numSeries[j] > numSeries[j + 1]) {
        [
          numSeries[j],
          numSeries[j + 1]
        ] = [
          numSeries[j + 1],
          numSeries[j]
        ];
      }
    }
  }

  return numSeries;
}
```

- 插入排序

``` javascript
function insertSort(list) {
  const result = list.slice();
  const len = list.length;
  let temp;

  for (let i = 1; i < len; i++) {
    let j;

    temp = result[i];
    j = i;

    while (j > 0 && arr[j - 1] > temp) {
      result[j] = result[j - 1];
      j--;
    }
    
    result[j] = temp;
  }
  
  return result;
}
```

#### 去除首尾空格

``` javascript
function removePlace(str) {
  const reg = /(^s*)|(s*)$/;

  if (str && typeof str === 'string') {
    return str.replace(reg, '');
  }
}
```

#### 使用 JavaScript 计算两个日期的时间差

- [JavaScript: DateDiff & DateMeasure: Calculate days, hours, minutes, seconds between two Dates](https://gist.github.com/remino/1563963)

#### 阶乘

``` javascript
// 普通递归方式
function factorial(n) {
  if (n === 1) {
    return 1;
  }
  return n * factorial(n - 1);
}

// 尾递归方式
function factorial(n, result) {
  if (n === 1) {
    return 1;
  }
  return factorial(n - 1, n * result);
}
```

#### Fibonacci 数列

``` javascript
// 普通递归方式
function fibonacci(n) {
  if (n <=1) {
    return 1;
  }
  return fibonacci(n - 1) + fibonacci(n - 2);
}

// 尾递归方式
function fibonacci1(n, ac = 1, ac2 = 1) {
  if (n <= 1) {
    return 1;
  }
  return fibonacci1(n - 1, ac2, ac + ac2);
}
```

#### 广度优先

#### 深度优先

#### 动态规划

#### 最短路径

#### 图

---

### 插件编写

> 关于某些插件编写，可参考：[jQuery插件库](http://www.jq22.com)

#### 焦点轮播图 Carousel

#### 网页弹出层 Modal

#### 多级菜单

#### Tab 切换

#### Lightbox

#### 模板引擎

#### 路由

#### 数据双向绑定

#### 拖动

---

### JavaScript 模块化

#### CommonJS

- 同步的方式加载模块，服务器优先
- 使用`require`加载模块，使用`module.exports`定义模块

#### AMD

- 浏览器优先的方式，通过异步加载的方式完成任务
- 使用`define(['module'], function ( module ) {})`加载模块
- 不兼容 io、文件系统（filesystem）和其它通过 CommonJS 实现的面向服务器的功能
- 推崇依赖前置
- 对于依赖的模块提前执行

---

### NodeJS

### HTML5

### WebSocket

### Canvas

### Functional Programming

### Design Patterns

> 各个设计模式的定义，适用场景，分别为了解决什么样的问题？

### Data Structure

## Contribution

如果对内容有什么好的建议以及有新的知识点, 欢迎提交 Pull Request.

## License

Release under the MIT License.
