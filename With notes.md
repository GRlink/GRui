### 1.src和href各用在哪些标签，区别是什么？

href 表示超文本引用（hypertextreference），在 link和a 等元素上使用。href 的内容，是与该页面有关联，是引用。

src 表示来源地址，在 img、script、iframe 等元素上。src 的内容，是页面必不可少的一部分，是引入。

### 2.jQuery绑定事件的三种方法以及区别

（1）target.click(function(){});       一次绑定一个事件
（2）target.bind("click",function(){});     可以同时绑定多个事件
（3）target.live("click",function(){});      委派事件（1.7以下版本支持）
（4）on("click",function(){});

### 3.json是什么,原理？

json是一种轻量级的数据交换格式,json简单说就是javascript中的对象和数组

### 4.new

1.创建空对象；

　　var obj = {};

2.设置新对象的constructor属性为构造函数的名称，**设置新对象的__proto__属性指向构造函数的prototype对象；**　　obj.__proto__ = ClassA.prototype;

3.使用新对象调用函数，函数中的this被指向新实例对象：

　　ClassA.call(obj);　　//{}.构造函数();          

4.将初始化完毕的新对象地址，保存到等号左边的变量中

### 5.jsonp的跨域原理

JSONP的最基本的原理是：动态添加一个<script>标签，而script标签的src属性是没有跨域的限制的。这样说来，这种跨域方式其实与ajax XmlHttpRequest协议无关了。

用jsonp的原因是json是javascript中的对象，而跨域访问中有图片、css、javascript脚本文件等是不限制，因此你可以在页面渲染时动态在<script>标签设置src路径，而这个路径返回回来的就是json对象

### 6.更好的优化页面，加载速度更快

模块化开发
Ajax应用
渐进式增强*
富客户端运用
增强可读性

### 7.前端开发的优化问题，详细说说？

（1） 减少http请求次数：css spirit,data uri
（2） JS，CSS源码压缩
（3） 前端模板 JS+数据，减少由于HTML标签导致的带宽浪费，前端用变量保存AJAX请求结果，每次操作本地变量，不用请求，减少请求次数
（4） 用innerHTML代替DOM操作，减少DOM操作次数，优化javascript性能
（5） 用setTimeout来避免页面失去响应
（6） 用hash-table来优化查找
（7） 当需要设置的样式很多时设置className而不是直接操作style
（8） 少用全局变量
（9） 缓存DOM节点查找的结果
（10） 避免使用CSS Expression
（11） 图片预载
（12） 避免在页面的主体布局中使用table，table要等其中的内容完全下载之后才会显示出来，显示比div+css布局慢

### 8.CSS HACK如何书写

*：仅在IE6/7中支持，其他浏览器不支持
_：仅在IE6中支持，其他浏览器均不支持
‘\9’：区分所有的IE浏览器与其他浏览器
‘\9\0’：IE9、IE10支持，其他浏览器均不支持
‘\0’：IE8、IE9、IE10支持，其他浏览器均不支持

### 9.创建插入删除节点

jquery:
append() - 在被选元素内部的结尾插入指定内容
prepend() - 在被选元素内部的开头插入指定内容
after() - 在被选元素之后插入内容
before() - 在被选元素之前插入内容
remove() - 删除被选元素（及其子元素）
empty() - 从被选元素中删除子元素
js:
appendChild()
insertBefore()
removeChild()

### 10.nodejs

服务器端的js运行环境 

### 11.call和apply的区别？

call方法: 调用一个对象的一个方法，以另一个对象替换当前对象。
apply方法： 应用某一对象的一个方法，用另一个对象替换当前对象。

### 12.如何阻止事件冒泡和默认事件？

阻止事件冒泡  .stopPropagation     .cancleBubble=true
阻止默认事件  .preventDefault     Return false

### 13.冒泡机制

事件冒泡：事件从事件目标(target)开始，往上冒泡直到页面的最上一级标签。

### 14.继承的几种方式

1.使用对象冒充实现继承
2.采用call方法改变函数上下文实现继承
3.采用Apply方法改变函数上下文实现继承
4.采用原型链的方式实现继承
5.采用混合模式实现继承
6.Es6的extends 

### 15.cookie特点

一般小于4KB
自动发送给服务器

### 16.渐进增强和优雅降级

渐进增强：针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器进行效果/交互等改进和追加功能达到更好的用户体验。
优雅降级：一开机就构建完整的功能，然后再针对低版本浏览器进行兼容

### 17.清除浮动的方法。

