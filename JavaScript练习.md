>## for循环
>### 实现十行十列的表格,奇数行奇数列、偶数行偶数列不同的背景颜色。
```
	let tab = "<table border='1' cellspacing='0'>";
	for(let i=1;i<=10;i++){  //循环行
		tab += "<tr align='center'>";
		for(let j=1;j<=10;j++){  //循环列
			if(i%2==0 && j%2==0){
				tab += `<td bgcolor='red'>${i}行${j}列</td>`;
			}else if(i%2!=0 && j%2!=0){
				tab += `<td bgcolor='blue'>${i}行${j}列</td>`;
			}else{
				tab += `<td>${i}行${j}列</td>`;
			}
		}
		tab += "</tr>";
	}
	tab += "</table>";
	document.write(tab);
```
>### 背景色为红色的九九乘法表
```
    let cfb ="<table width='600' height='400'>";
	for(let i=1;i<10;i++){
		cfb +="<tr align='center'>";
		for(let j=1;j<=i;j++){
			cfb +=`<td bgcolor='red'>${j}*${i}=${i*j}</td>`;
		}
		cfb +="</tr>";
	}
	cfb +="</table>";
	document.write(cfb);
```
>### 直角三角形
##### 正三角，直角边在左边
```
    let sanjiao1 ="<table>";
	for(let i=1;i<=10;i++){ //循环行
		sanjiao1 +="<tr>";
		for(let j=1;j<=i;j++){ //循环列
			sanjiao1 +="<td>*</td>";
		}
		sanjiao1 +="</tr>"
	}
	sanjiao1 +="</table>";
	document.write(sanjiao1);
```
##### 正三角，直角边在右边
```
    let sanjiao2 ="<table>";
	for(let i=1;i<=10;i++){
		sanjiao2 +="<tr>";
		for(let j=1;j<=10-i;j++){ //循环空格
			sanjiao2 +="<td> </td>";
		}
		for(let j=1;j<=i;j++){
			sanjiao2 +="<td>*</td>";
		}
		sanjiao2 +="</tr>"
	}
	sanjiao2 +="</table>";
	document.write(sanjiao2);
```
```
十行十列，要实现题目要求，前面需要空格填充，先循环每一行的空格，第一行9、之后递减，每一行空格为（10-i）;每一行的*为 i 。
```
##### 倒三角，直角边在左边
```
	let sanjiao3 ="<table>";
	for(let i=1;i<=10;i++){
		sanjiao3 +="<tr>";
		for(let j=1;j<=11-i;j++){
			sanjiao3 +="<td>*</td>";
		}
		sanjiao3 +="</tr>"
	}
	sanjiao3 +="</table>";
	document.write(sanjiao3);
```
```
十行十列，要实现题目要求，第一行10个*，之后依次递减，每一行的*为（10-i+1） 。
```
##### 倒三角，直角边在右边
```
	let sanjiao4 ="<table>";
	for(let i=1;i<=10;i++){
		sanjiao4 +="<tr>";
		for(let j=1;j<=i-1;j++){
			sanjiao4 +="<td> </td>"; //循环空格
		}
		for(let j=1;j<=11-i;j++){
			sanjiao4 +="<td>*</td>";
		}
		sanjiao4 +="</tr>"
	}
	sanjiao4 +="</table>";
	document.write(sanjiao4);
```
```
十行十列，实现题目要求，先循环空格，第一行0个空格，之后每行递增，每行空格为（i-1）；第一行*为10个，之后每行递减，每行*为（10-i+1）。
```
>### 基础练习题
##### 一个四位数，恰好等于去掉它的首位数字之后所剩的三位数的3倍，这个四位数是多少?
```
for(let i=1000;i<10000;i++){
	let num = i%1000;
	if(i/num==3){
		console.log("这个四位数是："+i);
	}
}
```
##### 有一个两位数，如果在它的前面添一个3，可得到一个三位数；把3添在它的后面，也可以得到一个三位数。这两个三位数相差468，求原来的两位数。
```
for(let i=10;i<100;i++){
	let num1 = i+300;
	let num2 = i*10+3;
	if(num1-num2==468 ||num1-num2==-468){
		console.log(i);
	}
}
```
##### 一个六位自然数，将其末位上数字7移至首位，其余数字依次向右移动一位，得到一个新的六位数，新的六位数是原六位数的4倍，求原数。
```
	for(let i=100000;i<1000000;i++){
		let num = (i-7)/10+700000;
		if(num/i==4){
			console.log(i);
		}
	}
```
##### 笼子里有鸡兔共34只，共有96只脚，鸡兔各有几只？
```
	for(let a=0;a<=34;a++){
		for(let b=0;b<=24;b++){
			if(a+b==34 && a*2+b*4==96){
				document.write("有"+a+"只鸡，"+"有"+b+"只兔子");
			}
		}
	}
```
```
a为鸡，b为兔子，共有34只，限制鸡、兔子的个数都<=34;共有96只脚，限制兔子的个数<=24。两个条件与的关系，if判断，符合条件的输出。
```
##### 参考书单价10元，笔记本单价5元，练习本单价0.5元，一共花了100元买了100本，参考书、笔记本、练习本各买了几本？
```
	for(let a=0;a<=10;a++){
		for(let b=0;b<=20;b++){
			for(let c=0;c<=100;c++){
				if(a*10+b*5+c*0.5==100&&a+b+c==100){
					document.write("参考书"+a+"本，"+"笔记本"+b+"本，"+"练习本"+c+"本");
				}
			}
		}
	}
```
```
通过价格和一共的本数限制参考书<=10、笔记本<=20、练习本<=100;两个条件与的关系，if判断，符合条件的输出。
```
##### 操场上100多人排队，三人一组多1人，四人一组多2人，五人一组多3人，共多少人?
```
	for(let a=100;a<200;a++){
		if(a%3==1 && a%4==2 && a%5==3){
			document.write("操场上共有"+a+"个人");
		}
	}
```
```
一共一百多人，人数应该>=100 且 <200;由三个条件人数取余，三条件与的关系，if判断，符合条件的输出。
```

