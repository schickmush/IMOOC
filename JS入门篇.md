## JavaScript入门篇 ##
[课程链接：JavaSript入门篇](https://www.imooc.com/learn/36)
### 第一章 入门 ###
- 如何插入JS
	- 使用 `<script>` 标签在HTML网页中插入JavaScript代码
	- 引用JS外部文件
		把HTML文件和JS代码分开，并单独创建一个JavaScript文件，其文件后缀通常为.js，然后将JS代码直接写在JS文件中。
		```javascript
		<script src="script.js"></script>
		```
- JS在页面中的位置
	- 我们可以将JavaScript代码放在html文件中任何位置，一般放在网页的head或者body部分。
	- 放在`<head>部分`：最常用的方式是在页面中head部分放置`<script>`元素，浏览器解析head部分就会执行这个代码，然后才解析页面的其余部分。
	- 放在`<body>`部分：JavaScript代码在网页读取到该语句的时候就会执行。
- 注释
	- 单行注释，在注释内容前加符号 `//`
	- 多行注释以`/*`开始，以`*/`结束
- 定义变量
	- 变量必须使用字母、下划线(_)或者美元符($)开始。
	- 然后可以使用任意多个英文字母、数字、下划线(_)或者美元符($)组成。
	- 不能使用JavaScript关键词与JavaScript保留字，JS区分大小写
	- 语句：var 变量名,变量要先声明再赋值，如下：
		```javascript
		var mychar;
		mychar="javascript";
		var mynum = 6;
		```
- 判断语句（if...else）
	```javascript
	<script type="text/javascript">
	   var myage = 18;
	   if(myage>=18)  //myage>=18是判断条件
	   { document.write("你是成年人。");}
	   else  //否则年龄小于18
	   { document.write("未满18岁，你不是成年人。");}
	</script>
	```
- 函数
	- 定义函数
		```javascript
		function 函数名()
		{
		     函数代码;
		}		
		```
	- 调用函数
		```javascript
		<!DOCTYPE HTML>
		<html>
		<head>
		<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
		<title>函数调用</title>
		   <script type="text/javascript">
		      function contxt() //定义函数
		      {
		         alert("哈哈，调用函数了!");
		      }
		   </script>
		</head>
		<body>
		   <form>
		      <input type="button"  value="点击我" onclick="contxt()" />  
		   </form>
		</body>
		</html> 
		```

### 第二章 常用互动方法 ###
- 输出内容
	- 输出内容用""括起，直接输出""号内的内容。
		```javascript
		<script type="text/javascript">
		  document.write("I love JavaScript！"); //内容用""括起来
		</script>
		```
	- 通过变量，输出内容
		```javascript
		<script type="text/javascript">
		  var mystr="hello world!";
		  document.write(mystr);  //直接写变量名，输出变量存储的内容。
		</script>
		```
	- 输出多项内容，内容之间用+号连接
		```javascript
		<script type="text/javascript">
			var mystr="hello";
			document.write(mystr+"I love JavaScript");  //多项内容之间用+号连接
		</script>
		```
- 警告（alert 消息对话框）：弹出一个小窗口（只有确定按钮）
	```javascript
	alert(str);
	```
- 确认（confirm 消息对话框）：弹出对话框(包括一个确定按钮和一个取消按钮)。
	当用户点击"确定"按钮时，返回true
	当用户点击"取消"按钮时，返回false
	```
	confirm(str);
	```
	```javascript
	<script type="text/javascript">
	    var mymessage=confirm("你喜欢JavaScript吗?");
	    if(mymessage==true)
	    {   document.write("很好,加油!");   }
	    else
	    {  document.write("JS功能强大，要学习噢!");   }
	</script>
	```
- 提问（prompt 消息对话框）：弹出消息对话框（包含一个确定按钮、取消按钮与文本输入框）
	str1: 要显示在消息对话框中的文本，不可修改
	str2：文本框中的内容，可以修改
	```javascript
	prompt(str1, str2);
	```
	```
	var myname=prompt("请输入你的姓名:");
	if(myname!=null)
	  {   alert("你好"+myname); }
	else
	  {  alert("你好 my friend.");  }
	```
- 打开新窗口（window.open）
	```
	window.open([URL], [窗口名称], [参数字符串])
	```
	```
	<script type="text/javascript"> 
	window.open('http://www.imooc.com','_blank','width=300,
	height=200,menubar=no,toolbar=no, status=no,scrollbars=yes')
	</script>
	```
	- URL：可选参数，在窗口中要显示网页的网址或路径。如果省略这个参数，或者它的值是空字符串，那么窗口就不显示任何文档。
	- 窗口名称：可选参数，被打开窗口的名称。由字母、数字和下划线字符组成。
		```
		_blank：在新窗口显示目标网页
       _self：在当前窗口显示目标网页
       _top：框架网页中在上部窗口中显示目标网页
		```
	- 参数字符串：可选参数，设置窗口参数，各参数用逗号隔开。
		```
		top：number,窗口顶部离屏幕顶部的像素数
		left：number,窗口左端离屏幕左端的像素数
		width：number,窗口宽度
		height：number,窗口高度
		menubar：yes or no,窗口有没有菜单
		toolbar：yes or no,窗口有没有工具条
		scrollbars：yes or no,窗口有没有滚动条
		status：yes or no,窗口有没有状态栏
		```
- 关闭窗口（window.close）
	```
	window.close();   //关闭本窗口
	<窗口对象>.close();   //关闭指定的窗口
	```
	```
	<script type="text/javascript">
	   var mywin=window.open('http://www.imooc.com'); 
	   //将新打的窗口对象，存储在变量mywin中
	   mywin.close();
	</script>
	```

### 第三章 DOM操作 ###
- 文档对象模型DOM（Document Object Model）：定义访问和处理HTML文档的标准方法。DOM 将HTML文档呈现为带有元素、属性和文本的树结构（节点树）。
- 三种常见的DOM节点:
	- 元素节点：上图中`<html>`、`<body>`、`<p>`等都是元素节点，即标签。
	- 文本节点:向用户展示的内容，如`<li>...</li>`中的JavaScript、DOM、CSS等文本。
	- 属性节点:元素属性，如`<a>`标签的链接属性href="http://www.imooc.com"。
	```
	<a href="http://www.imooc.com">JavaScript DOM</a>
	```
- 通过ID获取元素
	```
	document.getElementById(“id”) 
	```
	```
	<p id="con">JavaScript</p>
	<script type="text/javascript">
	  var mychar=document.getElementById("con").innerHTML;
	  document.write("结果:"+mychar); //输出获取的p的文本。 
	</script>
	```
	结果：JavaScript

	```
	<p id="con">JavaScript</p>
	<script type="text/javascript">
	  var mychar=document.getElementById("con");
	  document.write("结果:"+mychar); //输出获取的p的文本。 
	</script>
	```	
	结果：[object HTMLParagraphElement]
- innerHTML 属性：用于获取或替换 HTML 元素的内容
	```
	<body>
	<h2 id="con">javascript</H2>
	<script type="text/javascript">
	  var mychar= document.getElementById("con");
	  document.write("原标题:"+mychar.innerHTML+"<br>"); //输出原h2标签内容
	  mychar.innerHTML="Hello world!"
	  document.write("修改后的标题:"+mychar.innerHTML); //输出修改后h2标签内容
	</script>
	</body>
	```
- 改变 HTML 样式
	```
	Object.style.property=new style;
	```
	```
	backgroundColor：设置元素的背景颜色
	height：设置元素高度
	width：设置元素宽度
	color：设置文本的颜色
	font：在一行设置所有的字体属性
	fontFamily：设置元素的字体系列
	fontSize：设置元素的字体大小
	```
	```
	<p id="pcon">Hello World!</p>
	<script>
	   var mychar = document.getElementById("pcon");
	   mychar.style.color="red";
	   mychar.style.fontSize="20";
	   mychar.style.backgroundColor ="blue";
	</script>
	```
- 显示和隐藏（display属性）
	```
	Object.style.display = none  //隐藏元素
	Object.style.display = block  //显示为块状元素
	```
- 控制类名（className 属性）：设置或返回元素的class 属性。
	```
	object.className = classname
	```
	
	


