## 一、元素
1. 按照在页面中的呈现效果进行分类
    * 行内元素
        * 特性：在一行内显示，不可以设置宽高。
        * 例如：a b span strong i em del.......
    * 块元素
        * 特性：独占一行，可以设置宽高。
        * 例如：div p pre h1-h6 ul>li(无序) ol>li(有序) dl>dt+dd(项目列表)
    * 行内块元素
        * 特性：在一行内显示，可以设置宽高。
        * 例如：表单控件 img 
2. 元素的转换
    * display:block:让一个元素转变为块元素
        * inline:让一个元素转变为行元素
        * inline-block:一个元素转变为行内块元素
        * none:让一个元素隐藏（浏览器将该元素忽略，不会显示）
3. 元素嵌套的规则
    * 不能交叉嵌套
    * 权重：块元素>行内块元素>行内元素。
    * 同一级别的可以相互嵌套；级别高的可以嵌套级别低的。	
## 二、盒子模型
#### 四个部分构成
1. 外边距：盒子与盒子之间的距离

```
margin缩写：
      margin:40px;
      1个值：表示四周都有40px;(上下左右)
      2个值：上下  左右
      3个值：上  左右  下。
      4个值：上  右  下  左（顺时针方向
```
）
2. 边框：border
3. 内边距：边框与内容之间的距离 padding
* 盒子的实际宽度（高度）：

```
width+border+padding 
设置了padding值以后，需要做减的操作。
 marpin支持负数        padding不支持负数
 margin:0 auto;让块标签在页面中居中（auto：自动）
CSS加样式：box-sizing:border-box   实际宽为width
```
#### 盒子模型的问题：
1. 大部分元素的默认值margin/padding值为0，但是有一些元素的不为0。

```
网页布局开始去掉标签的内外边距，以及一些初始样式
*{
	margin:0px;
	padding:0px;
	list-style:none;
}
a{
	text-decoration: none;
}
img{
	display:block；
}
```

2. * 块标签/行内块标签的外边距四个方向都可以设置
    * 行标签的外边距只能左右起作用，上下无效
3. 相邻的两个块元素，margin值会重合，会取最大值。
4. margin值可以设置负数  padding不支持负数
5. 发生嵌套关系的两个元素，如果父容器没有边框，给子容器设置margin-top时，这个边距会作用到父容器身上。

```
解决方法：
1.给父容器设置一个padding-top来模拟margin-top；
 2.给父容器添加overflow：hidden；
```


##### overflow  对超出父容器的内容设置
1. hidden:将超出的内容隐藏（会在浏览器中占位置）
   display:none（元素不会在浏览器显示）
 2. visible:超出部分永远都显示
 3. auto:浏览器自动判断超出的元素，超出将出现滚动条
 4. scroll:横向与纵向始终出现滚动条
清除滚动条(谷歌浏览器)：.类名::-webkit-scrollBar{
display:none;
   }

### 三、浮动
###### 问题1：
如果父容器没有设置高，并且子容器有浮动属性，结果是父容器没有被撑开。
    
```
解决：
1.给父容器设置：overflow:hidden;
2.清除浮动带来的影响：
  给子元素的最后添加：
      <div style="clear:both"></div>
3.给父容器设置高

clear属性（对有浮动的元素做分组）
         both:左右都不允许有浮动元素
         left:
         right:（视觉上没有任何变化）
         none:不清除浮动
```

###### 问题2：
* 如果父容器过窄，有浮动的子元素会向下移动，如果有浮动的子元素高度不同，在向下移动时，会被卡住。
     只能避免此类问题

## 四、CSS样式的引入以及选择器
#### css的引入方式
1. 行内样式
     
```
style=“属性名:属性值;属性名:属性值;......"
```

2. 嵌入式

```
<style>
    选择器{
        属性名:属性值;属性名:属性值;......  
    }
</style>
位置：页面的任何地方都可以使用，一般情况放在<head>标签对中。
```

3. 外部样式

