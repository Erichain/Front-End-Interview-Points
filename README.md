# Front-End-Interview-Points
个人总结的比较全面的前端面试知识点。持续更新中...

涵盖了以下各个方面的知识:

- HTML, CSS, JS基础知识
- 网站性能优化知识
- 前端项目自动化构建相关知识
- 算法相关知识
- 网络与HTTP协议相关知识
- 前端的安全相关知识
- 插件编写相关知识
- JS模块化编程相关知识

> 欢迎fork和star. 如果对内容什么问题, 请新建issue.

## 目录

- [关于前端是什么，以及需要学习什么，移步这里](#关于前端是什么，以及需要学习什么，移步这里)
- [HTML 部分](#HTML部分)
- [CSS 部分](#CSS部分)
- [JS 部分](#JS部分)
- [浏览器部分](#浏览器部分)
- [前端安全](#前端安全)
- [构建系统](#自动化)
- [网络知识部分](#网络知识部分)
- [框架相关知识](#框架相关知识)
- [算法](#算法)
- [插件编写](#插件编写)
- [Javascript模块化](#Javascript模块化)
- [Javascript设计模式](#Javascript设计模式)
- [ES 2015](#ES 2015)
- [NodeJS](#NodeJS)
- [HTML5](#HTML5)
- [CSS3](#CSS3)
- [Websocket](#Websocket)
- [Canvas](#Canvas)
- [Angular2](#Angular2)
- [React && React Native](#React && React Native)
- [Functional Programming](#Functional Programming)

---

#### 关于前端是什么，以及需要学习什么，移步这里：

#### [Front-End Developer Handbook](http://www.frontendhandbook.com)

---

### HTML部分

#### docType

- 混杂模式
	- 触发条件：不加文档类型声明
- 标准模式
	- 触发条件：
		- `<!DOCTYPE html>`
		- `<!-- HTML 4.01 严格型 -->
<!DOCTYPE HTML PUBLIC"-//W3C//DTD HTML4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">`
		- `<!-- XHTML 1.0 严格型 -->
<!DOCTYPE htmlPUBLIC "-//W3C//DTD XHTML 1.0Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">`
- 准标准模式
	- 触发条件：
		- `<!-- HTML 4.01 过渡型 -->
<!DOCTYPE HTMLPUBLIC "-//W3C//DTD HTML 4.01Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">`
		- `<!-- HTML 4.01 框架集型 -->
<!DOCTYPE HTMLPUBLIC "-//W3C//DTD HTML 4.01Frameset//EN" "http://www.w3.org/TR/html4/frameset.dtd">`
		- `<!-- XHTML 1.0 过渡型 -->
<!DOCTYPE htmlPUBLIC "-//W3C//DTD XHTML 1.0Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">`
		- `<!-- XHTML 1.0 框架集型 -->
<!DOCTYPE htmlPUBLIC "-//W3C//DTD XHTML 1.0Frameset//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd">`

#### 标签语义化

- 去掉或者丢失样式的时候能够让页面呈现出清晰的结构
- 有利于SEO：和搜索引擎建立良好沟通，有助于爬虫抓取更多的有效信息：爬虫依赖于标签来确定上下文和各个关键字的权重
- 方便其他设备解析（如屏幕阅读器、盲人阅读器、移动设备）以意义的方式来渲染网页
- 便于团队开发和维护，语义化更具可读性，是下一步网页的重要动向，遵循W3C标准的团队都遵循这个标准，可以减少差异化

#### 块级标签，行内标签

- 块级：div, ul, li, ol, table, th, tbody, tfoot, tr, pre, fieldset, form, h1-6, p等
- a, abbr, b, br, code, em, img, input, label, select, textarea, strong等

#### 替换元素和非替换元素

- 替换元素
	- `img, object, iframe, video` 等。即元素本身没有实际内容，通过元素的标签和属性来显示内容
- 非替换元素
	- 大多数标签属于非替换元素，这部分标签把标签里的内容直接告诉浏览器显示出来

#### meta标签

- 如何在不使用JS的情况下刷新页面(http-equiv="refresh", content="time")
- 设置页面缓存
- 移动端设置
- etc.

#### HTML代码优化

- 标签嵌套层级不要太深，标签尽量简洁化.如懒加载后将data属性去除
- 大量图片的懒加载策略，以及一些元素利用ajax在onload后实行延迟加载
- 对一些js的异步加载

#### 搜索引擎优化SEO

---

### CSS部分

#### 浮动，清除浮动的方法和原理(4种方法)

- 使用空标签设置`clear: both;`
- 为父级元素设置`overflow: hidden;`(利用BFC的原理)
- 使用伪元素，为要清除浮动的元素添加`.clearfix`类(推荐)
- 使用`min-height: contain-floats;`(不推荐，兼容性不好)

#### CSS块级格式化上下文

- 触发条件
	- `position`属性不为`static`或者`relative`
	- `float`属性不为none
	- 非块级的块级元素(inline-block, table-cell)
	- `overflow`不为`visible`
- 特性
	- 内部的Box会在垂直方向，从顶部开始一个接一个地放置
	- Box垂直方向的距离由margin决定。属于同一个BFC的两个相邻Box的margin会发生叠加
	- BFC的区域不会与float box叠加
	- BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素，反之亦然
	- 计算BFC的高度时，浮动元素也参与计算
- 用处
	- 解决margin边距叠加问题。为元素单独创建一个BFC来防止外边距的折叠
	- 布局
	- 清除浮动。为包含浮动元素的container创建BFC来清除浮动

#### 盒子模型(IE盒子模型的区别)

- 总宽度 ＝  margin＋padding＋border＋content，IE的盒子模型的宽度不计padding和border
- css3的`box-sizing`属性，详见https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing
	- content-box，border和padding不计算入width之内
	- border-box，border和padding计算入width之内

#### 定位

- 定位和浮动的区别
- 什么时候使用定位，什么时候使用浮动

#### 样式继承

- 可继承的样式
	- `font-size` `font-family` `color` `text-indent`

#### z-index属性

- [理解 CSS 的 z-index 属性](https://segmentfault.com/a/1190000000460664)


#### CSS sprite

- 减少请求

#### 布局模型

- 双飞翼布局
- 圣杯布局
- 两列布局
- 三列布局
- 弹性布局
- 流式布局
- 瀑布流布局
- 多列布局等高

#### CSS优先级

- 行内样式 > 内联样式 > 外部样式，ID > Class > Element
- 设置了`!important`的样式优先级更高

#### Flexbox

- [A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

#### 各个单位的区别(px, em, rem, 百分比, vw, vh, vmax, vmin)

- [Understanding Font sizing in CSS: em – px – pt – percent – rem](https://www.narga.net/understanding-font-sizing-in-css-em-px-pt-percent-rem/)
- [REM vs EM – The Great Debate](http://zellwk.com/blog/rem-vs-em/?utm_source=CSS-Weekly&utm_campaign=Issue-204&utm_medium=email)

#### 居中

- [CSS Center Complete](https://github.com/Erichain/css-center-complete)

#### link和@import的区别

- link属于XHTML标签，而@import是CSS提供的
- 页面被加载的时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载
- @import只在IE5以上才能识别，而link是XHTML标签，无兼容问题
- link方式的样式的权重 高于@import的权重

#### 如何将div与图片设置等宽，inline-block元素之间的空隙如何解决

- 设置父元素`font-size`为0，再对里面的文字单独设置`font-size`
- 全兼容的样式解决方法

``` css
.finally-solve {
    letter-spacing: -4px; /*根据不同字体字号或许需要做一定的调整*/
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

#### CSS优化

-  嵌套层级不要太深，一般三层最多
-  css解析从右向左，所以最右边的应该是相对少一点
-  html用了base64的img的话，并不会缓存起来，可以将这个base64的图片放在css文件里，css会缓存，图片就缓存起来了
-  尽量不用后代元素选择器，最右边的一层不要是标签，尤其是像div这种非常常用的标签
-  多使用css的继承，而不是每一次都书写时都全部重写一遍。写多个css属性时，能连在一起写的就连在一起写

#### 预处理器

- Sass
	- Ruby Sass 与 Lib Sass 的区别
- Less
- Stylus
- PostCSS

#### CSS 规范，模块化

- OOCSS
- BEM
- SMACSS

[An Overview Of OOCSS BEM SMACSS](http://codetheory.in/an-overview-of-oocss-bem-smacss/)

---

### JS部分

#### 严格模式

- `'use strict'`
- 不能使用`eval()`
- 抑制`this`的行为
- 不允许读写`eval`和`arguments`的值
- 不允许意外创建全局变量

#### 变量

- 使用var定义的全局变量不能使用delete删除
- 无var创建的全局变量可以使用delete删除
- 隐式类型转换
	- 数字与字符串相加，结果为字符串
	- 数字与字符串相减，结果为数字
	- 比较变量的是否相同时，要采用`===`，`==`会发生隐式类型转换
	- NaN与任何变量不相等

#### 类型检测

- `typeof`
- `instanceof`
- `constructor`
- `Object.prototype.toString.apply()`

#### 作用域

- 全局作用域
- 函数作用域

#### 对象

- `hasOwnProperty, isPrototypeOf, propertyIsEnumerable`
- 配置属性(`configurable, enumerable, writable, value`)
- 特性
	- 扩展: `isExtensible`, `preventExtensions`(是否可以添加新的属性)
	- 密封:  `isSealed`, `seal`(是否可以删除属性，是否可以配置属性)
	- 冻结:  `isFrozen`, `freeze`(所有属性是否可读可写)
- 定义属性
	- `defineProperty`, `defineProperties`

#### 数组

- 数组的类型检测
- 数组的方法
	- `slice()`
	- `map()`
	- `every()`
	- `some()`
	- `filter()`

#### 函数

- 柯里化
	- 概念：部分求值（Partial Evaluation），是把接受多个参数的函数变换成接受一个单一参数（最初函数的第一个参数）的函数，并且返回接受余下的参数而且返回结果的新函数的技术

``` javascript
function currying( fn ) {
    var args = Array.prototype.slice.call(arguments, 1);
    return function () {
        var newArgs = args.concat(Array.prototype.slice.call(arguments));
        return fn.apply(null, newArgs);
    }
}
```
 
- arguments对象
- JS函数不存在重载，后定义的函数会覆盖先定义的函数
- 函数调用模式
	- 方法调用
	- 函数调用
	- 构造器调用
	- apply调用

#### `new`操作符的原理

使用`new`关键字来创建实例的时候，原理如下：

- 首先，在构造函数内部使用`Object.create(constructor.prototype)`创建一个对象继承自构造函数
- 然后，将这个对象引用到`this`上
- 最后，返回`this`

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
- 经典例子：列表点击，弹出每一个的index

``` javascript
/* 错误做法 */
var elems = document.getElementById('links').getElementsByTagName('li');

for ( var i = 0; i < elems.length; i++ ) {
	elems[i].addEventListener('click', function ( event ) {
        event.preventDefault();
        alert(i);
    }, false);
}
```

``` javascript
/* 正确的做法，使用闭包 */
var elems = document.getElementById('links').getElementsByTagName('li');

for ( var i = 0; i < elems.length; i++ ) {
	(function ( index ) {
    	elems[i].addEventListener('click', function ( event ) {
        	event.preventDefault();
            alert(index);
        }, false);
    
    })( i );
}
```

#### this

- 函数的`this`的值永远绑定在调用此函数的对象上
- 可以使用`apply`，`call`或者`bind`改变`this`值的指向

#### 对象创建的模式和方法及区别

- 工厂模式

``` javascript
/* 缺点：无法检测对象的类型 */
var createPerson = function ( name, age, job ) {
	var o = new Object();
	o.name = name;
	o.age = age;
	o.job = job;

	return o;
};

var person1 = createPerson('Erichain', 21, 'Web');
```

- 构造函数模式

``` javascript
/* 缺点：每个方法要在每个实例上重新创建一遍 */
var Person = function ( name, age, job ) {
	this.name = name;
	this.age = age;
	this.job = job;
}

var person1 = new Person('Erichain', 21, 'Web');
```

- 原型模式

``` javascript
var Person = function () {};

Person.prototype = {
	constructor: Person, // 如果这个属性十分重要的话
	name: 'Erichain',
	age: 21,
	job: 'web'
};
var person1 = new Person();
```

- 组合构造函数原型模式
- 动态原型模式

``` javascript
var Person = function ( name, age, job ) {
	this.name = name;
	this.age = age;
	this.job = job;

	if ( typeof this.sayName !== 'function' ) {
		Person.prototype.sayName = function () {
			alert( this.name );
		}
	}
};
```

- 寄生构造函数模式
	- 除了使用`new`来实例化外，与工厂模式没区别
	- 不能依赖`instanceof`来确定对象类型，一般不建议使用
- 稳妥构造函数模式

#### 原型和继承

- 原型链
- 借用构造函数

``` javascript
function Person( name ) {
	this.name = name;
}

function man() {
	// 继承自Person，可以选择是否传入参数
	Person.call(this, 'Erichain');
}
```

- 组合继承
- 原型式继承
- 寄生式继承
- 寄生组合式继承
- `new Object()`和`Object.create()`的区别
	- `Object.create`创建的对象直接从他的第一个参数继承，而`new Object`所创建的对象是从对象的原型上继承
	- 使用`Object.create`，可以创建一个不继承于任何东西的对象，但是，如果设置`someConstructor.prototype = null`，那么，这个新创建的对象会继承自`Object.prototype`

#### 回调函数

#### 变量提升，函数声明提升

- 函数声明优于变量声明
- 函数声明会覆盖变量声明，但是不会覆盖变量赋值

#### IIFE(立即执行函数)

- 在闭包中保存变量状态
- 模块化
- IIFE和自执行函数的区别
- IIFE的几种表示方法

``` javascript
(function () {})();
(function () {}());

!function () { /* code */ } ();
~function () { /* code */ } ();
-function () { /* code */ } ();
+function () { /* code */ } ();
```

#### 事件

- 事件流
	- 事件捕获
	- 处于目标
	- 事件冒泡
- 事件对象(IE的区别)
- 跨浏览器事件处理函数

``` javascript
var EventUtil = {
    getEvent: function ( event ) {
        return event ? event : window.event;
    },
    getTarget: function ( event ) {
        return event.target || event.srcElement;
    },
    addHandler: function ( elem, type, handler ) {
        if ( elem.addEventListener ) {
            elem.addEventListener(type, handler, false);
        }
        else if ( elem.attachEvent ) {
            elem.attachEvent('on' + type, handler);
        }
        else {
            elem['on' + type] = handler;
        }
    },
    preventDefault: function ( event ) {
        if ( event.preventDefault ) {
            event.preventDefault();
        }
        else {
            event.returnValue = false;
        }
    },
    stopPropagation: function ( event ) {
        if ( event.stopPropagation ) {
            event.stopPropagation();
        }
        else {
            event.cancelable = true;
        }
    }
};
```

- 事件广播
- 事件委托

```vbscript-html
<ul id="links">
    <li id="link1">Link1</li>
    <li id="link2">Link2</li>
    <li id="link3">Link3</li>
</ul>
```

``` javascript
var links = document.getElementById('links');

// 使用之前定义的跨浏览器事件处理程序
EventUtil.addHandler(links, 'click', function ( event ) {
    var target = EventUtil.getTarget(event);
    event = EventUtil.getEvent(event);

    switch ( target.id ) {
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

- 事件函数的参数(注意`addEventListener()`的最后一个参数，如果为false表示在冒泡阶段获取事件，如果为true，表示在事件捕获阶段获取事件)

#### call, apply, bind(手动实现)

- `call(obj, args)`, `apply(obj, array)`
- `call`与`apply`支持低版本浏览器，`bind`只支持高版本浏览器
- `bind`原生代码实现

``` javascript
if ( !Function.prototype.bind ) {
    Function.prototype.bind = function ( oThis ) {
        if ( typeof this !== 'function') {
            throw new Error('What is trying to be bound is not callable');
        }

        var aArgs = Array.prototype.slice.call(arguments, 1),
            fToBound = this,
            fNOP = function () {},
            fBound = function () {
                return fToBound.apply(
                    this instanceof fNOP ? this : oThis,
                    aArgs.concat(Array.prototype.slice.call(arguments))
                )
            };

        if ( this.prototype ) {
            fNOP.prototype = this.prototype;
        }

        fBound.prototype = new fNOP();
        return fBound;
    };
}
```

#### 能力检测

#### BOM

- `window`对象
- `location`对象
- `screen`对象
- `navigator`对象
	- 检测插件`navigator.plugins`
	- 检测用户代理`navigator.userAgent`
- `history`对象

#### promise

- [Javascript Promise 迷你书](http://liubin.org/promises-book/)
- [JavaScript Promise API](http://mp.weixin.qq.com/s?__biz=MzAxODE2MjM1MA==&mid=402552108&idx=1&sn=b0d4d986984a45276c6bbbf386c04790&scene=0#wechat_redirect)

#### DOM 操作

- 查找
	- document.getElementById
	- document.getElementsByTagName
	- document.getElementsByName
	- document.getElementsByClassName
	- document.querySelector
	- document.querySelectAll
- 节点关系
	- element.childNodes
	- element.firstChild
	- element.lastChild
	- element.previousSibling
	- element.nextSibling
	- element.parentNode
	- element.appendChild()
	- element.insertBefore()
	- element.removeChild()
	- element.replaceChild()
- 属性操作
	- element.getAttribute()
	- element.setAttribute()
- 样式操作
	- element.style[PROPERTY_NAME]
	- element.classList
	- element.classList.add
	- element.classList.remove
	- element.classList.contains
	- element.classList.toggle
- 元素遍历
	- `childElementCount`子元素数量
	- `firstElementChild`第一个子元素: `firstChild`的元素版
	- `lastElementChild`最后一个子元素: `lastChild`的元素版
	- `previousElementSibling`->`previousSibling`的元素版
	- `nextElementSibling`->`nextSibling`的元素版
	- 遍历方法
		- `document.createNodeIterator(root, whatToShow, filter)`参见https://developer.mozilla.org/en-US/docs/Web/API/NodeIterator
		- `document.createTreeWalker(root, whatToShow, filter, expandEntityReferences, currentNode)`参见https://developer.mozilla.org/en-US/docs/Web/API/TreeWalker

#### 性能优化

- 操作DOM的时候一定要缓存变量，避免发生大量的重排重绘
- 异步加载Javascript文件
	- 使用`document.write()`
	- 动态改变已有script标签的`src`属性
	- 使用DOM方法动态创建script元素
	- 使用Ajax获取脚本内容再加载
	- 在script标签中使用`defer`以及`async`属性
	- 按需加载
- 合并文件
- 合理使用二进制
- CDN加速，原理
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

#### 垃圾回收

- 引用计数

``` javascript
/* 出现循环引用的例子 */
function () {
	var objectA = {},
		objectB = {};

	objectA.someOtherObject = objectB;
	objectB.anotherObject = objectA;
}
```

- 标记清除

#### 内存泄漏

- setTimeout 的第一个参数使用字符串而非函数的话，会引发内存泄漏
- 循环引用

#### 优雅降级和渐进增强

- 优雅降级：Web站点在所有新式浏览器中都能正常工作，如果用户使用的是老式浏览器，则代码会检查以确认它们是否能正常工作。由于IE独特的盒模型布局问题，针对不同版本的IE的hack实践过优雅降级了,为那些无法支持功能的浏览器增加候选方案，使之在旧式浏览器上以某种形式降级体验却不至于完全失效
- 渐进增强：从被所有浏览器支持的基本功能开始，逐步地添加那些只有新式浏览器才支持的功能,向页面增加无害于基础浏览器的额外样式和功能的。当浏览器支持时，它们会自动地呈现出来并发挥作用

####  JSON

- `JSON.stringify()` json序列化为字符串
- `JSON.parse()` 将类JSON的字符串转化为JSON对象

#### XMLHttpRequest对象

- 一段比较完整的使用原生Javascript实现ajax请求方法

``` javascript
function createRequestObject() {
    if ( window.XMLHttpRequest ) {
        return new XMLHttpRequest();
    }

    // 针对IE
    else if ( window.ActiveXObject ) {
        return new ActiveXObject('Microsoft.XMLHTTP');
    }
}

// 请求的回调函数
function requestCallBack() {
    if ( request.readyState === 4 && request.status === 200 ) {
        console.log(request.responseText);
    }
}

var request = createRequestObject();

request.onreadystatechange = requestCallBack;
// open函数的三个参数分别是请求的方法, 请求的地址, 是否异步(true表示异步)
request.open('POST', url, true);
request.send(null);
```

#### 使用Javascript计算两个日期的时间差

- [JavaScript: DateDiff & DateMeasure: Calculate days, hours, minutes, seconds between two Dates](https://gist.github.com/remino/1563963)

#### 性能测试工具

- [Performance Tools](https://css-tricks.com/performance-tools/)

#### 代码审查工具

- JSHint
- JSLint
- ESLint(针对ECMAScript 2015)

#### 代码压缩

- JSMin
- YUI Compressor
- Gzip

#### Javascript原生函数使用

- [You-Dont-Need-jQuery](https://github.com/Erichain/You-Dont-Need-jQuery)

#### `Array.prototype.slice.call()`原理

- [how does Array.prototype.slice.call() work?](http://stackoverflow.com/questions/7056925/how-does-array-prototype-slice-call-work)

#### RESTful

---

### 浏览器部分

#### 浏览器针对页面的渲染过程

- [How browsers work](http://taligarsiel.com/Projects/howbrowserswork1.htm#Introduction)

#### 各个浏览器内核

- IE: Trident
- Chrome: Webkit, Blink(now)
- Firefox: Gecko
- Opera: Presto

#### sessionStorage，cookie，localStorage

- cookie 由服务器生成，可设置失效时间。如果是浏览器端生成的cookie，则在浏览器关闭之后失效；而localStorage除非被清除，否则永久保存，sessionStorage则在关闭浏览器或者页面之后清除
- cookie的大小为4k左右，localStorage和sessionStorage的大小一般为5MB
- 与服务器痛心的时候，cookie每次都会携带在http头中，但是其他两个不参与服务器通信
- cookie中最好不要放置任何的明文的东西，其他两个的数据如果提交到服务器一定要校验

#### 浏览器的多个标签页之间如何通信

- [Javascript communication between browser tabs/windows](http://stackoverflow.com/questions/4079280/javascript-communication-between-browser-tabs-windows)

#### 关于浏览器缓存

- [浅谈Web缓存](http://www.alloyteam.com/2016/03/discussion-on-web-caching/)

---

### 前端安全

- 防止XSS(跨站点脚本)攻击
- 防止CSRF(跨站点伪造请求攻击)
- 防止跨iframe攻击

---

### 构建系统

### webpack

- css loader 与 style loader 的区别

### Rollup

#### npm与bower的区别

- [bower与npm的不同点](https://github.com/Erichain/Front-End-Note/blob/master/前端自动化/diffBetweenBower%26Npm.md)

#### gulp流与管道的概念

- Unix流
- 管道
	- 管道是一个固定大小的缓冲区
	- 从管道读数据是一次性操作，数据一旦被读，它就从管道中被抛弃，释放空间以便写更多的数据
	- 可以把一个进程的标准输出流与另一个进程的标准输入流连接起来

#### 打包后静态资源路径的修改

#### gulp和grunt的区别

- [前端工程的构建工具对比 Gulp vs Grunt](https://segmentfault.com/a/1190000002491282)

#### 测试工具

- Mocha
- Karma
- Jasmine
- Jest

---

### 网络知识部分

#### Ajax

#### 同源策略

- 同源策略指的是：协议，域名，端口相同，同源策略是一种安全协议。 指一段脚本只能读取来自同一来源的窗口和文档的属性

#### 跨域处理(方法和区别)

- JSONP
- `document.domain`
- `window.name`
- HTML5的`window.postMessage`和`window.onmessage`

#### HTTP基本知识

- [前端进阶--让你升级的网络知识](http://mp.weixin.qq.com/s?__biz=MjM5OTkwOTA5Mw==&mid=409908127&idx=1&sn=56a1110d6c22571c04ce13e889aeac87&scene=0#wechat_redirect)
- 三次握手
	- 客户端发起连接试探
	- 服务端接收到试探请求，向客户端发送确认消息
	- 客户端得到服务端的确认消息之后，再次向服务端发送确认消息
- 一次完整的http请求是怎么样的
	- 域名解析
	- TCP三次握手
	- 发起http请求
	- 服务器端响应http请求，客户端得到html代码
	- 浏览器解析html代码，并请求html代码中的资源
	- 浏览器对页面进行渲染呈现给用户
- Get 与 Post 的区别
	- [99%的人都理解错了HTTP中GET与POST的区别](http://mp.weixin.qq.com/s?__biz=MzI3NzIzMzg3Mw==&mid=100000054&idx=1&sn=71f6c214f3833d9ca20b9f7dcd9d33e4#rd&utm_source=tuicool&utm_medium=referral)

---

### 框架相关知识

#### jQuery

- [jQuery Tips Everyone Should Know](https://github.com/Erichain/jquery-tips-everyone-should-know)
- 如何组织jQuery项目的代码结构
	- [Best Practice to Organize Javascript Library & CSS Folder Structure](http://stackoverflow.com/questions/24199004/best-practice-to-organize-javascript-library-css-folder-structure)

#### Bootstrap，插件原理

- 栅格布局实现原理
- `.img-responsive`实现原理
- 内联表单实现原理
- Bootstrap组件实现原理

#### AngularJS 1.x

- 双向绑定
	- `$digest`循环
	- dirty checking
	- `$watch`
- MVC
- 独立作用域
- 依赖注入
- 循环监听
- 同级控制器之间如何通信
	- 使用`$rootScope`发送和接收
- `ng-if`与`ng-hide/show`的区别
	- `ng-if`为`true`的时候节点才会存在于DOM中
	- `ng-show/hide`只是控制节点的显示和隐藏，设置`display`属性
- `factory`，`service`与`provider`的区别和关系
	- 使用`factory`创建的服务，是一个对象，然后，将方法和属性定义在这个对象上，在返回这个对象，就可以供外部controller调用了
	- 使用`service`创建的服务，是使用`new`进行实例化的，所以，方法和属性要定义在`this`上，并且这个服务会自动返回`this`
	- 使用`provider`创建的服务，是唯一可以注入到`config()`函数的服务，可以用来提供模块化的配置。并且，定义在`this`上的属性和方法，在`config`函数里才可以访问，从`this.$get()`函数里返回的属性和方法，才能被控制器所访问
- `ng-click`是否可以使用原生函数
	- 不可以，因为对应的方法不存在于其控制器中，除非在控制器中声明
- `ng-repeat`数组中有相同元素的解决办法
	- 可以添加`track by $index`
- `$emit`，`$broadcast`和`$on`
	- `$emit`由子级向父级广播，`$broadcast`由父级向子级广播
- `controllerAs`与`$scope`的区别
- AngularJS的缺点
	- 强约束，学习成本高
	- 不利于SEO
	- 性能问题
		- 减少监控项
		- 主动设置索引
		- 降低渲染的数据数量
		- 数据扁平化

### Vue

- `v-if`与`v-show`的区别
	- `v-show`控制节点的`display`属性，`v-if`为true的时候节点才会存在于DOM中
	- 频繁切换`v-show`较好，如果在运行时条件不大可能改变`v-if`较好
- Vue 如何为 input 的 onchange 事件添加延时
- `$emit`, `$broadcast`, `$dispatch` 的区别
	- 如何在两个同级的 component 之间通信
- Vuex
- 源码阅读

---

### 算法

#### 数组降维

- [优雅的数组降维——Javascript中apply方法的妙用](http://mp.weixin.qq.com/s?__biz=MzAxODE2MjM1MA==&mid=402262046&idx=1&sn=bdcdcb93392c147a7b5449bd2d639a3b&scene=0#wechat_redirect)

#### 数组去重

- 最简单的方法

``` javascript
function removeDuplicate( arr ) {
    var len = arr.length,
        temp = [];

    for ( var i = 0; i < len; i+=1 ) {
        if ( temp.indexOf(arr[i]) === -1 ) {
            temp.push(arr[i]);
        }
    }
    return temp;
}
```

#### 对象深度复制

``` javascript
function clone( Obj ) {   
        var buf;   
        if ( Obj instanceof Array ) {   
            buf = [];  //创建一个空的数组 
            var i = Obj.length;   
            while ( i-- ) {   
                buf[i] = clone(Obj[i]);   
            }   
            return buf;   
        }
        else if ( Obj instanceof Object ) {   
            buf = {};  //创建一个空对象 
            for ( var k in Obj ) {  //为这个对象添加新的属性 
                buf[k] = clone(Obj[k]);   
            }   
            return buf;   
        }
        else {   
            return Obj;   
        }   
    }  
```

#### 各个类型的复制

``` javascript
function clone( obj ) {
	var dest;
	
	switch( typeof obj ) {
		case 'undefined':
			break;
			
		case 'number':
			dest = +obj;
			break;
			
		case 'string':
			dest = obj + '';
			break;
			
		case 'boolean':
			dest = obj;
			break;
		
		case 'object':
			if ( obj instanceof Array ) {
				dest = [];

				for ( var i = 0; i < obj.length; i++ ) {
					dest[i] = obj[i];
				}
			}
			else {
				dest = {};
				for ( var i in obj ) {
					dest[i] = obj[i];
				}
			}
		
		default:
			break;
	}

	return dest;
}
```

#### 排序

- 快速排序

``` javascript
function quickSort( arr ) {
    var left = [],
        right = [],
        len = arr.length,
        breakPoint = arr[0];

    if ( len === 1 || len === 0 ) {
        return arr;
    }

    for ( var i = 1; i < len; i++ ) {
        if ( arr[i] < breakPoint ) {
            left.push(arr[i]);
        }
        else {
            right.push(arr[i]);
        }
    }

    return quickSort(left).concat(breakPoint, quickSort(right));
}
```

- 冒泡排序

``` javascript
function bubbleSort( arr ) {
    var len = arr.length,
        temp;

    for ( var i = 0; i < len - 1; i ++ ) {
        for ( var j = 0; j < len - 1 - i; j++ ) {
            if ( arr[j] > arr[j+1] ) {
                temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
    }

    return arr;
}
```

- 插入排序

``` javascript
function insertSort( arr ) {
    var len = arr.length,
        temp;

    for ( var i = 1; i < len; i++ ) {
        var j;
        temp = arr[i];
        j = i;

        while ( j > 0 && arr[j-1] > temp ) {
            arr[j] = arr[j-1];
            j--;
        }
        arr[j] = temp;
    }
    return arr;
}
```

#### 去除首尾空格

``` javascript
function removePlace( str ) {
	var reg = /(^s*)|(s*)$/;

	if ( str && typeof str === 'string' ) {
		return str.replace(reg, '');
	}
}
```

#### 统计字符数量

``` javascript
function charCount( str ) {
	var obj = {},
		len = str.length,
		i = 0;

	for ( ; i < len; i++ ) {
		var val = str.charAt(i);

		if ( obj[val] && obj[val].value === val ) {
			obj[val].count++;
		}
		else {
			obj[val] = {};
			obj[val].count = 1;
			obj[val].value = val;
		}
	}

	for ( var key in obj ) {
		console.log( key + ' is ' + obj[key].count );
	}

	return obj;
}
```

---

### 插件编写

> 关于插件编写，可参考：[jQuery插件库](http://www.jq22.com)

#### 焦点轮播图

#### 弹窗效果

#### 多级菜单

#### tab切换

#### Lightbox

---

### Javascript模块化

#### CommonJS

- 同步的方式加载模块，服务器优先
- 使用`require`加载模块，使用`module.exports`定义模块

#### AMD

- 浏览器优先的方式，通过异步加载的方式完成任务
- 使用`define(['module'], function ( module ) {})`加载模块
- 不兼容 io、文件系统（filesystem）和其它通过 CommonJS 实现的面向服务器的功能
- 推崇依赖前置
- 对于依赖的模块提前执行

#### CMD

- 推崇依赖就近
- 对于依赖的模块延迟执行
- 使用`define(function ( require, exports, module ) {})`加载模块

#### UMD(通用模块定义，Universal Module Definition)

- 同时支持 AMD 和 CommonJS 特性

---

### Javascript设计模式

- [Learning JavaScript Design Patterns](https://addyosmani.com/resources/essentialjsdesignpatterns/book/)

---

### ES 2015

- 数组去重
	- `[...new Set(arr)]`
- 结构赋值
- Symbol
- Set && Map
- Arrow Function
- Proxy
- Promise
- Async && Await
- Generator Function

### NodeJS

### HTML5

### CSS3

### Websocket

### Canvas

### Angular2

### React && React Native

### Functional Programming

### Git

## Contribution

如果对内容有什么好的建议以及有新的知识点, 欢迎提交Pull Request.

## License

Release under the MIT License.
