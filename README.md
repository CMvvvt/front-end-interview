# front-end-interview —— 前端面试题

- [1.Javascript/ES6](#javascript)
  - [1.1 浅拷贝与深拷贝区别](#-1浅拷贝和深拷贝的区别)
  - [1.2 defer 和 async 区别](#2defer-和-async-的区别js-延迟加载的方式)
  - [1.3 null 和 undefined 的区别](#3null-和-undefined-的区别)
  - [1.4 事件循环解释一下](#4事件循环)
  - [1.5 JS 数据类型](#5-js数据类型)
  - [1.6 内存回收机制](#6-js内存回收机制)
  - [1.7 Set Map](#7-setmap--weaksetweakmap)
  - [1.8 web 性能优化](#8-web-性能优化)
  - [1.9 介绍一下 Promise](#9-promise)
  - [1.10 export default 和 export 的区别](#10)
  - [1.11 讲一下 let、var、const 的区别](#11-讲一下letvarconst的区别)
  - [1.12 闭包](#12-闭包是什么为什么要使用闭包)
  - [1.13 获取页面url，search参数生成对象](#13-获取页面url，search参数生成对象)
  - [1.14 判断一个字符是否回文](#14-判断一个字符是否回文)
  - [1.15 数组去重](#15-数组去重)
  
- [2.计算机网络题目](#计算机网络知识)
  - [2.1 cookie/webStorage](#1请你谈谈-cookie你对-cookie-的理解以及与-seesionstoragelocalstorage-的区别)
  - [2.2 url 输入到页面显示的过程](#2-一个页面从输入-url-到页面加载显示完成这个过程中都发生了什么)
  - [2.3 GET 和 POST 区别](#3get-与-post-请求的区别)
  - [2.4 如何解决跨域](#4如何解决跨域问题跨域常考题)
  - [2.5 TCP UDP 区别](#5-tcp-和-udp-的区别)

- [3.HTML5/CSS3](#htmlcss)

  - [3.1 CSS 盒子模型](#1-介绍一下-css-的盒子模型box-sizing--content--padding--margin--border)
  - [3.2 CSS 选择符](#2-css-选择符有哪些哪些属性可以继承优先级算法如何计算-css3-新增伪类有那些)
  - [3.3 CSS3 新特性](#3-css3-有哪些新特性)
  - [3.4 Image alt 属性](#4)
  - [3.5 页面渲染 html 的过程](#5)

- [4.react/vue](#react--vue)
- [5.其他](#其他)
  - [5.1 说说常见的排序算法](#1说说常见的算法)
  - [5.2 git 用法](#2说说git用法)
  - [5.3 实习时间](#)

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

### 4.事件循环

[事件循环看这一篇就够了](https://zhuanlan.zhihu.com/p/87684858)

js 引擎遇到一个异步事件后并不会一直等待其返回结果，而是会将这个事件挂起，继续执行执行栈中的其他任务。当一个异步事件返回结果后，js 会将这个事件加入与当前执行栈不同的另一个队列，我们称之为事件队列。被放入事件队列不会立即执行其回调，而是等待当前执行栈中的所有任务都执行完毕，主线程处于闲置状态时，主线程会去查找事件队列是否有任务。如果有，那么主线程会从中去除排在第一位的事件，并把这个事件对应的回调放入执行栈中，然后执行其中的同步代码...，如此反复，这样就形成了一个循环。这就是这个过程被称为“事件循环（Event Loop）“的原因。

以下事件属于宏任务：

```
setInterval()
setTimeout()
```

以下事件属于微任务：

```
new Promise()
new MutationObserver()
```

我们只需要记住当当前执行栈执行完毕时，会立即处理所有微任务队列中的事件，然后再去宏任务队列中取出一个事件。同一次循环中微任务永远再宏任务之前执行。

**为什么要区分微任务和宏任务**

---

### 5. js 数据类型

### 6. js 内存回收机制

---

### 7. Set,Map / weakSet,weakMap

**Set/WeakSet**

ES6 新增的一种新的数据结构，类似于数组，但成员是唯一且无序的，没有重复的值。

Set 本身是一种构造函数，用来生成 Set 数据结构。

```
new Set([iterable])
```

WeakSet 对象允许你将弱引用对象储存在一个集合中

WeakSet 与 Set 的区别：

WeakSet 对象中储存的对象值都是被弱引用的，即垃圾回收机制不考虑 WeakSet 对该对象的应用，如果没有其他的变量或属性引用这个对象值，则这个对象将会被垃圾回收掉（不考虑该对象还存在于 WeakSet 中），所以，WeakSet 对象里有多少个成员元素，取决于垃圾回收机制有没有运行，运行前后成员个数可能不一致，遍历结束之后，有的成员可能取不到了（被垃圾回收了），WeakSet 对象是无法被遍历的（ES6 规定 WeakSet 不可遍历），也没有办法拿到它包含的所有元素

属性：

constructor：构造函数，任何一个具有 Iterable 接口的对象，都可以作参数

```
const arr = [[1, 2], [3, 4]]
const weakset = new WeakSet(arr)
console.log(weakset)
```

**Map/weakMap**

共同点：集合、字典 可以储存不重复的值
不同点：集合 是以 [value, value]的形式储存元素，字典 是以 [key, value] 的形式储存

WeakMap 对象是一组键值对的集合，其中的键是弱引用对象，而值可以是任意。

注意，WeakMap 弱引用的只是键名，而不是键值。键值依然是正常引用。

WeakMap 中，每个键对自己所引用对象的引用都是弱引用，在没有其他引用和该键引用同一对象，这个对象将会被垃圾回收（相应的 key 则变成无效的），所以，WeakMap 的 key 是不可枚举的。

---

### 8. web 性能优化

[前端性能优化](https://zhuanlan.zhihu.com/p/22215561)

```
一、尽量减少前端HTTP请求
二、浏览器缓存
三、页面压缩
四、HTML代码结构优化
五、组件分成多个域
六、图片懒加载
七、图片，脚本，数据 预加载
八、图片base64
```

---

### 9. Promise

---

### 10.export 和 export default

1.export 与 export default 均可用于导出常量、函数、文件、模块等

2.你可以在其它文件或模块中通过 import+(常量 | 函数 | 文件 | 模块)名的方式，将其导入，以便能够对其进行使用

3.在一个文件或模块中，export、import 可以有多个，export default 仅有一个

4.通过 export 方式导出，在导入时要加{ }，export default 则不需要

---

### 11 讲一下 let、var、const 的区别

```
var 没有块级作用域，支持变量提升。
let 有块级作用域，不支持变量提升。不允许重复声明，暂存性死区。不能通过window.变量名进行访问.
const 有块级作用域，不支持变量提升，不允许重复声明，暂存性死区。声明一个变量一旦声明就不能改变，改变报错。
```

### 12 闭包是什么，为什么要使用闭包

闭包：即重用一个变量，又保护变量不被污染的一种机制。

为什么使用闭包 : 全局变量和局部变量都具有不可兼得的优缺点。

```
 　　全局变量:  优: 可重用, 缺: 易被污染。
 　　局部变量:  优: 仅函数内可用，不会被污染。
 　　　　　　   缺: 不可重用!
```

何时使用: 只要即重用一个变量，又保护变量不被污染时。

如何: 3 步:

```
　　 1. 用外层函数包裹要保护的变量和内层函数。
 　　2. 外层函数将内层函数返回到外部。
　　 3. 调用外层函数，获得内层函数的对象，保存在外部的变量中——形成了闭包。　　
```

闭包形成的原因: 外层函数调用后，外层函数的函数作用域（AO）对象无法释放，被内层函数引用着。

闭包的缺点：

```
 　　比普通函数占用更多的内存。
 　　解决：闭包不在使用时，要及时释放。
 　　将引用内层函数对象的变量赋值为null。
```

---



### 13 获取页面url，search参数生成对象

直接生成对象
```
function query(sHref = window.location.href){
    var obj = {};
    var args = sHref.split('?');
    if(args[0] == sHref) return obj;
    var arr = args[1].split('&');
    for(var i = 0;i< arr.length;i++){
        var arg = arr[i].split('=');
        obj[arg[0]] = arg[1];
    }
    return obj;
}
```

获取指定名称search对象名所对应的值
```
function getQueryVariable(variable)
{
       var query = window.location.search.substring(1);
       var vars = query.split("&");
       for (var i=0;i<vars.length;i++) {
               var pair = vars[i].split("=");
               if(pair[0] == variable){return pair[1];}
       }
       return(false);
}
```

---
### 14 判断一个字符是否回文

回文是指类似于“上海自来水来自海上”或者“madam”，从前往后和从后往前读，字符串的内容是一样的，称为回文。判断一个字符串是否是回文有很多种思路：

1: 创建一个与原字符串前后倒过来的新字符串，比较二者是否相等，如果相等则是回文.

1.1 利用中介Array.reverse()的反转数组的特性
```
function isPalindRome(str) {
    return str.split('').reverse().join('') === str;

}

console.log(isPalindRome('madam')); //true
console.log(isPalindRome('mada')); //false
```

1.2 不利用任何方法，手动创建新字符串
```
function isPalindRome(str) {
    let newStr = '';
    for(let i = str.length - 1; i >= 0; i --){
        newStr = newStr + str[i];

    }
    return newStr === str;

}

console.log(isPalindRome('madam'));
console.log(isPalindRome('mada')); 
```


2: 从字符串的头和尾开始，依次比较字符串组是否相等，逐渐往中间收，如果全部相等，则是回文
```
function isPalindRome(str) {
    let length = str.length;
    for(let i = 0; i <= Math.floor(str.length / 2); i ++){
        if(str[i] !== str[length - 1 - i]){
            return false;
        }
    }

    return true;

}

console.log(isPalindRome('aabbaa')); //true
console.log(isPalindRome('aabaa')); //true
console.log(isPalindRome('abb')); //false
```

---

### 15 数组去重

2.1 利用ES6新增的Set，因为Set的元素是非重复的
```
function deduplicate(arr) {
    return Array.from(new Set(arr));
}
deduplicate([1,1,2,2,3]);//[1,2,3]
```

2.1 创建一个新数组，只包含源数组非重复的元素
```
function deduplicate(arr) {
    let newArray = [];
    for(let i of arr){
        if(newArray.indexOf(i) === -1){
            newArray.push(i);
        }
    }
    return newArray;
}
deduplicate([1, 1, 2, 2, 3]);//[1,2,3]
```
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

### 4.如何解决跨域问题(跨域常考题)

[JS 中的跨域问题及解决办法汇总](https://blog.csdn.net/lareinalove/article/details/84107476)

---

### 5 TCP 和 UDP 的区别

TCP 的优点：

```
可靠，稳定 TCP的可靠体现在TCP在传递数据之前，会有三次握手来建立连接，而且在数据传递时，有确认、窗口、重传、拥塞控制机制，在数据传完后，还会断开连接用来节约系统资源。
```

TCP 的缺点：

```
慢，效率低，占用系统资源高，易被攻击 TCP在传递数据之前，要先建连接，这会消耗时间，而且在数据传递时，确认机制、重传机制、拥塞控制机制等都会消耗大量的时间，而且要在每台设备上维护所有的传输连接，事实上，每个连接都会占用系统的CPU、内存等硬件资源。 而且，因为TCP有确认机制、三次握手机制，这些也导致TCP容易被人利用，实现DOS、DDOS、CC等攻击。
```

UDP 的优点：

```
 快，比TCP稍安全 UDP没有TCP的握手、确认、窗口、重传、拥塞控制等机制，UDP是一个无状态的传输协议，所以它在传递数据时非常快。没有TCP的这些机制，UDP较TCP被攻击者利用的漏洞就要少一些。但UDP也是无法避免攻击的，比如：UDP Flood攻击……
```

UDP 的缺点：

```
不可靠，不稳定 因为UDP没有TCP那些可靠的机制，在数据传递时，如果网络质量不好，就会很容易丢包。 基于上面的优缺点，那么： 什么时候应该使用TCP： 当对网络通讯质量有要求的时候，比如：整个数据要准确无误的传递给对方，这往往用于一些要求可靠的应用，比如HTTP、HTTPS、FTP等传输文件的协议，POP、SMTP等邮件传输的协议。 在日常生活中，常见使用TCP协议的应用如下： 浏览器，用的HTTP FlashFXP，用的FTP Outlook，用的POP、SMTP Putty，用的Telnet、SSH QQ文件传输 ………… 什么时候应该使用UDP： 当对网络通讯质量要求不高的时候，要求网络通讯速度能尽量的快，这时就可以使用UDP。 比如，日常生活中，常见使用UDP协议的应用如下： QQ语音 QQ视频 TFTP ……
```

1、TCP 面向连接（如打电话要先拨号建立连接）;UDP 是无连接的，即发送数据之前不需要建立连接

2、TCP 提供可靠的服务。也就是说，通过 TCP 连接传送的数据，无差错，不丢失，不重复，且按序到达;UDP 尽最大努力交付，即不保证可靠交付

3、TCP 面向字节流，实际上是 TCP 把数据看成一连串无结构的字节流;UDP 是面向报文的。UDP 没有拥塞控制，因此网络出现拥塞不会使源主机的发送速率降低（对实时应用很有用，如 IP 电话，实时视频会议等）

4、每一条 TCP 连接只能是点到点的;UDP 支持一对一，一对多，多对一和多对多的交互通信

5、TCP 首部开销 20 字节;UDP 的首部开销小，只有 8 个字节

6、TCP 的逻辑通信信道是全双工的可靠信道，UDP 则是不可靠信道

---

### 6 http 响应码

```
http响应状态码大全
http状态返回代码 1xx（临时响应）
表示临时响应并需要请求者继续执行操作的状态代码。

http状态返回代码 代码   说明
100   （继续） 请求者应当继续提出请求。 服务器返回此代码表示已收到请求的第一部分，正在等待其余部分。
101   （切换协议） 请求者已要求服务器切换协议，服务器已确认并准备切换。

http状态返回代码 2xx （成功）
表示成功处理了请求的状态代码。

http状态返回代码 代码   说明
200   （成功）  服务器已成功处理了请求。 通常，这表示服务器提供了请求的网页。
201   （已创建）  请求成功并且服务器创建了新的资源。
202   （已接受）  服务器已接受请求，但尚未处理。
203   （非授权信息）  服务器已成功处理了请求，但返回的信息可能来自另一来源。
204   （无内容）  服务器成功处理了请求，但没有返回任何内容。
205   （重置内容） 服务器成功处理了请求，但没有返回任何内容。
206   （部分内容）  服务器成功处理了部分 GET 请求。

http状态返回代码 3xx （重定向）
表示要完成请求，需要进一步操作。 通常，这些状态代码用来重定向。

http状态返回代码 代码   说明
300   （多种选择）
针对请求，服务器可执行多种操作。 服务器可根据请求者 (user agent) 选择一项操作，或提供操作列表供请求者选择。

301   （永久移动）
请求的网页已永久移动到新位置。 服务器返回此响应（对 GET 或 HEAD 请求的响应）时，会自动将请求者转到新位置。

302   （临时移动）
服务器目前从不同位置的网页响应请求，但请求者应继续使用原有位置来进行以后的请求。

303   （查看其他位置）
请求者应当对不同的位置使用单独的 GET 请求来检索响应时，服务器返回此代码。

304   （未修改）
 自从上次请求后，请求的网页未修改过。 服务器返回此响应时，不会返回网页内容。

305   （使用代理）
请求者只能使用代理访问请求的网页。 如果服务器返回此响应，还表示请求者应使用代理。

307   （临时重定向）
服务器目前从不同位置的网页响应请求，但请求者应继续使用原有位置来进行以后的请求。

http状态返回代码 4xx（请求错误）
这些状态代码表示请求可能出错，妨碍了服务器的处理。

http状态返回代码 代码   说明
400   （错误请求） 服务器不理解请求的语法。
401   （未授权） 请求要求身份验证。 对于需要登录的网页，服务器可能返回此响应。
403   （禁止） 服务器拒绝请求。
404   （未找到） 服务器找不到请求的网页。
405   （方法禁用） 禁用请求中指定的方法。
406   （不接受） 无法使用请求的内容特性响应请求的网页。
407   （需要代理授权） 此状态代码与 401（未授权）类似，但指定请求者应当授权使用代理。
408   （请求超时）  服务器等候请求时发生超时。
409   （冲突）  服务器在完成请求时发生冲突。 服务器必须在响应中包含有关冲突的信息。
410   （已删除）  如果请求的资源已永久删除，服务器就会返回此响应。
411   （需要有效长度） 服务器不接受不含有效内容长度标头字段的请求。
412   （未满足前提条件） 服务器未满足请求者在请求中设置的其中一个前提条件。
413   （请求实体过大） 服务器无法处理请求，因为请求实体过大，超出服务器的处理能力。
414   （请求的 URI 过长） 请求的 URI（通常为网址）过长，服务器无法处理。
415   （不支持的媒体类型） 请求的格式不受请求页面的支持。
416   （请求范围不符合要求） 如果页面无法提供请求的范围，则服务器会返回此状态代码。
417   （未满足期望值） 服务器未满足"期望"请求标头字段的要求。

http状态返回代码 5xx（服务器错误）
这些状态代码表示服务器在尝试处理请求时发生内部错误。 这些错误可能是服务器本身的错误，而不是请求出错。

http状态返回代码 代码   说明
500   （服务器内部错误）  服务器遇到错误，无法完成请求。
501   （尚未实施） 服务器不具备完成请求的功能。 例如，服务器无法识别请求方法时可能会返回此代码。
502   （错误网关） 服务器作为网关或代理，从上游服务器收到无效响应。
503   （服务不可用） 服务器目前无法使用（由于超载或停机维护）。 通常，这只是暂时状态。
504   （网关超时）  服务器作为网关或代理，但是没有及时从上游服务器收到请求。
505   （HTTP 版本不受支持） 服务器不支持请求中所用的 HTTP 协议版本。

一些常见的http状态返回代码为：
200 - 服务器成功返回网页
404 - 请求的网页不存在
503 - 服务不可用
```

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

### 3.4 image 中 alt 属性

---

### 3.5 页面渲染 html 过程

1.浏览器解析 html 源码，然后创建一个 DOM 树。并行请求 css/image/js 在 DOM 树中，每一个 HTML 标签都有一个对应的节点，并且每一个文本也都会有一个对应的文本节点。DOM 树的根节点就是 documentElement，对应的是 html 标签。

2.浏览器解析 CSS 代码，计算出最终的样式数据。构建 CSSOM 树。对 CSS 代码中非法的语法它会直接忽略掉。解析 CSS 的时候会按照如下顺序来定义优先级：浏览器默认设置 < 用户设置 < 外链样式 < 内联样式 < html 中的 style。

3.DOM Tree + CSSOM --> 渲染树（rendering tree）。渲染树和 DOM 树有点像，但是是有区别的。

DOM 树完全和 html 标签一一对应，但是渲染树会忽略掉不需要渲染的元素，比如 head、display:none 的元素等。而且一大段文本中的每一个行在渲染树中都是独立的一个节点。渲染树中的每一个节点都存储有对应的 css 属性。

4.一旦渲染树创建好了，浏览器就可以根据渲染树直接把页面绘制到屏幕上。

以上四个步骤并不是一次性顺序完成的。如果 DOM 或者 CSSOM 被修改，以上过程会被重复执行。实际上，CSS 和 JavaScript 往往会多次修改 DOM 或者 CSSOM。

---

## React / Vue

## 其他

### 1.说说常见的算法

### 2.说说 git 用法