（1）clear:both
（2）给父容器添加一个:after伪元素，content:"\20"
（3）overflow:hidden 或 overflow:auto
（4）给父元素也添加浮动

### 18.让用户只点击一次

（1）在点击一次之后，把点击事件的功能清除
（2）disabled

### 19.string对象的方法

charAt()返回第n个
concat()连接字符串
indexOf()检索字符串
slice()截取字符串
split()将字符串分割成数组
substr()截取字符串
substring()截取

### 20.Array对象的方法

concat()连接数组
join()将数组按指定的符号连接起来，返回一个字符串
pop()删除并返回数组的最后一个元素   出栈
push()入栈  给数组添加元素
reverse()颠倒元素顺序
shift()将元素移除数组
slice()截取数组
sort()排序
splice()插入/删除/替换元素
toString()将数组转换成一个字符串

### 21.同源策略

同源策略是网景公司提出的一个著名的安全策略，现在所有支持javascript的浏览器都会使用这个策略，所谓同源是指，域名/协议/端口相同，在浏览器的一个页面在执行一个脚本的时候会检查这个脚本是属于那个页面的，即检查是否同源，只有和当前页面同源的脚本才会被执行。如果非同源，那么在请求时，浏览器会报一个异常在控制台。

### 22.跨域的方法

jsonp
document.domain
动态创建script标签

### 23.对象冻结

一个对象是冻结是指它不可扩展，所有属性都是不可配置的，却所有数据属性都是不可写的
或者说，冻结对象是指那些不能添加新的属性，不能修改已有的属性的值，不能删除已有属性，也就是说，这个对象永远是不可变得。

### 24.变量提升

在javascript中，函数及变量的声明都会被提升到函数的最顶部。也就是说，变量可以在使用后声明。
var let const中，var的声明会被提升到该作用于的顶部，但是被赋的值不会提升。let和const被赋予了一个“暂存性死区”的概念

### 25.暂存死区

在es6中,let绑定不受变量提升的约束，这意味着let声明不会被提升到当前执行上下文的顶部。在块中的变量初始化之前，引用它将会导致引用错误。
而暂存性死区是指从代码块开始到let声明之间的区域

### 26.let的特点

不存在变量提升
暂存性死去：let声明的变量被绑定到该区域，不在受外部影响
同一个作用于中，不允许重复声明

### 27.jquery怎么实现链式写法的

通过使用对象上的方法之后return this 返回当前对象，然后继续调用就可以了。

### 28.闭包是什么，有什么特性，对页面有什么影响

   闭包：是有权访问另一个函数作用域中变量的函数
   对页面的影响：由于闭包时，变量的值都保存到内存中，会导致页面加载时内存消耗很大，IE会导致内在泄露，因此尽量少用或用时要及时删除变量。

### 29.localStorage

保存的数据，一般情况下是永久保存的，也就是说只要采用localstorage保存信息，数据便一直存储在用户的客户端中。即使用户关闭当前web浏览器后重新启动，数据让然存在。知道用户或程序明确制定删除，数据的生命周期才会结束。

在安全性方面，localstorage是域内安全的，即localstorage是基于域的。任何在该域内的所有页面，都可以访问localstorage数据。

无法互相读取数据。

### 30.sessionStorage

1. 服务器会把长时间没有活动的Session从服务器内存中清除，此时Session便失效。Tomcat中Session的默认失效时间为20分钟。
2. 调用Session的invalidate方法。




### 31.cookie是什么

服务器向客户端浏览器写入并存储的非加密信息



### 32.session

session的工作原理

（1）当一个session第一次被启用时，一个唯一的标识被存储于本地的cookie中。

