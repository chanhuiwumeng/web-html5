# JQuery

> jQuery is a fast, small, and feature-rich JavaScript library. It makes things like HTML document traversal and manipulation, event handling, animation, and Ajax much simpler with an easy-to-use API that works across a multitude of browsers. With a combination of versatility and extensibility, jQuery has changed the way that millions of people write JavaScript.

![image-20210224104338061](_media/image-20210224104338061.png)

## 1. 下载jquery库

![image-20210224111304765](_media/image-20210224111304765.png)

![image-20210224111327424](_media/image-20210224111327424.png)

![image-20210224111412164](_media/image-20210224111412164.png)

## 2. JQuery初体验

### 2.1 Jquery初体验

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>jquery初体验</title>
	</head>
	<body>
		<button>点击一下</button>
		<script src="js/jquery-3.1.1.min.js"></script>
		<script>
			// 通过jquery获取到的是jquery对象  document获取到的是dom对象
			/* let btn = $("button");
			console.log(btn); */
			window.onload = ()=>{
				// js代码
			}
			//页面加载完成以后  回调函数
			/* $(document).ready(function(){
				console.log("----------");
			}) */
			/* 最终也页面加载完成写法简化 */
			$(function(){
				console.log("ready OK!");
			})
			/* es6jquery的写法简单 */
			$(()=>{
				console.log("es6----");
			})
		</script>
	</body>
</html>

```

### 2.2 JQuery核心

#### 2.2.1 Jquey对象和DOM对象互转 和 each

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>核心</title>
		<style>
			div{
				width: 300px;
				height: 300px;
				background: lawngreen;
			}
		</style>
	</head>
	<body>
		<div>
			
		</div>
		
		<ul>
			<li>Hello</li>
			<li>Hello</li>
			<li>Hello</li>
			<li>Hello</li>
			<li>Hello</li>
		</ul>	
		
		<script src="js/jquery-3.1.1.min.js"></script>
		<script>
			$(function(){
				//获取页面的元素 $("css选择器")
				//jquery对象 和 dom 对象转换
				let div = 	$("div");
				/* jquery对象转为dom对象 */
				console.log(div.get(0));
				console.log(div[0]);
				//div.get(0).appendChild();
				/* dom对象转为jquery对象 */
				let main = document.querySelector("div");
				console.log($(main));
				/* 将dom对象转为jquery对象 */
				let p = $("<p></p>");
				console.log(p);
				
				/* each遍历数组 */
				let arr = [1,2,3,4,5,6,7];
				/* arr.forEach((i)=>{
					console.log(i);
				}) */
				/* index是下标 item是下标对应的值 */
				$.each(arr,function(index,item){
					console.log("下标:"+index);
					console.log(item);
				})
				/* arr不是jquery对象 */
				$(arr).each(function(index,item){
					console.log(index);
					console.log("值:"+item);
				})
				/* 获取所有的li标签 */
				let lis = $("li");
				console.log(lis);
				lis.each(function(index,item){
					console.log(index + "="+ item);
				})
			})
		</script>
	</body>
</html>

```

#### 2.2.2 选择器



