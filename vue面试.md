### **一. 请谈谈Vue中的MVVM模式**

MVVM全称是Model-View-ViewModel

Vue是以数据为驱动的，Vue自身将DOM和数据进行绑定，一旦创建绑定，DOM和数据将保持同步，每当数据发生变化，DOM会跟着变化。  ViewModel是Vue的核心，它是Vue的一个实例。Vue实例时作用域某个HTML元素上的这个HTML元素可以是body，也可以是某个id所指代的元素。

DOMListeners和DataBindings是实现双向绑定的关键。DOMListeners监听页面所有View层DOM元素的变化，当发生变化，Model层的数据随之变化；DataBindings监听Model层的数据，当数据发生变化，View层的DOM元素随之变化。

------

### **二. v-show和v-if指令的共同点和不同点?**

-  `v-show`指令是通过修改元素的`display`CSS属性让其显示或者隐藏
-  `v-if`指令是直接销毁和重建DOM达到让元素显示和隐藏的效果

------

### **三. 如何让CSS只在当前组件中起作用?**

将当前组件的`<style>`修改为`<style scoped>`

------

### **四. <keep-alive></keep-alive>的作用是什么?**

`<keep-alive></keep-alive>` 包裹动态组件时，会缓存不活动的组件实例,主要用于保留组件状态或避免重新渲染。

### **五. Vue中引入组件的步骤?**

1.采用ES6的`import ... from ...`语法或CommonJS的`require()`方法引入组件
 2.对组件进行注册,代码如下

```
// 注册
Vue.component('my-component', {
  template: '<div>A custom component!</div>'
})
```

3.使用组件`<my-component></my-component>`

------



------

### **七. 在Vue中使用插件的步骤**

1. 采用ES6的`import ... from ...`语法或CommonJSd的`require()`方法引入插件
2. 使用全局方法`Vue.use( plugin )`使用插件

------

### **八. 请列举出3个Vue中常用的生命周期钩子函数?**

1.  **created:** 实例已经创建完成之后调用,在这一步,实例已经完成数据观测, 属性和方法的运算, watch/event事件回调. 然而, 挂载阶段还没有开始, `$el`属性目前还不可见
2.  **mounted:** `el`被新创建的 `vm.$el` 替换，并挂载到实例上去之后调用该钩子。如果 `root` 实例挂载了一个文档内元素，当 mounted 被调用时 `vm.$el` 也在文档内。

------











1、active-class是哪个组件的属性？嵌套路由怎么定义？

答：vue-router模块的router-link组件。

2、怎么定义vue-router的动态路由？怎么获取传过来的动态参数？

