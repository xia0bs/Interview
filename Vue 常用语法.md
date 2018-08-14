#### Vue 获取后台数据，组件
```
  import FecHeader from '../common/FecHeader';
  import FecFooter from '../common/FecFooter';
  export default {
      name: 'Index',
      components: {FecHeader,FecFooter},
      component:{'fec-header':FecHeader},
      component:{'fec-footer':FecFooter},
      data(){
          return{}
      },
      mounted(){
        fetch('/general/base/menu')
            .then(res => res.json())
            .then(data => {
                console.log(data)
                this.msg = data;
            })
    }
  }
```
#### Vue的虚拟dom？
```
虚拟的DOM的核心思想是：对复杂的文档DOM结构，提供一种方便的工具，进行最小化地DOM操作。
```
#### 请详细说下你对vue生命周期的理解？
```
总共分为8个阶段创建前/后，载入前/后，更新前/后，销毁前/后。

创建前/后： 在beforeCreated阶段，vue实例的挂载元素$el和数据对象data都为undefined，还未初始化。在created阶段，vue实例的数据对象data有了，$el还没有。

载入前/后：在beforeMount阶段，vue实例的$el和data都初始化了，但还是挂载之前为虚拟的dom节点，data.message还未替换。在mounted阶段，vue实例挂载完成，data.message成功渲染。

更新前/后：当data变化时，会触发beforeUpdate和updated方法。

销毁前/后：在执行destroy方法后，对data的改变不会再触发周期函数，说明此时vue实例已经解除了事件监听以及和dom的绑定，但是dom结构依然存在
```
#### Vue 双向数据绑定原理
`
响应式系统是如何做到 UI(View)与状态(Modal)同步的
`
```
vue.js 是采用数据劫持结合发布者-订阅者模式的方式，通过Object.defineProperty()来劫持各个属性的setter，getter，在数据变动时发布消息给订阅者，触发相应的监听回调。

具体步骤：

第一步：需要observe的数据对象进行递归遍历，包括子属性对象的属性，都加上 setter和getter
这样的话，给这个对象的某个值赋值，就会触发setter，那么就能监听到了数据变化

第二步：compile解析模板指令，将模板中的变量替换成数据，然后初始化渲染页面视图，并将每个指令对应的节点绑定更新函数，添加监听数据的订阅者，一旦数据有变动，收到通知，更新视图

第三步：Watcher订阅者是Observer和Compile之间通信的桥梁，主要做的事情是:
1、在自身实例化时往属性订阅器(dep)里面添加自己
2、自身必须有一个update()方法
3、待属性变动dep.notice()通知时，能调用自身的update()方法，并触发Compile中绑定的回调，则功成身退。

第四步：MVVM作为数据绑定的入口，整合Observer、Compile和Watcher三者，通过Observer来监听自己的model数据变化，通过Compile来解析编译模板指令，最终利用Watcher搭起Observer和Compile之间的通信桥梁，达到数据变化 -> 视图更新；视图交互变化(input) -> 数据model变更的双向绑定效果。
```
####  请说出vue.cli项目中src目录每个文件夹和文件的用法？
```
答：assets文件夹是放静态资源；components是放组件；router是定义路由相关的配置;view视图；app.vue是一个应用主组件；main.js是入口文件
```
#### Vue 路由问题

vue-router模块的router-link组件

在router目录下的index.js文件中
```
import Router from 'vue-router'
对path属性加上/:id
export default new Router({
  routes: [
      {
          path: '/show/:id',
          name: 'Show',
          component: Show
      },
      {
          path: '/user/:id',
          name: 'User',
          component: User,
          children:[
              {
                 path:"profile",component:UserProfile
              },
              {
                  path:"collect",component:UserCollect
              }
          ]
      }
  ]
})
使用router对象的params.id
```
#### vue-router有哪几种导航钩子？  
```
第一种：是全局导航钩子：router.beforeEach(to,from,next)，作用：跳转前进行判断拦截。
第二种：组件内的钩子；
第三种：单独路由独享组件
```
#### axios是什么？怎么使用？描述使用它实现登录功能的流程？
```
请求后台资源的模块
npm install axios-S装好，然后发送的是跨域，需在配置文件中config/index.js进行设置。
在登录页面的<script>标签中使用import进来，然后.get或.post。返回在.then函数中如果成功，失败则是在.catch函数中
```
#### vuex是什么？怎么使用？哪种功能场景使用它？
```
vue框架中状态管理。在main.js引入store，注入。新建了一个目录store，….. export 。场景有：单页应用中，组件之间的状态。音乐播放、登录状态、加入购物车
```
#### mvvm框架是什么？它和其它框架（jquery）的区别是什么？哪些场景适合？
```
Model 层代表数据模型，也可以在Model中定义数据修改和操作的业务逻辑；View 代表UI 组件，它负责将数据模型转化成UI 展现出来，ViewModel 是一个同步View 和 Model的对象
区别：vue数据驱动，通过数据来显示视图层而不是节点操作。
场景：数据操作比较多的场景，更加便捷
```