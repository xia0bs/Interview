# 前端工程师面试总结
#  知识点测试
## HTML
1. Doctype作用？标准模式与兼容模式各有什么区别?
     <!DOCTYPE>告知浏览器的解析器用什么文档标准解析这个文档。DOCTYPE不存在或格式不正确会导致文档以兼容模式呈现。
    标准模式的排版和JS运作模式都是以该浏览器支持的最高标准运行。在兼容模式中，页面以宽松的向后兼容的方式显示,模拟老式浏览器的行为以防止站点无法工作。

2. WEB标准以及W3C标准是什么？
    标签闭合、标签小写、不乱嵌套、使用外链css和js、结构行为表现的分离。

3. 行内元素有哪些？块级元素有哪些？  
    行内元素: a b img  em br i span input select
    块级元素：div p h1-h6 form ul dl ol table

4. 行元素和块元素有哪些？有什么特性？ 空(void)元素有哪些？
    行内元素不可以设置宽高，不独占一行;
    块级元素可以设置宽高，独占一行。
    空元素     
`<br> <hr> <img> <input> <link> <meta> <area> <base> <col> <command> <embed> <keygen> <param> <source> <track> <wbr>`

5.  页面载入时，link和@import有什么区别？
    （1）link属于xhtml标签，除了加载css之外，还能用于定义RSS,定义rel连接属性等作用而@import是css提供的只用于加载css
    （2）页面加载时，link会同时被加载；@import引用css会等页面加载完毕之后在加载
     （3）@import只有ie5以上浏览器才兼容，而link属于xhtml无兼容问题

6.   清除浮动有几种方式，各自的优缺点？


     （1）在父元素结尾添加空div标签clear:both
               简单，代码少，浏览器支持好，不容易出现怪问题;不少初学者不理解原理；如果页面浮动布局多，就要增加很多空div，让人感觉很不爽;这种方法不推荐使用，这是以前的一种使用方式。

     （2）给父元素添加before、after伪元素
              浏览器支持好，在ie8以上的ie浏览器和非ie中才支持，代码较多

     （3）给父元素添加overflow:hidden 属性
             必须定义width或zoom:1，同时不能定义height，使用overflow:hidden时，浏览器会自动检查浮动区域的高度，代码少，简单浏览器支持，不能和position配合使用，因为超出部分被隐藏

      （4）父级元素一起浮动，所有代码浮动变成一个整体，但是会产生新的问题，只做了解不推荐使用。

      （5）父级div定义display:table ，只做了解不推荐使用。

      （6） 结尾处加br标签clear:both ，只做了解不推荐使用。

7.  前端页面有三层构成，分别是什么？有什么作用？
       结构层、表示层、行为层

       网页的结构层(structural layer)由 HTML 或 XHTML 之类的标记语言负责创建。通过标签对网页内容的语义含义做出了描述，但这些标签不包含任何关于如何显示有关内容的信息。<br>
       网页的表示层(presentation layer) 由 CSS 负责创建。 CSS 对“如何显示有关内容”的问题做出了回答。<br>

       网页的行为层(behavior layer)负责回答“内容应该如何对事件做出反应”这一问题。这是 Javascript 语言和 DOM 主宰的领域。    

8. 简述标签中alt和title有什么区别？

      alt是html标签的属性，而title既是html标签，又是html属性。title作为标签是文档的标题，title作为属性是为元素提供额外的说明信息。例如，给超链接标签a添加了title属性，把鼠标移动到该链接上面是，就会显示title的内容，以达到补充说明或者提示的效果。而alt属性则是用来指定替换文字，只能用在img、area和input元素中（包括applet元素），用于网页中图片无法正常显示时给用户提供文字说明使其了解图像信息。