（2）首先使用session_start()函数，[PHP](https://baike.baidu.com/item/PHP/9337)从session仓库中加载已经存储的session变量。

（3）当执行PHP脚本时，通过使用session_register()函数注册session变量。

（4）当PHP脚本执行结束时，未被销毁的session变量会被自动保存在本地一定路径下的session库中，这个路径可以通过php.ini文件中的session.save_path指定，下次浏览网页时可以加载使用。



### 33.cookie 和session 的区别

1、cookie数据存放在客户的浏览器上，session数据放在服务器上。

2、cookie不是很安全，别人可以分析存放在本地的COOKIE并进行COOKIE欺骗
   考虑到安全应当使用session。

3、session会在一定时间内保存在服务器上。当访问增多，会比较占用你服务器的性能
   考虑到减轻服务器性能方面，应当使用COOKIE。

4、单个cookie保存的数据不能超过4K，很多浏览器都限制一个站点最多保存20个cookie。

5、所以个人建议：
   将登陆信息等重要信息存放为SESSION
   其他信息如果需要保留，可以放在COOKIE中



### 34.深拷贝和浅拷贝

在js中，深拷贝会复制被拷贝对象的文本和子元素，浅拷贝是只复制标签

jq中，深拷贝会复制



### 35.tigger和tiggerhandler的区别

###### tiggerhandler:

不会触发执行元素的默认行为(例如链接click事件默认的跳转行为，表单submit事件默认的提交行为)。

触发事件只针对jQuery对象中的第一个匹配元素。

触发的事件不会在DOM树中冒泡，因此事件不会冒泡传递到它的任何祖辈元素。

返回值是对应事件处理函数的返回值，而不是当前jQuery对象本身。

###### tigger:

trigger() 方法触发被选元素上指定的事件以及事件的默认行为（比如表单提交）。



### 36.如何判断用户使用的浏览器

```
<script type="text/javascript">  
  var Sys = {};  
        var ua = navigator.userAgent.toLowerCase();  
        var s;  
        (s = ua.match(/msie ([\d.]+)/)) ? Sys.ie = s[1] :  
        (s = ua.match(/firefox\/([\d.]+)/)) ? Sys.firefox = s[1] :  
        (s = ua.match(/chrome\/([\d.]+)/)) ? Sys.chrome = s[1] :  
        (s = ua.match(/opera.([\d.]+)/)) ? Sys.opera = s[1] :  
        (s = ua.match(/version\/([\d.]+).*safari/)) ? Sys.safari = s[1] : 0;  
        /以下进行测试/  
        if (Sys.ie) alert('IE: ' + Sys.ie);  
        if (Sys.firefox) alert('Firefox: ' + Sys.firefox);  
        if (Sys.chrome) alert('Chrome: ' + Sys.chrome);  
        if (Sys.opera) alert('Opera: ' + Sys.opera);  
        if (Sys.safari) alert('Safari: ' + Sys.safari);  
        if (Sys.ie == 6.0){alert("fuck!")}  
</script> 

```







### 36.angularjs特点

1.数据的双向绑定：这可能是其最激动人心的特性吧，view层的数据和model层的数据是双向绑定的，其中之一发生更改，另一方会随之变化，这不用你写任何代码！（想想jQuery方式下怎么做吧）

2.代码模块化，每个模块的代码独立拥有自己的作用域，model，controller等。

3.强大的directive可以将很多功能封装成HTML的tag,属性或者注释等，这大大美化了HTML的结构，增强了可阅读性；

4.依赖注入，将这种后端语言的设计模式赋予前端代码，这意味着前端的代码可以提高重用性和灵活性，未来的模式可能将大量操作放在客户端，服务端只提供数据来源和其他客户端无法完成的操作；

5.测试驱动开发，angularjs一开始就以此为目标，使用angular开发的应用可以很容易地进行单元测试和端对端测试，这解决了传统的js代码难以测试和维护的缺陷

以上就是研究angularjs一段时间得出的结论，其中某些地方可能有所疏漏，没关系，接下来会展开其中某一点一步步去学习。

### 37.react特点

　　（1）声明式设计

　　（2）高效：通过对DOM的模拟，最大限度的减少与DOM的交互。

　　（3）灵活：可以与已知的框架或库很好的配合。

　　（4）JSX：是js语法的扩展，不一定使用，但建议用。

　　（5）组件：构建组件，使代码更容易得到复用，能够很好地应用在大项目的开发中。

　　（6）单向响应的数据流：React实现了单向响应的数据流，从而减少了重复代码，这也是解释了它为什么比传统数据绑定更简单。

### 38.vue特点

1. 简单：官方文档很清晰，比 Angular 简单易学。
2. 快速：异步批处理方式更新 DOM。
3. 组合：用解耦的、可复用的组件组合你的应用程序。
4. 紧凑：~23kb min+gzip，且无依赖。
5. 强大：表达式 & 无需声明依赖的可推导属性 (computed properties)。
6. 对模块友好：可以通过 NPM、Bower 或 Duo 安装，不强迫你所有的代码都遵循 Angular 的各种规定，使用场景更加灵活。


### 39.ES6的对象的解构赋值与数组解构赋值的区别:

数组解构赋值是根据元素位置赋值, 由于对象是无序的属性值对, 所以解构赋值时需要注意, 同名的属性才会被赋值成功(根据对象的属性名来赋对应的值).





  M model 后台获取的json数据 处理显示的

  V view 显示数据的DOM区域

  C controller angularjs 控制器
快速开发  高效能  全平台



