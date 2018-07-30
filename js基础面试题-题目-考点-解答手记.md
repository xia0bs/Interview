# 变量类型和计算

### 题目：
- js中使用typeof能得到哪些类型
- 何时使用 === 何时使用 ==
- js中有哪些内置函数
- js中变量按照存储方式区分为哪些类型，并描述其特点
- 如何理解JSON

### 考点：
#### 值类型vs引用类型

eg.
值类型：
	var a = 100
	''var b = a
	''a = 200
	''console.log(b) 
	//100

引用类型：
	var a = {age:20}
	var b = a
	b.age = 21
	console.log(a.age) 
	//21

#### typeof 运算符详解

typeof undefined //undefined
typeof `'abc'` //string
typeof 123 //bumber
typeof true //boolean
typeof `{}` //object
typeof `[]` //object(array)
typeof null //object
typeof console.log //function

#### 变量计算 - 强制类型转换
- 字符串拼接
	var a = 100 + 10  //110
	var b =100 + '10'  //'10010'
- ==运算符
	100 == '100' //true
	0 == ' ' //true
	null == undefined //true
- if语句
	var a = true 
	if(a){
	//.....
	}
	
	var b =100
	if(b){
	//.....
	}
	
	var c = ' '
	if(c){
	//.....
	}
- 逻辑运算
	console.log(10&&0) //0
	console.log(' '||'abc') //'abc'
	console.log(!window.abc) //true
	
	//判断一个变量会被当做 true 还是 false
	var a = 100
	console.log(!!a)

### 解答：
- js中使用typeof能得到哪些类型？
如上。
- 何时使用 === 何时使用 ==
	if (obj.a==null){
	//这里是相当于obj.a===null || obj.a === undefined，简写形式
	//这是jquery源码中推荐的写法
	}

-  js中有哪些内置函数——数据封装类对象
Object
Array
Boolean
Number
String
Function
Data
RegExp
Error

-  js中变量按照存储方式区分为哪些类型，并描述其特点
1. 值类型（单纯赋值）
2. 引用类型（指针指向）
特点：如上。

-  如何理解JSON
只不过是一个JS对象而已

对象转化成字符串：
	JSON.stringify({a:10,b:20})
字符串转化成对象：
	JSON.parse('{"a":10,"b":20}')