9.  简述几种可以提高页面加载速度的方法？

    （1） 减少http请求次数：CSS Sprites, JS、CSS源码压缩、图片大小控制合适；网页Gzip，CDN托管，data缓存 ，图片服务器。

    （2） 前端模板 JS+数据，减少由于HTML标签导致的带宽浪费，前端用变量保存AJAX请求结果，每次操作本地变量，不用请求，减少请求次数

    （3） 用innerHTML代替DOM操作，减少DOM操作次数，优化javascript性能。

    （4） 当需要设置的样式很多时设置className而不是直接操作style。

    （5） 少用全局变量、缓存DOM节点查找的结果。减少IO读取操作。

    （6） 避免使用CSS Expression（css表达式)又称Dynamic properties(动态属性)。

    （7） 图片预加载，将样式表放在顶部，将脚本放在底部  加上时间戳。

    （8） 避免在页面的主体布局中使用table，table要等其中的内容完全下载之后才会显示出来，显示比div+css布局慢。对普通的网站有一个统一的思路，就是尽量向前端优化、减少数据库操作、减少磁盘IO。向前端优化指的是，在不影响功能和体验的情况下，能在浏览器执行的不要在服务端执行，能在缓存服务器上直接返回的不要到应用服务器，程序能直接取得的结果不要到外部取得，本机内能取得的数据不要到远程取，内存能取到的不要到磁盘取，缓存中有的不要去数据库查询。减少数据库操作指减少更新次数、缓存结果减少查询次数、将数据库执行的操作尽可能的让你的程序完成（例如join查询），减少磁盘IO指尽量不使用文件系统作为缓存、减少读写文件次数等。程序优化永远要优化慢的部分，换语言是无法“优化”的。

10. html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 HTML 和HTML5？

     HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加。
      绘画 canvas;
      用于媒介回放的 video 和 audio 元素;
      本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失;
      sessionStorage 的数据在浏览器关闭后自动删除;
      语意化更好的内容元素，比如 article、footer、header、nav、section;
      表单控件，calendar、date、time、email、url、search;
      新的技术webworker, websocket, Geolocation;

     移除的元素：
      纯表现的元素：basefont，big，center，font, s，strike，tt，u;
      对可用性产生负面影响的元素：frame，frameset，noframes；

    支持HTML5新标签：
     IE8/IE7/IE6支持通过document.createElement方法产生的标签，
     可以利用这一特性让这些浏览器支持HTML5新标签， 浏览器支持新标签后，还需要添加标签默认的样式。当然也可以直接使用成熟的框架、比如html5shim;

     如何区分HTML5： DOCTYPE声明\新增的结构元素\功能元素
11. HTML5中新增的API有哪些？
     canvas、拖拽、audio、video、本地存储等。
12. 简述cookie，localStorage，sessionStorage的区别？

     cookie是网站为了标示用户身份而储存在用户本地终端（Client Side）上的数据（通常经过加密）。
     cookie数据始终在同源的http请求中携带（即使不需要），记会在浏览器和服务器间来回传递。
     sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。

    存储大小：
    cookie数据大小不能超过4k。
    sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大。

    有期时间：
    localStorage    存储持久数据，浏览器关闭后数据不丢失除非主动删除数据；
    sessionStorage  数据在当前浏览器窗口关闭后自动删除。
    cookie  设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭

13. 你做的页面经常在哪些浏览器进行测试？这些浏览器的内核是什么？
     Trident内核：IE,MaxThon,TT,The World,360,搜狗浏览器等。[又称MSHTML]
     Gecko内核：Netscape6及以上版本，FF,MozillaSuite/SeaMonkey等
     Presto内核：Opera7及以上。      [Opera内核原为：Presto，现为：Blink;]
     Webkit内核：Safari,Chrome等。   [ Chrome的：Blink（WebKit的分支）]

14. 浏览器内核的理解？
     主要分成两部分：渲染引擎(layout engineer或Rendering Engine)和JS引擎。
     渲染引擎：负责取得网页的内容（HTML、XML、图像等等）、整理讯息（例如加入CSS等），以及计算网页的显示方式，然后会输出至显示器或打印机。浏览器的内核的不同对于网页的语法解释会有不同，所以渲染的效果也不相同。所有网页浏览器、电子邮件客户端以及其它需要编辑、显示网络内容的应用程序都需要内核。

    JS引擎：解析和执行javascript来实现网页的动态效果
    最开始渲染引擎和JS引擎并没有区分的很明确，后来JS引擎越来越独立，内核就倾向于只指渲染引擎。

15. 简述你就html语义化标签的理解
     用正确的标签做正确的事情。
     html语义化让页面的内容结构化，结构更清晰，便于对浏览器、搜索引擎解析;
     即使在没有样式CSS情况下也以一种文档格式显示，并且是容易阅读的;
     搜索引擎的爬虫也依赖于HTML标记来确定上下文和各个关键字的权重，利于SEO;
     使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。

