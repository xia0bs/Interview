# 技术点：

![](https://github.com/xia0bs/Interview/blob/master/exercise/magnifier/屏幕快照%202018-07-09%20下午4.13.47.png)
![](https://github.com/xia0bs/Interview/blob/master/exercise/magnifier/屏幕快照%202018-07-09%20上午11.52.46.png)
 
 # 代码：
 
 ```
 <!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>放大镜</title>
<script src="jquery.js"></script>

<style type="text/css">
* {
margin: 0;
padding: 0
}

#demo {
display: block;
width: 400px;
height: 255px;
margin: 50px;
position: relative;
border: 1px solid #ccc;
}

#small-box {
position: relative;
z-index: 1;
}

#float-box {
display: none;
width: 160px;
height: 120px;
position: absolute;
background: #ffffcc;
border: 1px solid #ccc;
filter: alpha(opacity=50);
opacity: 0.5;
cursor: move;
}

#mark {
position: absolute;
display: block;
width: 400px;
height: 255px;
z-index: 10;
background: #fff;
filter: alpha(opacity=0);
opacity: 0;
cursor: move;
}

#big-box {
display: none;
position: absolute;
top: 0;
left: 460px;
width: 400px;
height: 300px;
overflow: hidden;
border: 1px solid #ccc;
z-index: 1;;
}

#big-box img {
position: absolute;
z-index: 5
}
</style>
<script>
    $(function($){
        let demo = $("#demo")
        let smallBox = $("#small-box")
        let mark = $("#mark")
        let floatBox = $("#float-box")
        let bigBox = $("#big-box")
        let bigBoxImage = $("#big-box img");

        mark.mouseover(function(){
            floatBox.css({display:"block"})
            bigBox.css({display : "block"})
        })

        mark.mouseout(function(){
            floatBox.css({display:"none"})
            bigBox.css({display : "none"})
        })

        mark.mousemove(function(ev){
            let _event = ev || window.event;
            //兼容多个浏览器的event参数模式
            let left = _event.clientX - demo[0].offsetLeft - smallBox[0].offsetLeft - floatBox[0].offsetWidth / 2;
            let top = _event.clientY - demo[0].offsetTop - smallBox[0].offsetTop - floatBox[0].offsetHeight / 2;

            if(left<0){
                left = 0;
            }else if(left>mark[0].offsetWidth - floatBox[0].offsetWidth){
                left = mark[0].offsetWidth - floatBox[0].offsetWidth;
            }
            if(top<0){
                top = 0;
            }else if(top>mark[0].offsetHeight - floatBox[0].offsetHeight){
                top = mark[0].offsetHeight - floatBox[0].offsetHeight;
            }


            let l = left+ "px";
            let t = top + "px";

            floatBox.css({left : l});
            floatBox.css({top : t});

            let percentX = left / (mark[0].offsetWidth - floatBox[0].offsetWidth);
            let percentY = top / (mark[0].offsetHeight - floatBox[0].offsetHeight);

            bigBoxImage[0].style.left = -percentX * (bigBoxImage[0].offsetWidth - bigBox[0].offsetWidth) + "px";
            bigBoxImage[0].style.top = -percentY * (bigBoxImage[0].offsetHeight - bigBox[0].offsetHeight) + "px";

        })

    })
</script>
</head>
<body>
<div id="demo">
<div id="small-box">
<div id="mark"></div>
<div id="float-box"></div>
<img src="http://img.mukewang.com/537d77fb0001559d04000255.jpg"/>
</div>
<div id="big-box">
<img src="http://img.mukewang.com/537d781b0001c04210240654.jpg"/>
</div>
</div>
</body>
</html>
 ```
 
 