答：在router目录下的index.js文件中，对path属性加上/:id。[使用router对象的params.id](https://link.jianshu.com?t=http%3A%2F%2Fxn--routerparams-ov8ss11l264ektes46i.id%2F)

3、vue-router有哪几种导航钩子？

答：三种，一种是全局导航钩子：router.beforeEach(to,from,next)，作用：跳转前进行判断拦截。第二种：组件内的钩子；第三种：单独路由独享组件

 

4、v-model是什么？怎么使用？ vue中标签怎么绑定事件？

答：可以实现双向绑定，指令（v-class、v-for、v-if、v-show、v-on）。vue的model层的data属性。绑定事件：







5、vuex是什么？怎么使用？哪种功能场景使用它？

答：vue框架中状态管理。在main.js引入store，注入。新建了一个目录store，….. export 。场景有：单页应用中，组件之间的状态。音乐播放、登录状态、加入购物车

6、mvvm框架是什么？它和其它框架（jquery）的区别是什么？哪些场景适合？

答：一个model+view+viewModel框架，数据模型model，viewModel连接两个

区别：vue数据驱动，通过数据来显示视图层而不是节点操作。

场景：数据操作比较多的场景，更加便捷

7、说出至少4种vue当中的指令和它的用法？

答：v-if：判断是否隐藏；v-for：数据循环出来；v-bind:class：绑定一个属性；v-model：实现双向绑定

8、vue-router是什么？它有哪些组件？

答：vue用来写路由一个插件。router-link、router-view

9、导航钩子有哪些？它们有哪些参数？

答：导航钩子有：a/全局钩子和组件内独享的钩子。b/beforeRouteEnter、afterEnter、beforeRouterUpdate、beforeRouteLeave

参数：有to（去的那个路由）、from（离开的路由）、next（一定要用这个函数才能去到下一个路由，如果不用就拦截）最常用就这几种

10、Vue的双向数据绑定原理是什么？

答：vue.js 是采用数据劫持结合发布者-订阅者模式的方式，通过Object.defineProperty()来劫持各个属性的setter，getter，在数据变动时发布消息给订阅者，触发相应的监听回调。

具体步骤：

第一步：需要observe的数据对象进行递归遍历，包括子属性对象的属性，都加上 setter和getter 这样的话，给这个对象的某个值赋值，就会触发setter，那么就能监听到了数据变化

第二步：compile解析模板指令，将模板中的变量替换成数据，然后初始化渲染页面视图，并将每个指令对应的节点绑定更新函数，添加监听数据的订阅者，一旦数据有变动，收到通知，更新视图

第三步：Watcher订阅者是Observer和Compile之间通信的桥梁，主要做的事情是:

1、在自身实例化时往属性订阅器(dep)里面添加自己

2、自身必须有一个update()方法

3、待属性变动dep.notice()通知时，能调用自身的update()方法，并触发Compile中绑定的回调，则功成身退。

第四步：MVVM作为数据绑定的入口，整合Observer、Compile和Watcher三者，通过Observer来监听自己的model数据变化，通过Compile来解析编译模板指令，最终利用Watcher搭起Observer和Compile之间的通信桥梁，达到数据变化 -> 视图更新；视图交互变化(input) -> 数据model变更的双向绑定效果。

ps：10题答案同样适合”vue data是怎么实现的？”此面试题。

11、请详细说下你对vue生命周期的理解？

答：总共分为8个阶段创建前/后，载入前/后，更新前/后，销毁前/后。

创建前/后： 在beforeCreated阶段，vue实例的挂载元素$el和数据对象data都为undefined，还未初始化。在created阶段，vue实例的数据对象data有了，$el还没有。

载入前/后：在beforeMount阶段，vue实例的$el和data都初始化了，但还是挂载之前为虚拟的dom节点，data.message还未替换。在mounted阶段，vue实例挂载完成，data.message成功渲染。

更新前/后：当data变化时，会触发beforeUpdate和updated方法。

销毁前/后：在执行destroy方法后，对data的改变不会再触发周期函数，说明此时vue实例已经解除了事件监听以及和dom的绑定，但是dom结构依然存在

12、请说下封装 vue 组件的过程？

答：首先，组件可以提升整个项目的开发效率。能够把页面抽象成多个相对独立的模块，解决了我们传统项目开发：效率低、难维护、复用性等问题。

然后，使用Vue.extend方法创建一个组件，然后使用Vue.component方法注册组件。子组件需要数据，可以在props中接受定义。而子组件修改好数据后，想把数据传递给父组件。可以采用emit方法。



14、vue-loader是什么？使用它的用途有哪些？

答：解析.vue文件的一个加载器，跟template/js/style转换成js模块。

用途：js可以写es6、style样式可以scss或less、template可以加jade等

15、请说出vue.cli项目中src目录每个文件夹和文件的用法？

答：assets文件夹是放静态资源；components是放组件；router是定义路由相关的配置;view视图；app.vue是一个应用主组件；main.js是入口文件

16、vue.cli中怎样使用自定义的组件？有遇到过哪些问题吗？

答：第一步：在components目录新建你的组件文件（smithButton.vue），script一定要export default {

第二步：在需要用的页面（组件）中导入：import smithButton from ‘../components/smithButton.vue’

第三步：注入到vue的子组件的components属性上面,components:{smithButton}

第四步：在template视图view中使用，  问题有：smithButton命名，使用的时候则smith-button。

17、请说下具体使用vue的理解？

答：1、使用vue不必担心布局更改和类名重复导致的js重写，因为它是靠数据驱动双向绑定，底层是通过Object.defineProperty() 定义的数据 set、get 函数原理实现。

2、组件化开发，让项目的可拓展性、移植性更好，代码重用性更高，就好像农民工建房子，拿起自己的工具包就可以开工。项目经理坐等收楼就好。

3、单页应用的体验零距离接触安卓原生应用，局部组件更新界面，让用户体验更快速省时。

4、js的代码无形的规范，团队合作开发代码可阅读性更高。

18、你觉得哪些项目适合vue框架？

答：1、数据信息量比较多的，反之类似企业网站就无需此框架了。

2、手机web和app应用多端共用一套界面的项目，因为使用vue.cli+webpack后的前端目录，非常有利于项目的跨平台部署。

19、怎么理解MVVM模式的这些框架？

答：1、M就是Model模型层，存的一个数据对象。

2、V就是View视图层，所有的html节点在这一层。

3、VM就是ViewModel，它通过data属性连接Model模型层，通过el属性连接View视图层。

20、PC端项目你会在哪些场景使用Vue框架？

答：上万级数据需要瀑布流更新和搜索的时候，因为数据庞大的时候，用原生的dom操作js和html都会有列表的html布局，迭代很困难。再一个dom节点的大面积添加会影响性能。

那么vue为什么解决这些问题呢？

第一：只需用v-for在view层一个地方遍历数据即可，无需复制一段html代码在js和html两个地方。

第二：vue通过Virtual Dom就是在js中模拟DOM对象树来优化DOM操作。



22、ES6常用特性

变量定义(let和const,可变与不可变，const定义对象的特殊情况) 解构赋值 模板字符串 数组新API(例：Array.from(),entries(),values(),keys()) 箭头函数(rest参数，扩展运算符，::绑定this) Set和Map数据结构(set实例成员值唯一存储key值，map实例存储键值对(key-value)) Promise对象(前端异步解决方案进化史，generator函数，async函数) Class语法糖(super关键字)

 

 

 

 

  

 

 

 

 

 

 

 