>## 函数
>### 闭包
##### 一个函数fn嵌套一个函数fn1，当嵌套的函数fn1被外部的一个变量引用时，就形成了闭包。
##### 作用：可以在外部访问变量     将局部变量保存在作用域链上
```
    function fn(){
     	let aa = 123;
     	return function fn1(){
     		console.log(aa);
     	}
    }
    let fn1 = fn();
    fn1();//123
```
```
    function aa(){
    	let i=10;
    	function bb(){
    		return ++i;
    	}
    	return bb; 
    }
    let c = aa();
    alert(c());//11
```
>### 递归（求阶乘）
##### 一个函数再次调用这个函数
```
    function jc(num){
    	if(num==1){
    		return 1;
    	}
    	return num * jc(num-1);
    }
    console.log(jc(10));//10的阶乘
```
```
例如10的阶乘，10！= 10 * (10-1)!;
              9！= 9  * (9 -1)!;
              ......
              2! = 2  * (2 -1)!;
              1! = 1;
    对一个函数的循环调用
```
>### 回调（四则运算）
##### 通过函数的指针来调用函数。
##### – 把一个函数的指针做为另一个函数的参数，当调用这个参数的时候，这个函数就叫做回调函数
```
    function demo(a,b,c){
    	return c(a,b);
    }
    function jia(a,b){ //加
    	return a+b;
    }
    function jian(a,b){ //减
    	return a-b;
    }
    function sheng(a,b){ //乘
    	return a*b;
    }
    function chu(a,b){ //除
    	return a/b;
    }
    alert(demo(4,5,sheng));
```

