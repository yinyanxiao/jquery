## jquery 知识点和案例

### 选择器 $()

### 方法 css()、index()、attr()、text()、val()
 
### 1、css改变样式
```html
$(".box").css("background-color","red")
```
### 2、attr改变属性
```html
$(".pic").attr("src","image/1.jpg")
```
### 3、index获取索引
```html
var index = $(this).index();
```
### 4、text设置文本节点及获取文本节点
+ 设置文本节点
```html
<h1></h1>
var txt = $("h1").text("你好")
```
+获取文本节点
```html
<h1>你好</h1>
var txt = $("h1").text()
```
### 5、val设置属性节点及获取属性节点
+ 获取属性节点
```html
<input type="text" value="你好" class="txt">
var val = $(".txt").val();
```
+ 设置属性节点
```html
<input type="text"  class="txt">
var val = $(".txt").val("你好");
```
### 获取节点
+ eq(通过索引找元素)
+ siblings(同级中的其他元素)
+ parent(父级)
+ find(子孙级)

### 事件
+ click
+ mouseenter
+ mouseover
+ mouseleave
+ mouseout
+ mousemove

### 6、eq通过索引找元素
```html
$("#myForm input").click(function(){
	var ind = $(this).index();
	$(".box div").eq(ind).css("background-color","red")
})
```
### 7、图片切换
```html
$("#num-list li").click(function(){
	var index = $(this).index();
	var src = "images/" + index + ".jpg";
	$("#pic").attr("src",src);
	$(this).addClass("active").siblings().removeClass("active")
})
```
### 8、选项卡
```html
<body>
	<div class="one"> 
		<ul class="clearFixki">
		<li>标题一</li>
		<li>标题二</li>
		<li>标题三</li>
	</ul>
	</div>
	
	<div class="two">//必须大盒子
		<div class="box1">盒子一</div>
		<div class="box">盒子二</div>
		<div class="box">盒子三</div>
	</div>
	
	<script src="jquery.js"></script>
	<script>
		$(".one ul li").click(function(){
			var ind = $(this).index();
			$(".two div").eq(ind).css("display","block").siblings().css("display","none")
		})
	</script>
</body>
</html>		
```	
### 9、下拉菜单
+ 方法：find()找到它的子孙级、mouseenter()、mouseleave()
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style type="text/css">
	*{
		margin:0;
		padding:0;
	}
	.listAll>li{
		height: 30px;
		line-height: 30px;
		width: 50px;
		text-align: center;
		list-style: none;
		float: left;
		border:1px solid red;
	}
	.list li{
		list-style: none;
		display: none;
	}
	</style>
</head>
<body>
	<ul class="listAll">
		<li>
			<a href="">图书</a>
			<ul class="list">
				<li>图书一</li>
				<li>图书一</li>
				<li>图书一</li>
			</ul>
		</li>
		<li>
			<a href="">图书</a>
			<ul class="list">
				<li>图书二</li>
				<li>图书二</li>
				<li>图书二</li>
			</ul>
		</li>
		<li>
			<a href="">图书</a>
			<ul class="list">
				<li>图书三</li>
				<li>图书三</li>
				<li>图书三</li>
			</ul>
		</li>
	</ul>
	<script src="jquery.js"></script>
	<script>
		$(".listAll>li").mouseenter(function(){
			$(this).find(".list li").slideDown(3000);
		}).mouseleave(function(){
			$(this).find(".list li").slideUp(3000);
		})
	</script>
