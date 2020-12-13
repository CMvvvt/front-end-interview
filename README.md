# front-end-interview —— 前端面试题

## JavaScript

数据类型、面向对象、继承、闭包、插件、作用域、跨域、原型链、模块化、自定义事件、内存泄漏、事件机制、异步装载回调、模板引擎、Nodejs、JSON、ajax 等。

### 1.浅拷贝和深拷贝的区别

---

---

## 计算机网络知识

计算机网络知识、http 协议等

### 1.请你谈谈 Cookie,你对 Cookie 的理解，以及与 seesionStorage,localStorage 的区别

---

[彻底理解 Cookie](https://zhuanlan.zhihu.com/p/101612524)

[cookie、sessionStorage 和 localStorage 的区别](https://blog.csdn.net/weixin_42614080/article/details/90706499?utm_medium=distribute.pc_relevant.none-task-blog-searchFromBaidu-1.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-searchFromBaidu-1.control)

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

**webStorage**
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

**localStorage**
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

## HTML&CSS

对 Web 标准的理解、浏览器内核差异、兼容性、hack、CSS 基本功：布局、盒子模型、选择器优先级及使用、HTML5、CSS3、移动端适应。