```
<link rel=“stylesheet" type=“text/css" href=“css文件的地址">
```

4. 导入式

```
@import url(外部样式的地址);
```

#### 选择器
1. 标签选择器
    
```
css:
标签名{
    属性名:属性值;属性名:属性值;......  
}
```

   2. 类名选择器(可以给多个标签添加相同的类名)

```
html:
<div class=“类名”></div>
css:
.类名{
    属性名:属性值;属性名:属性值;...... 
}
```

   3. id选择器（表示唯一存在）

```
html:
<div id=“id名"></div>
css:
#id名{
    属性名:属性值;属性名:属性值;......  
}
```

   4. 通用选择器

```
*{ 属性名:属性值;属性名:属性值;......  }
```

   5. 群组选择器

```
每一个选择器以逗号隔开，一次可以设置多个元素的样式
例：body,p,h1,h2{
        margin:0;
    }
```

   6. 后代选择器

```
父容器 子容器{
    属性名:属性值;属性名:属性值;......
}
```

   7. 交叉选择器 

```
选择器 选择器{
    属性名:属性值;属性名:属性值;......
}
```

   8. 伪类选择器

```
<a></a>链接标签样式
    a:link    未访问的链接
    a:hover   鼠标移动到链接上
    a:active  选定的链接
    a:visited 已访问的链接
```

---   
优先级关系：（谁选择更具体，谁的优先级高）
* 行内样式 > 后代选择器丨交叉选择器 > id > 类名 > 标签 > *
---
9. 子类选择器
   
```
E1>E2｛    ｝选择作为某元素子元素的元素
```

10. 相邻兄弟选择器

11. CSS3结构伪类选择器
* E:first-child{}                        
    * 选择作为第一个子元素的E标签
* E:last-child{}     
    * 选择作为最后一个子元素的E标签
* E:nth-child(arg){}
    * 选择作为第arg个子元素的E标签
    * arg: number odd(奇数) even(偶数)
* E:nth-of-type(arg){}
     * 选择子元素中同类型的第arg个E标签
* E:last-of-type{}
     * 选择子元素中间类型的最后一个E标签
* E:first-of-type{}
     * 选择子元素中间类型的第一个E标签
* E:nth-last-of-type(arg){}
     * 选择子元素中间类型的倒数第arg个E标签
* E:nth-last-child(arg){}
     * 选择作为倒数第arg个子元素的E标签
* p[attr=box-3]{}
     * 选择attr属性为"box-3"的元素
* p[attr~=box-3]{}
     * 选择attr属性包含"box-3"的元素
* P[attr^=b]
    * 选择属性attr中值以b开头的p标签
* P[attr$=x]
    * 选择属性attr中值以x结尾的p标签
* [attr*=o]
    * 选择属性attr中值含有o的标签
12. 伪选择器
* 在元素之后添加内容
    * ::after{  }在元素内容之后添加内容
    * ::before{  }在元素内容之前添加内容



## 文字属性(继承性)

```
font-style: italic;倾斜显示
            normal;按标准显示
            
font-family: 字体

font-weight: bold;加粗
             normal;回到默认样式（不加粗）
             
text-decoration：underline;下划线
                overline;上划线，
                line-through;删除线
                none;去除文本修饰风格
                
text-indent:2em;  首行缩进两个字符（em表示倍数）

text-align: center;   水平居中
            left; 左对齐
            right;右对齐
            justify;两端对齐
            
line-height：数字（px）行高
            1.5em  多行文本的行距
例：让文字水平垂直都居中（块标签内）
    text-align：center;  
    line-height：300px;
vertical-align：middle;垂直居中
                top;   垂直居上
                bottom;垂直居下
                super上标  sub下标
                
文字样式的缩写
    font:bold 12px/20px "宋体";
    属性依次为：字体的粗细 - 字体大小/行高 - 文本的字体
    如果缩写至少要定义 font-size 和font-family两个属性
```

## 背景属性

