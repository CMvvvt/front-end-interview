# front-end-interview —— 前端面试题

- [1.Javascript](#javascript)
  - [1 浅拷贝与深拷贝区别](#-1浅拷贝和深拷贝的区别)
  -

## JavaScript

数据类型、面向对象、继承、闭包、插件、作用域、跨域、原型链、模块化、自定义事件、内存泄漏、事件机制、异步装载回调、模板引擎、Nodejs、JSON、ajax 等。

### 1.浅拷贝和深拷贝的区别

---

### 2.defer 和 async 的区别(JS 延迟加载的方式)

[defer 和 async 的区别](https://segmentfault.com/q/1010000000640869)

defer 和 async、动态创建 DOM 方式（创建 script，插入到 DOM 中，加载完毕后 callBack）、按需异步载入 js

---

### 3.null 和 undefined 的区别？

undefined 是一个表示"无"的原始值，转为数值时为 当声明的变量还未被初始化时，变量的默认值为 null 用来表示尚未存在的对象，常用来表示函数企图返回一个不存在的对象。

（1）变量被声明了，但没有赋值时，就等于 undefined。

（2) 调用函数时，应该提供的参数没有提供，该参数等于 undefined。

（3）对象没有赋值的属性，该属性的值为 undefined。

（4）函数没有返回值时，默认返回 undefined。

（1） 作为函数的参数，表示该函数的参数不是对象。

（2） 作为对象原型链的终点。

new 操作符具体干了什么呢?
1、创建一个空对象，并且 this 变量引用该对象，同时还继承了该函数的原型。
2、属性和方法被加入到 this 引用的对象中。
3、新创建的对象由 this 所引用，并且最后隐式的返回 this 。

```key
var obj  = {};
obj.__proto__ = Base.prototype;
Base.call(obj);
```

---

### 4.如何解决跨域问题(跨域常考题)

[JS 中的跨域问题及解决办法汇总](https://blog.csdn.net/lareinalove/article/details/84107476)

---

## 计算机网络知识

计算机网络知识、http 协议等

### 1.请你谈谈 Cookie,你对 Cookie 的理解，以及与 seesionStorage,localStorage 的区别

- [彻底理解 Cookie](https://zhuanlan.zhihu.com/p/101612524)

- [cookie、sessionStorage 和 localStorage 的区别](https://blog.csdn.net/weixin_42614080/article/details/90706499?utm_medium=distribute.pc_relevant.none-task-blog-searchFromBaidu-1.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-searchFromBaidu-1.control)

**优点：极高的扩展性和可用性**

1.通过良好的编程，控制保存在 cookie 中的 session 对象的大小。

2.通过加密和安全传输技术（SSL），减少 cookie 被破解的可能性。

3.只在 cookie 中存放不敏感数据，即使被盗也不会有重大损失。

4.控制 cookie 的生命期，使之不会永远有效。偷盗者很可能拿到一
个过期的 cookie。

**缺点：**

1.Cookie 数量和长度的限制。每个 domain 最多只能有 20 条 cookie，每个 cookie 长度不能超过 4KB，否则会被截掉。

2.安全性问题。如果 cookie 被人拦截了，那人就可以取得所有的 session 信息。即使加密也与事无补，因为拦截者并不需要知道 cookie 的意义，他只要原样转发 cookie 就可以达到目的了。

3.有些状态不可能保存在客户端。例如，为了防止重复提交表单，我们需要在服务器端保存一个计数器。如果我们把这个计数器保存在客户端，那么它起不到任何作用。

- **webStorage**
  (作者：binnan
  链接：https://www.jianshu.com/p/26e1e9fa7089
  来源：简书)

使用 HTML5 可以在本地存储用户的浏览数据。早些时候,本地存储使用的是 cookie。但是 Web 存储需要更加的安全与快速，这些数据不会被保存在服务器上，但是这些数据只用于用户请求网站数据上。它也可以存储大量的数据，而不影响网站的性能。数据以 键/值 对存在, web 网页的数据只允许该网页访问使用。

Web Storage 的目的是为了克服由 cookie 带来的一些限制，当数据需要被严格控制在客户端上时，无须持续地将数据发回服务器。Web Storage 的两个主要目标是：

提供一种在 cookie 之外存储会话数据的途径。
提供一种存储大量可以跨会话存在的数据的机制。
Web Storage 又分为两种： sessionStorage 和 localStorage ，即这两个是 Storage 的一个实例。从字面意思就可以很清楚的看出来，sessionStorage 将数据保存在 session 中，浏览器关闭也就没了；而 localStorage 则一直将数据保存在客户端本地。其 API 提供的方法有以下几种：

    - setItem (key, value) ——  保存数据，以键值对的方式储存信息。

    - getItem (key) ——  获取数据，将键值传入，即可获取到对应的value值。

    - removeItem (key) ——  删除单个数据，根据键值移除对应的信息。

    - clear () ——  删除所有的数据

    - key (index) —— 获取某个索引的key

- **localStorage**

localStorage 的生命周期是永久性的。假若使用 localStorage 存储数据，即使关闭浏览器，也不会让数据消失，除非主动的去删除数据，使用的方法如上所示。localStorage 有 length 属性，可以查看其有多少条记录的数据。使用方法如下：

     var storage = null;
         if(window.localStorage){              //判断浏览器是否支持localStorage
            storage = window.localStorage;
            storage.setItem("name", "Rick");    //调用setItem方法，存储数据
            alert(storage.getItem("name"));     //调用getItem方法，弹框显示 name 为 Rick
            storage.removeItem("name");     //调用removeItem方法，移除数据
            alert(storage.getItem("name"));   //调用getItem方法，弹框显示 name 为 null

         }

localStorage 相对 sessionStorage 简单一点，需要注意的地方不是很多。

sessionStorage
sessionStorage 的生命周期是在浏览器关闭前。也就是说，在整个浏览器未关闭前，其数据一直都是存在的。sessionStorage 也有 length 属性，其基本的判断和使用方法和 localStorage 的使用是一致的。需要注意的有以下几点：

页面刷新不会消除数据;
只有在当前页面打开的链接，才可以访 sessionStorage 的数据；
使用 window.open 打开页面和改变 localtion.href 方式都可以获取到 sessionStorage 内部的数据;

---

### 2. 一个页面从输入 URL 到页面加载显示完成，这个过程中都发生了什么？

```
 1.查看缓存（浏览器缓存，系统缓存，路由器缓存），如果有直接访问

 2.如果没有，DNS服务器进行域名解析，解析成ip地址

 3.通过ip地址找到服务器，进行TCP链接，完成三次握手

 4.浏览器像服务器发送http请求

 5.服务器响应，将响应报文通过TCP发送回浏览器

 6.对响应进行解码，根据资源类型决定如何处理

 7.如果是HTML文档，则构建DOM树，下载CSS，JS资源，构建渲染树，布局，绘制
```

---

### 3.GET 与 POST 请求的区别

[GET POST 区别](https://blog.csdn.net/yipiankongbai/article/details/24025633?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromBaidu-1.control&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromBaidu-1.**control**)

---

## HTML&CSS

---

对 Web 标准的理解、浏览器内核差异、兼容性、hack、CSS 基本功：布局、盒子模型、选择器优先级及使用、HTML5、CSS3、移动端适应。

### 1. 介绍一下 CSS 的盒子模型？(box-sizing -content -padding -margin -border)

- content-box：标准盒模型，又叫做 W3C 盒模型，一般在现代浏览器中使用的都是这个盒模型
- border-box：怪异盒模型，低版本 IE 浏览器中的盒模型

- 区别

content-box：padding 和 border 不被包含在定义的 width 和 height 之内。
盒子的实际宽度=设置的 width+padding+border

border-box：padding 和 border 被包含在定义的 width 和 height 之内。
盒子的实际宽度=设置的 width（padding 和 border 不会影响实际宽度）

---

### 2. CSS 选择符有哪些？哪些属性可以继承？优先级算法如何计算？ CSS3 新增伪类有那些？

    *   1.id选择器（ # myid）
        2.类选择器（.myclassname）
        3.标签选择器（div, h1, p）
        4.相邻选择器（h1 + p）
        5.子选择器（ul > li）
        6.后代选择器（li a）
        7.通配符选择器（ * ）
        8.属性选择器（a[rel = "external"]）
        9.伪类选择器（a: hover, li:nth-child）

    *   可继承的样式： font-size font-family color, text-indent;

    *   不可继承的样式：border padding margin width height ;

    *   优先级就近原则，同权重情况下样式定义最近者为准;

    *   载入样式以最后载入的定位为准;

优先级为:

- !important > id > class > tag
- important 比 内联优先级高,但内联比 id 要高

CSS3 新增伪类举例：

p:first-of-type 选择属于其父元素的首个 `<p>` 元素的每个 `<p>` 元素。

p:last-of-type 选择属于其父元素的最后 `<p>` 元素的每个 `<p>` 元素。

p:only-of-type 选择属于其父元素唯一的 `<p>` 元素的每个 `<p>` 元素。

p:only-child 选择属于其父元素的唯一子元素的每个 `<p>` 元素。

p:nth-child(2) 选择属于其父元素的第二个子元素的每个 `<p>` 元素。

:enabled :disabled 控制表单控件的禁用状态。

:checked 单选框或复选框被选中。

---

### 3. CSS3 有哪些新特性？

CSS3 实现圆角（border-radius），阴影（box-shadow），

对文字加特效（text-shadow、），线性渐变（gradient），旋转（transform）

transform:rotate(9deg) scale(0.85,0.90) translate(0px,-30px) skew(-9deg,0deg);//旋转,缩放,定位,倾斜

增加了更多的 CSS 选择器 多背景 rgba

在 CSS3 中唯一引入的伪元素是::selection.

媒体查询，多栏布局

border-image