16. HTML5的离线储存怎么使用，工作原理能不能解释一下？
     在用户没有与因特网连接时，可以正常访问站点或应用，在用户与因特网连接时，更新用户机器上的缓存文件。
     原理：HTML5的离线存储是基于一个新建的.appcache文件的缓存机制(不是存储技术)，通过这个文件上的解析清单离线存储资源，这些资源就会像cookie一样被存储了下来。之后当网络在处于离线状态下时，浏览器会通过被离线存储的数据进行页面展示。

17. 如何实现浏览器内多个标签页之间的通信?
     WebSocket、SharedWorker；也可以调用localstorge、cookies等本地存储方式；
     localstorge另一个浏览上下文里被添加、修改或删除时，它都会触发一个事件，
    我们通过监听事件，控制它的值来进行页面信息通信；
    注意quirks：Safari 在无痕模式下设置localstorge值时会抛出 QuotaExceededError 的异常；
18. 如何在页面上实现一个圆形的可点击区域？
     map+area或者svg
     border-radius
     纯js实现 需要求一个点在不在圆上简单算法、获取鼠标坐标等等


## CSS

1. 介绍一下标准的CSS的盒子模型？低版本IE的盒子模型有什么不同的？
    （1）有两种， IE 盒子模型、W3C 盒子模型；
    （2）盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border)；
    （3）区  别： IE的content部分把 border 和 padding计算了进去;
2.  CSS 选择符有哪些？
     id选择器（ # myid）
     类选择器（.myclassname）
     标签选择器（div, h1, p）
     相邻选择器（h1 + p）
     子选择器（ul < li）
     后代选择器（li a）
     通配符选择器（ * ）
     属性选择器（a[rel = "external"]）
     伪类选择器（a: hover, li: nth - child）

3. CSS选择器优先级？
    !important > 行内样式 > 后代、交叉 > ID > class > tag > * >浏览器预定义样式 > 继承样式
4. 常见的兼容性
    png24位的图片在iE6浏览器上出现背景，解决方案是做成PNG8.

    浏览器默认的margin和padding不同。解决方案是加一个全局的*{margin:0;padding:0;}来统一。

    IE6双边距bug:块属性标签float后，又有横行的margin情况下，在ie6显示margin比设置的大。

    浮动ie产生的双倍距离 #box{ float:left; width:10px; margin:0 0 0 100px;}  这种情况之下IE会产生20px的距离，解决方案是在float的标签样式控制中加入 ——\_display:inline;将其转化为行内属性。(\_这个符号只有ie6会识别)

    渐进识别的方式，从总体中逐渐排除局部。

    首先，巧妙的使用“\9”这一标记，将IE游览器从所有情况中分离出来。
    接着，再次使用“+”将IE8和IE7、IE6分离开来，这样IE8已经独立识别。
    css
      .bb{
          background-color:#f1ee18;/*所有识别*/
          .background-color:#00deff\9; /*IE6、7、8识别*/
          +background-color:#a200ff;/*IE6、7识别*/
          \_background-color:#1e0bd1;/*IE6识别*/
      }

    IE下,可以使用获取常规属性的方法来获取自定义属性,
    也可以使用getAttribute()获取自定义属性;
    Firefox下,只能使用getAttribute()获取自定义属性。
    解决方法:统一通过getAttribute()获取自定义属性。

    IE下,even对象有x,y属性,但是没有pageX,pageY属性;
    Firefox下,event对象有pageX,pageY属性,但是没有x,y属性。

    解决方法：（条件注释）缺点是在IE浏览器下可能会增加额外的HTTP请求数。

    Chrome 中文界面下默认会将小于 12px 的文本强制按照 12px 显示,可通过加入 CSS 属性 -webkit-text-size-adjust: none; 解决。

    超链接访问过后hover样式就不出现了 被点击访问过的超链接样式不在具有hover和active了解决方法是改变CSS属性的排列顺序:
    L-V-H-A :  a:link {} a:visited {} a:hover {} a:active {}

5. 如何居中div？如何居中一个浮动元素？如何让绝对定位的div居中？
     给div设置一个宽度，然后添加margin:0 auto属性
     div{
       width:200px;
       margin:0 auto;
     }

     居中一个浮动元素
     确定容器的宽高 宽500 高 300 的层
     设置层的外边距
     div {
       width:500px ; height:300px;//高度可以不设
       margin: -150px 0 0 -250px;
       position:relative;         //相对定位
       background-color:pink;     //方便看效果
       left:50%;
       top:50%;
     }

    让绝对定位的div居中
      position: absolute;
      width: 1200px;
      background: none;
      margin: 0 auto;
      top: 0;
      left: 0;
      bottom: 0;
      right: 0;