</body>
</html>		
```	
### 10、点击事件
+ 事件：和浏览器发生交互时，浏览器反馈给你信息，整个过程叫事件。
```html
$(".box").click(function(){
	$(this).css("background-color","blue");
});
```
### 11、jquery动画
+ ** 方法：** show()、hide()、fadeIn(渐入)、fadeOut(渐出)、slideDown(下拉)、slideUp(上拉)、toggle(显示和隐藏)、slideToggle(切换上卷和下拉)、animate(自定义动画)
```html
$("#show").click(function(){
	$(".box").show(500);
})
$("#hide").click(function(){
	$(".box").hide(500);
})
$("#fadeIn").click(function(){
	$(".box").fadeIn(5000);
})
$("#fadeOut").click(function(){
	$(".box").fadeOut(5000);
})
$("#slideDown").click(function(){
	$(".box").slideDown(5000);
})
$("#slideUp").click(function(){
	$(".box").slideUp(5000);
})
$("#toggle").click(function(){
	$(".box").toggle(5000);
})
$("#fadeToggle").click(function(){
	$(".box").fadeToggle(5000);
})
$("#slideToggle").click(function(){
	$(".box").slideToggle(5000);
})
$("#animate").click(function(){
	$(".box").animate({"margin-top":"100px","margin-left":"100px"},5000)
})
```

### 12、导航滚动
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
	*{
		margin:0px;
		padding:0px;
	}
	.nav li{
		width:70px;
		height:30px;
		border:1px solid blue;
		margin-top:50px;
		float:left;
		list-style:none;
		overflow:hidden;
	}
	.nav li a{
		display: block;
		width:70px;
		height:30px;
		text-align:center;
		line-height: 30px;
		background-color:red;
	}
	.nav li span{
		display: block;
		width:70px;
		height:30px;
		text-align:center;
		line-height: 30px;
		background-color:yellow;
	}
	</style>
</head>
<body>
	<ul class="nav">
		<li>
			<div>
				<a href="">网页</a>
				<span>链接</span>
			</div>
		</li>
		<li>
			<div>
				<a href="">网页</a>
				<span>链接</span>
			</div>
		</li>
		<li>
			<div><a href="">网页</a>
				<span>链接</span>
			</div>
		</li>
	</ul>
	<script src="jquery.js"></script>
	<script>

	$(".nav li").mouseenter(function(){
		$(this).find("div").animate({"margin-top":"-30px"},5000);
	}).mouseleave(function(){
		$(this).find("div").animate({"margin-top":"0px"},5000);
	})
</script>
</body>
</html>
```
### 13、图片轮播
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style type="text/css">
		*{
			margin:0px;
			padding:0px;
		}
		#pic-box{
			width: 650px;
			height: 420px;
			overflow: hidden;
		}
		#pic-box ul{
			width: 3250px;
		}
		#pic-box ul li{
			float: left;
		}
		#num-list li{
			list-style: none;
			float: left;
			width:20px;
			height:20px;
			border:1px solid #aaa;
			text-align: center;
			line-height: 20px;
			cursor: pointer;
		}
	</style>
</head>
<body>
	<div id="pic-box">
		<ul>
			<li><img src="images/0.jpg" alt=""></li>
			<li><img src="images/1.jpg" alt=""></li>
			<li><img src="images/2.jpg" alt=""></li>
			<li><img src="images/3.jpg" alt=""></li>
			<li><img src="images/4.jpg" alt=""></li>
		</ul>
	</div>
	<ul id="num-list">
		<li>1</li>
		<li>2</li>
		<li>3</li>
		<li>4</li>
		<li>5</li>
	</ul>
	<script src="script/jquery.js"></script>
	<script>
		$("#num-list li").click(function(){
			var index = $(this).index();
			var marLeft = index * -650;
			$("#pic-box ul").animate({marginLeft:marLeft},5000);
		})

	</script>
</body>
</html>
```
### 14、添加节点
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<form action="">
		<input type="text" id="txt">
		<input type="button" id="btn" value="添加">
	</form>
	<ul id="list">
		<li>香蕉</li>
		<li class="apple">苹果</li>
		<li>鸭梨</li>
	</ul>	
	<script src="script/jquery.js"></script>
	<script>
		$("#btn").click(function(){
			var value = $("#txt").val();
			var li = "<li>" + value + "</li>";
			$("#list").append(li);/*在li后面添加一条*/
			$("#list").prepend(li);/*在li前面添加一条*/
			$(".apple").before(li);
			$(".apple").after(li);
		})
	</script>	
</body>
</html>
```
### 删除节点
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<form action="">
		<input type="text" id="txt">
		<input type="button" id="btn" value="添加">
	</form>
	<ul id="list">
		<li>香蕉 <span>删除</span></li>
		<li>苹果 <span>删除</span></li>
		<li>鸭梨 <span>删除</span></li>
		<li>芒果 <span>删除</span></li>
		<li>草莓 <span>删除</span></li>
	</ul>
	<script src="script/jquery.js"></script>
	<script>
		$("#list li span").click(function(){
			$(this).parent().remove();
		})
	</script>
</body>
</html>
```
获取鼠标坐标
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style type="text/css">
		.box{
			height:500px;
			width: 500px;
			border:1px solid red;
		}
	</style>
</head>
<body>
	<div class="box"></div>
	<h1 class="x">横坐标：<span></span></h1>
	<h1 class="y">纵坐标：<span></span></h1>
	<script src="script/jquery.js"></script>
	<script>
		$(".box").mousemove(function(event){
			var x = event.pageX;
			var y = event.pageY;
			$(".x span").text(x);
			$(".y span").text(y);
		})
	</script>
</body>
</html>
```
### 11、获取鼠标坐标应用
```html

```





	








	