>## 数组
>### 数组的遍历
#### 二维数组的遍历
```
    let arrAr = [1,1,2,3,[4,5]];
	for(i in arrAr){
		if(typeof arrAr[i]=="object"){
			for(j in arrAr[i]){
				console.log(arrAr[i][j]);
			}
		}else{
			console.log(arrAr[i]);
		}
	}
```
#### 多维数组的遍历（递归）
```
	let arrDuo = [1,1,[8,6],3,[54,[12,3],66],5];
	function bl(arr){
		for(i in arr){
			if(typeof arr[i]=="object"){
				bl(arr[i]);
			}else{
				console.log(arr[i]);
			}
		}
	}
	bl(arrDuo);
```
>### 数组的拷贝
#### 数组的浅拷贝
```
    let arrA=[1,2,3,45];
	let arrB=arrA;
	arrB[0]=0;
	console.log(arrB);//[0,2,3,45]
	console.log(arrA);//[0,2,3,45]
浅拷贝
	let arrC=[1,2,3,45];
	let arrD=[];
	for(i in arrC){
		arrD[i] = arrC[i];
	}
	arrD[0]=0;
	console.log(arrD);//[0,2,3,45]
	console.log(arrC);//[1,2,3,45]
```
#### 数组的深拷贝
```
    let arrShen = [1,1,[8,6],3,[54,[12,3],66],5];
	let arrNew = [];
	function skb(arrShen,arrNew){
		for(i in arrShen){
			if(typeof arrShen[i]=="object"){
				arrNew[i]= [];
				skb(arrShen[i],arrNew[i]);
			}else{
				arrNew[i]=arrShen[i];	
			}
		}
	}
	skb(arrShen,arrNew);
	console.log(arrShen);
	console.log(arrNew);
```
>### 获取数组里面的最大值
```
	let arr = [2,33,4,5,1,55,1];
	function arrMax(arr){
		let max = arr[0];
		for(i in arr){
			if(arr[i]>max){
				max = arr[i];
			}
		}
		console.log(max);
	}
	arrMax(arr);
```
>### 删除数组里面的空值
```
    let arr = [2,3,,4,,"a",,6];
	let newArr = [];
	function qukong(arr){
		let j =0;
		for(i in arr){
			if(arr[i]!=undefined){
				newArr[j] = arr[i];
				j++;
			}
		}
		console.log(newArr);
	}
	qukong(arr);
```
```
声明一个新数组，遍历旧数组，根据如果为空返回的是undefined，把判断不为undefined的元素拷贝给新的数组。
```
>### 连接两个数组
```
    let arr1 = [1,2,3];
	let arr2 = [4,5,6];
	let newArr = [];
	function concat(arr1,arr2){
		let index = 0;
		for(i in arr1){
			newArr[index]=arr1[i];
			index++;
		}
		for(i in arr2){
			newArr[index]=arr2[i];
			index++;
		}
		console.log(newArr); //[1,2,3,4,5,6]
	}
	concat(arr1,arr2);
```
>###  删除数组的首位元素
```
    let arr = [1,2,3];
	let newArr = [];
	function shift(arr){
		let index =0;
		for(let i=1;i<arr.length;i++){
			newArr[index]=arr[i];
			index++;
		}
		console.log(newArr); //[2,3]
	} 
	shift(arr);
```
>### 在数组的首位添加一个元素
```
	let arr = [1,2,3];
	let newArr = [];
	function unshift(arr,item){
		newArr[0]=item;
		let index = 1;
		for(i in arr){
			newArr[index]=arr[i];
			index++;
		}
		console.log(newArr);
	}
	unshift(arr,0);
```
>### 在数组的首位添加多个元素
```
    let arr = [1,2,3];
	function unshift(arr,...item){
		let newArr = item;
		let index = item.length;
		for(i in arr){
			newArr[index]=arr[i];
			index++;
		}
		console.log(newArr);
	}
	unshift(arr,0,0,0,0);
```
>### 向数组的末位添加一个元素
```
	let arr = [1,2,3];
	function push(arr,item){
		let newArr = [];
		for(i in arr){
			newArr[i]=arr[i];
		}
		newArr[arr.length]=item;
		console.log(newArr);
	}
	push(arr,4);
```
>### 删除数组的末位元素
```
	let arr = [1,2,3];
	function pop(arr){
		let newArr = [];
		for(let i=0;i<(arr.length-1);i++){
			newArr[i]=arr[i];
		}
		console.log(newArr);
	}
	pop(arr);
```
>### 数组倒序排列
```
	let arr = [1,2,3,4];
	function reverse(arr){
		let newArr = [];
		let index = arr.length-1 ;
		for(i in arr){
			newArr[index]=arr[i];
			index--;
		}
		console.log(newArr);
	}
	reverse(arr);
```
>### 数组的排序
#### 冒泡排序
```
	let arr=[3,2,6,1,7,9];
	function paixu(arr){
		for(var i=0;i<arr.length-1;i++){ 
			for(var j=0;j<arr.length-1-i;j++){ 
				if(arr[j]>arr[j+1]){ 
					var paixu;
					paixu=arr[j];
					arr[j]=arr[j+1];
					arr[j+1]=paixu;
				}			
			}
		}
		console.log(arr);
	}
	paixu(arr);
```
#### 顺序排序
```
	let arr=[3,2,6,1,7,9];
	function paixu(arr,b){
		for(var i=0;i<arr.length-1;i++){ //遍历数组以后，拿数组的每一个元素参与比较
			for(var j=i+1;j<arr.length;j++){ //从i的下一个元素开始遍历，拿出一个元素参与比较；里层的for循环循环完一次，就找出一个最大值。
				if(b==">"){
					if(arr[i]<arr[j]){ //当i的当前元素比j的当前元素小，就让他两交换位置
						var paixu;
						paixu=arr[i];
						arr[i]=arr[j];
						arr[j]=paixu;
					}	
				}else if(b=="<"){
					if(arr[i]>arr[j]){
						var paixu;
						paixu=arr[i];
						arr[i]=arr[j];
						arr[j]=paixu;
					}
				}		
			}
		}
		console.log(arr);
	}
	paixu(arr,">");
```