```
1. 缩写形式
   background:颜色 图片地址 重复方式 位置 随滚动条的移动;（不限制顺序）
2. 背景颜色：
   background-color:颜色：关键字
                    十六进制
                    rgb(0,0,0)
3. 背景图片：background-image:url(图片地址);
4、背景图片的重复方式：
   background-repeat：repeat（平铺，重复出现）;
                      no-repeat(只出现一次);
                      repeat-x(水平方向平铺);
                      repeat-y(竖直方向平铺);
5、背景图片的位置：
   background-position:
            A:center(水平垂直都居中);
              top/left/bottom/right
            B:x,y轴（通过具体的数字来调整位置）
              50px 100px
            C:百分比（x,y轴）
6、背景图片随滚动条变化
   background-attachment:fixed;固定（相对屏幕来定位的）
                         scroll;背景图片随滚动条一起滚动
7、调整背景图片的大小
   background-size:number 宽 高;
                   cover  覆盖盒子
                   contain 图片全部呈现
8、背景图开始渲染的位置
   background-origin:  padding-box;（默认）
                       border-box；
                       content-box；
   背景图结束渲染的位置
   background-clip: border-box（默认）;
```


##### 表单控件
* 取消轮廓  outline:0;
* 光标缩进  text-indent:  px;

##### 投影

```
box-shadow:
1.投影的方向：outside（默认）
              inside
2.x轴上的偏移：数字px
3.y轴上的偏移：数字px
4.投影的模糊：数字px
5.颜色
.shipin-con1:hover{
	box-shadow:0px 10px 20px rgba(0,0,0,0.2);	
}
```

## 定位
###### 1. 相对定位
> 特点：相对于自身去定位。在页面中保留原来的位置
position:relative;
###### 2. 绝对定位
> 特点：相对于最近的、定位的、祖先元素，完全脱离文档流
 position:absolute;
 使用绝对定位，必须对元素设置位置
 left,right,top,bottom
###### 3. 固定定位
> 特点：相对于浏览器定位，完全脱离文档流
position:fixed;
* 定位的元素会多出五个样式：

```
top:;   right:;   bottom:;   left:;  
z-index:;层级（层级越高距离用户越近）
left权重>right  top权重>buttom
定位元素居中
    水平居中：left:0; right:0; margin: 0 auto;
             left:50%;(相对于定位元素width*50%)    margin-left: -width*50%
    垂直居中：top:0; buttom:0; margin: auto 0;
    绝对居中：left:0; right:0;top:0; buttom:0; margin: auto;
```
## CSS3 动画以及渐变

```
过度时间
transition: all 0.4s ease 0s; 
            样式  时间  时间函数  延迟的时间
    transition-property:all;
    transition-duration: 0.5s;
    transition-timing-function: ease;
    transition-delay: 0s;
平移
transform: translateY(-10px);
transform: translate3d(x,y,z);
放大缩小
transform: scale(x,y,);
旋转
transform-origin:left center; 旋转中心
transform: rotate(90deg); 顺时针旋转90°
斜切
transform: skew(45deg,45deg); 
动画
缩写 animation：样式名称 2s ease 0s infinite alternate
    animation-name:样式名称；
    animation-duration:2s; 一次动画持续时间
    animation-timing-function: ease; 动画的时间函数
    animation-delay: 0s; 动画的延迟
    animation-iteration-count: number/infinite; 动画执行的次数几次/一直循环
    animation-direction: alternate ;（逆向）      规定动画第二次运行的方向
 			             normal;（常规 默认）
    animation-fill-mode: forwards;    保持动画后的状态
 			             backwards;  恢复动画前的状态（默认）
    animation-play-state: paused; 暂停   动画执行状态
                          running; 播放
@keyframes 样式名称{
    from{
        开始执行的样式
    }
    to{
        结束执行的动画
    }
}
```

#### 渐变