6. CSS3有哪些新特性？
      新增各种CSS选择器    （: not(.input)：所有 class 不是“input”的节点）
     圆角           （border-radius:8px）
     多列布局        （multi-column layout）
     阴影和反射      （Shadow\Reflect）
    文字特效      （text-shadow、）
    文字渲染      （text-decoration）
    线性渐变      （gradient）
    旋转          （transform）
    增加了旋转,缩放,平移,倾斜,动画，多背景transform:\scale(0.85,0.90)\ translate(0px,-30px)\ skew(-9deg,0deg)\Animation:

7. 用纯CSS创建一个三角形的原理是什么？
    把上、左、右三条边隐藏掉（颜色设为 transparent）
     .demo {
     width: 0;
     height: 0;
    border-width: 20px;
    border-style: solid;
    border-color: transparent transparent red transparent;
     }   
8. 什么是CSS 预处理器 / 后处理器？
    预处理器例如：LESS、Sass、Stylus，用来预编译Sass或less，增强了css代码的复用性，还有层级、mixin、变量、循环、函数等，具有很方便的UI组件模块化开发能力，极大的提高工作效率。
    后处理器例如：PostCSS，通常被视为在完成的样式表中根据CSS规范处理CSS，让其更有效；目前最常做的是给CSS属性添加浏览器私有前缀，实现跨浏览器兼容性的问题
9. 如果需要手动写动画，你认为最小时间间隔是多久，为什么？
    多数显示器默认频率是60Hz，即1秒刷新60次，所以理论上最小间隔为1/60＊1000ms ＝ 16.7ms

10. ::before 和 :after中双冒号和单冒号 有什么区别？解释一下这2个伪元素的作用
    单冒号(:)用于CSS3伪类，双冒号(::)用于CSS3伪元素。
    伪元素由双冒号和伪元素名称组成。双冒号是在css3规范中引入的，用于区分伪类和伪元素。但是伪类兼容现存样式，浏览器需要同时支持旧的伪类，比如:first-line、:first-letter、:before、:after等。
    对于CSS2之前已有的伪元素，比如:before，单冒号和双冒号的写法::before作用是一样的。
    提醒，如果你的网站只需要兼容webkit、firefox、opera等浏览器，建议对于伪元素采用双冒号的写法，如果不得不兼容IE浏览器，还是用CSS2的单冒号写法比较安全
## Javascript
1. javascript中数据类型有哪些？为什么这么分？
根据数据在内存中存储的数据类型的不同去划分。
分为两大类：
基本类型：undefined、null、boolean、string、number
引用类型：object(function、Array)

2. javascript中的作用域分为几种？有什么好处？
全局作用域、局部作用域。

3. 在javascript中什么是作用域链？

4. 在javascript中什么是闭包？

5. 在javascript中常用string或Array的常用方法？

6. 在javascript中什么是面向对象？为什么要使用面向对象？

7. 常用DOM操作有哪些？

8. DOM节点之间有什么关系？

9. ajax 是什么?ajax 的交互模型?同步和异步的区别?
   1. 通过异步模式，提升了用户体验
   2. 优化了浏览器和服务器之间的传输，减少不必要的数据往返，减少了带宽占用
   3. Ajax在客户端运行，承担了一部分本来由服务器承担的工作，减少了大用户量下的服务器负载

  2. Ajax的最大的特点是什么。
    Ajax可以实现动态不刷新（局部刷新）

  3.ajax的缺点：
      1、ajax不支持浏览器back按钮。
      2、安全问题 AJAX暴露了与服务器交互的细节。
      3、对搜索引擎的支持比较弱。
      4、破坏了程序的异常机制。
      5、不容易调试。

10. HTTP状态码都有那些？
   200 OK      //客户端请求成功
   400 Bad Request  //客户端请求有语法错误，不能被服务器所理解
   403 Forbidden  //服务器收到请求，但是拒绝提供服务
   404 Not Found  //请求资源不存在，输入了错误的URL
   500 Internal Server Error //服务器发生不可预期的错误
   503 Server Unavailable  //服务器当前不能处理客户端的请求，一段时间后可能恢复正常

11. JSON是什么？
   JSON是一种轻量级的数据交换格式。它是基于JS的一个子集。数据格式简单, 易读写, 占用带宽小