```
background-image:linear-gradient(to left,red,blue,yellow);
background: -webkit-gradient(linear,0 0,right 0,from(#ca4283),to(#eb75cf));
<linear-gradient>：
使用线性渐变创建背景图像。
<radial-gradient>：
使用径向(放射性)渐变创建背景图像。
<repeating-linear-gradient>：
使用重复的线性渐变创建背景图像。
<repeating-radial-gradient>：
使用重复的径向(放射性)渐变创建背景图像。
```
## 弹性盒子

```
默认的水平方向  主轴         默认的垂直方向  交叉轴
父元素称为 容器              子元素称为 项目
容器的样式
display: flex;
flex-direction: row;
      主轴方向： row (从左到右);
                row-reverse (从右到左);
                column (从上到下);
                column-reverse (从下到上);
flex-wrap: nowrap;  是否换行
           nowrap  不换行
           wrap  换行
           wrap-reverse  换行第一行在下
justify-content:  ;项目在主轴的对齐方式	
                 flex-start  主轴开始位置
                 center      轴中心
                 flex-end   轴结束
                 space-between  两端对齐
                 space-around    平均分配
align-items:  ;交叉轴单行对齐
            flex-start  交叉轴开始位置
            center      交叉轴中心
            flex-end   交叉轴结束
align-content:  ;交叉轴多行对齐方式
            flex-start  主轴开始位置
            center      轴中心
            flex-end   轴结束
            space-between  两端对齐
            space-around    平均分配
```


```
项目的样式
flex-shrink: 1 : 缩放 默认缩放 1
flex-grow: 0 ;   放大 默认为0
flex: flex-shrink flex-grow flex-basis;
align-self: center ;允许项目有不同于其他项目在交叉轴单行的对齐方式
order: num ; 排序数值越小越靠前
```
## 移动端
> 布局视口：浏览器分配出来用于布局的大小。 iphone7 980*
* 视觉视口：屏幕的大小。 iphone7 375*667
* 理想视口：<meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=0">

1. 测试环境
    1. chrome浏览器，只能测试尺寸
    2. wampServer
    3. Hbuilder编译器
2. 适配
* em：当前元素文字的倍率
* rem：跟元素(html)文字的倍率

>响应式布局
* @media screen and (min-width:500px){
}

## 表单
>####  表单标签

标签 |  描述
---|---
<form> | 定义供用户输入的表单
<input>| 定义输入域
<textarea>| 定义文本域 (一个多行的输入控件)
<label> |定义一个控制的标签
<fieldset>| 定义域
<legend> |定义域的标题
<select> |定义一个选择列表
<optgroup>| 定义选项组
<option> |定义下拉列表中的选项
<button> |定义一个按钮

```
<form></form>表单使用表单标签（<form>）定义
文本框：<input type="text" name="zhanghao" value="" size="20" >
密码框：<input type="password" name="mima" value="1234567" size="20" >
label:用户选择该标签时，浏览器就会自动将焦点转到和标签相关的表单控件上 
性别：<input type="radio" name="sex" id="nan"><label for="nan">男</label>
	 <input type="radio" name="sex" id="nv"><label for="nv">女</label>
爱好：<input type="checkbox" name="likes" value="like">跑步
	<input type="checkbox" name="likes" value="like">看书
	<input type="checkbox" name="likes" value="like">打球
文件域： multiple 多选 <input type="file" value="" name="file" multiple> 
<input type="submit" value="提交" name="submit" > 
<input type="reset" value="重置" name="reset" > 
<input type="button" value="按钮" name="button" > 
下拉框：multiple属性表示可以多选，按Ctrl可以多选. 
地点: <select name=""  size="2" multiple>
		<option >太原</option>
		<option>北京</option>
		<option>天津</option>
	</select>
文本区域: <textarea name="" rows="" cols="30" >文本区域</textarea>
```
[http://note.youdao.com/noteshare?id=57ed195cf672c6afa6eb5ecf4da7ec9f&sub=E403562CFBBC4883BAF8CE3753DC17FB](https://note.youdao.com/)



