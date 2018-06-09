## HTML基础课程 ##
[课程链接:HTML+CSS基础课程](https://www.imooc.com/learn/9)
### 第一章 HTML介绍 ###
- HTML是网页内容的载体。CSS样式是表现。JavaScript用来实现网页上的特效效果。
- 认识HTML文件基本结构
	```html
	<html>
		<head>...</head>   
		<body>...</body>
	</html>
	```
- HTML的代码注释
	```html
	<!--注释文字-->
	```

### 第二章 认识标签（第一部分） ###
- **head**标签：文档的头部描述了文档的各种属性和信息，包括文档的标题等。绝大多数文档头部包含的数据都不会真正作为内容显示给读者。以下标签可用在head部分
	```html
	<head>
		<title>...</title>
		<meta>
		<link>
		<style>...</style>
		<script>...</script>
	</head>
	```

- **body**标签：网页上显示的内容放在这里

- **title**标签：网页的标题信息，它会出现在浏览器的标题栏中

- **p**标签：添加段落

- **hx**标签：为你的网页添加标题，分为h1,h2,h3,h4,h5,h6，6个等级，重要性抵减

- **strong**标签：粗体

- **em**标签：斜体

- **br**标签：换行符

- **&nbsp**：添加一些空格

- **hr**标签，添加水平横线

- **img**标签：添加图片
	```html
	<img src="图片地址" alt="下载失败时的替换文本" title = "提示文本">
	```

- **span**标签：为文字设置单独样式
	```html
	<html>
	<head>
	<style>
	span{
    	color:blue;
		}
	</style>
	</head>
	<body>
    		<p>为了追寻他的<span>美国梦</span>，他搬入纽约附近一海湾居住。</p>
	</body>
	</html>
	``` 

- **q**标签：短文本引用，添加引号
	```html
	<html>
	<head>
	</head>
	<body>
	<p>周瑜确实配的上那句<q>聪明秀出为之英，胆略过人为之雄。</q></p> 
	</body>
	</html>
	```
	> <p>周瑜确实配的上那句<q>聪明秀出为之英，胆略过人为之雄。</q></p> 

- **blockquote**标签：长文本引用，独立成有缩进的段落
	```html
	<html>
	<head>
	</head>
	<body>
	<p>大家都在忙于自认为最重要的事情，却没能享受到人生的乐趣，反而要吞下苦果？</p>
	<blockquote>暗淡轻黄体性柔，情疏迹远只香留。何须浅碧深红色，自是花中第一流。</blockquote>
	<p>这是李清照《咏桂》中的词句，在李清照看来，桂花暗淡青黄，性情温柔，淡泊自适，远比那些大红大紫争奇斗艳花值得称道。</p>
	</body>
	</html> 
	```
	> <p>大家都在忙于自认为最重要的事情，却没能享受到人生的乐趣，反而要吞下苦果？</p>
	> <blockquote>暗淡轻黄体性柔，情疏迹远只香留。何须浅碧深红色，自是花中第一流。</blockquote>
	> <p>这是李清照《咏桂》中的词句，在李清照看来，桂花暗淡青黄，性情温柔，淡泊自适，远比那些大红大紫争奇斗艳花值得称道。</p>

- **address**标签：为网页加入地址信息（真实地址/邮箱地址），地址用斜体表示
	```html
	<html>
	<head>
	</head>
	<body>
	<p>公司地址：<address>北京市西城区德外大街10号</address></p> 
	</body> 
	</html> 
	```
	> <p>公司地址：<address>北京市西城区德外大街10号</address></p> 

- **code**标签：加入一行代码
	```html
	<html>
	<head>
	</head>
	<body>
	<p>我们可能知道水平渐变的实现，类似这样：
	<code>{background-image:linear-gradient(left, red 100px, yellow 200px);}</code></p>
	</body>
	</html> 
	```
	> <p>我们可能知道水平渐变的实现，类似这样：
	> <code>{background-image:linear-gradient(left, red 100px, yellow 200px);}</code></p>

- **pre**标签：加入大段代码
	```html
	<head>
	</head>
	<body>
	<pre> 
	var message="欢迎";
	for(var i=1;i<=10;i++)
			{
    			alert(message);
			}
	</pre>
	</body>
	</html> 
	```
	> <pre>
	> var message="欢迎";
	> for(var i=1;i<=10;i++)
	> {
   	>   alert(message); 
	> }
	> </pre>

### 第三章 认识标签（第二部分） ###
- 使用**ul - li**，添加信息列表
	```html
	<ul>
			<li>新闻一</li>
			<li>新闻二</li>
			<li>新闻三</li>
	</ul>
	```
	> <ul>
	>	<li>新闻一</li>
	>	<li>新闻二</li>
	>	<li>新闻三</li>
	> </ul>

- 使用**ol - li**，添加排行榜
	```html
	<ol>
			<li>排行第一名</li>
			<li>排行第二名</li>
			<li>排行第三名</li>
	</ol>
	```
	> <ol>
	>	<li>排行第一名</li>
	>	<li>排行第二名</li>
	>	<li>排行第三名</li>
	> </ol>

- **div**标签：把一些独立的逻辑部分划分出来
	```html
	<div id='版块名称'>...</div>
	```

- **table**标签：网页上的表格
**caption**标签：为表格添加标题和摘要 
**五元素：table, tbody, tr（行）, th（表头）, td（表格）**
Markdown中输入以下代码，表格前会出现许多空行，解决方法是将代码改为紧凑模式
	```html
	<body>
	<table summary="本表格记录2012年到2013年库存记录，记录包括U盘和耳机库存量">
	<caption>2012年到2013年库存记录</caption>  
  	<tr>
    	<th>产品名称 </th>
    	<th>品牌 </th>
    	<th>库存量（个） </th>
    	<th>入库时间 </th>
  	</tr>
  	<tr>
    	<td>耳机 </td>
    	<td>联想 </td>
    	<td>500</td>
    	<td>2013-1-2</td>
  	</tr>
  	<tr>
    	<td>U盘 </td>
    	<td>金士顿 </td>
   	<td>120</td>
   	<td>2013-8-10</td>
  	</tr>
	</table>
	</body> 
	```
	> <body><table summary="本表格记录2012年到2013年库存记录，记录包括U盘和耳机库存量"><caption>2012年到2013年库存记录</caption><tr><th>产品名称 </th><th>品牌 </th><th>库存量（个） </th><th>入库时间 </th></tr><tr><td>耳机 </td><td>联想 </td><td>500</td><td>2013-1-2</td></tr><tr><td>U盘 </td><td>金士顿 </td><td>120</td><td>2013-8-10</td></tr></table></body> 
- **a**标签：添加超链接
默认情况下链接的网页是在当前浏览器窗口中打开，但有时我们需要在新的浏览器窗口中打开
	```html
	<a  href="http://www.imooc.com"  title="点击进入慕课网">click here!</a>
	```
	> <a  href="http://www.imooc.com"  title="点击进入慕课网">click here!</a>
	```html
	<a href="http://www.imooc.com" target="_blank">click here!</a>
	```
	> <a href="目标网址" target="_blank">click here!</a>

- **mailto**标签：在网页中链接Email地址，能让访问者便捷向网站管理者发送电子邮件
	```html
	<!--浏览器自动调用默认邮件程序，并在收件人框中自动填上收件人地址-->
	<a href="malito:yy@imooc.com">发送</a>
	<br>
	<!--cc填写抄送地址-->
	<a href="malito:yy@imooc.com?cc=imoocAdmin@imooc.com">发送</a>
	<br>
	<!--bcc填写密件抄送地址-->
	<a href="malito:yy@imooc.com?bcc=pp@imooc.com">发送</a>
	<br>
	<!--用分号隔开多个收件人地址，可以发送给多个收件人-->
	<a href="malito:yy@imooc.com;pp@imooc.com">发送</a>
	<br>
	<!--subject添加邮件主题-->
	<a href="malito:yy@imooc.com?subject=发送电子邮件">发送</a>
	<br>
	<!--body添加邮件内容-->
	<a href="malito:yy@imooc.com?body=欢迎来到慕课网">发送</a>
	```
如果mailto后面同时有多个参数，第一个参数必须以“?”开头，后面的参数每一个都以“&”分隔。
	```html
	<a href="malito:yy@imooc.com ? cc=imoocAdmin@imooc.com&bcc=pp@imooc.com
	&subject=发送电子邮件&body=欢迎来到慕课网">发送</a>
	```

### 第四章 表单标签 ###
- **表单(form)**：可以把浏览者输入的数据传送到服务器端
**action**：浏览者输入的数据被传送到的地方,比如一个PHP页面(save.php)
**method**： 数据传送的方式（get/post）
	```html
	<form   method="传送方式"   action="服务器文件">...</form>
	```
	```html
	<form    method="post"   action="save.php">...</form>
	```

- 文本输入框、密码输入框
	```html
	<form>
   	<input type="text/password" name="名称" value="文本" />
	</form>
	```
	```html
	<form>
 	 姓名：
  	<input type="text" name="myName">
  	密码：
  	<input type="password" name="pass">
	</form>
	```
> <form>
  姓名：
  <input type="text" name="myName">
  密码：
  <input type="password" name="pass"><br>
</form>

- **文本域(textarea)**：支持多行文本输入
	```html
	<textarea  rows="行数" cols="列数">文本</textarea>
	```
	```html
	<form  method="post" action="save.php">
        	<label>联系我们</label>
        	<textarea cols="50" rows="10" >在这里输入内容...</textarea>
	</form>
	```
> <form  method="post" action="save.php">
        <label>联系我们</label>
        <textarea cols="50" rows="10" >在这里输入内容...</textarea><br>
</form>

- 单选框（radio）、复选框（checkbox）
checked：当设置 checked="checked" 时，该选项被默认选中
同一组的单选按钮，name 取值一定要一致
	```html
	<input   type="radio/checkbox"   value="值"    name="名称"   checked="checked"/>
	```
	```html
	<form name="iForm" method="post" action="save.php">
		你是否喜欢旅游？<br/>
		<input type="radio" name="radiolove" value="喜欢" checked="checked">喜欢
		<input type="radio" name="radiolove" value="不喜欢">不喜欢
		<input type="radio" name="radiolove" value="无所谓">无所谓<br>
		你对哪些运动感兴趣？<br/>
		<input type="checkbox" name="checkbox1" value="跑步" checked="checked">跑步
		<input type="checkbox" name="checkbox2" value="打球" checked="checked">打球
		<input type="checkbox" name="checkbox3" value="登山">登山
		<input type="checkbox" name="checkbox4" value="健身">健身<br>
	</form>
	```
> <form name="iForm" method="post" action="save.php">
		你是否喜欢旅游？
		<input type="radio" name="radiolove" value="喜欢" checked="checked">喜欢
		<input type="radio" name="radiolove" value="不喜欢">不喜欢
		<input type="radio" name="radiolove" value="无所谓">无所谓<br>
		你对哪些运动感兴趣？
		<input type="checkbox" name="checkbox1" value="跑步" checked="checked">跑步
		<input type="checkbox" name="checkbox2" value="打球" checked="checked">打球
		<input type="checkbox" name="checkbox3" value="登山">登山
		<input type="checkbox" name="checkbox4" value="健身">健身<br>
</form>

- 下拉列表框（select)，节省空间
可实现单选和多选（multiple），进行多选时按下Ctrl键同时进行单击
	```html
	<form action="save.php" method="post" >
    	<label>爱好:</label>
    	<select>
      	<option value="看书">看书</option>
      	<option value="旅游" selected="selected">旅游</option>
      	<option value="运动">运动</option>
      	<option value="购物">购物</option>
    	</select>
	</form>
	<br>
	<form action="save.php" method="post" >
    	<label>爱好:</label>
    	<select multiple="multiple">
	<option value="看书">看书</option>
      	<option value="旅游">旅游</option>
      	<option value="运动">运动</option>
     	<option value="购物">购物</option>
    	</select>
	</form>
	```
> <form action="save.php" method="post" >
    <label>爱好:</label>
    <select>
      <option value="看书">看书</option>
      <option value="旅游" selected="selected">旅游</option>
      <option value="运动">运动</option>
      <option value="购物">购物</option>
    </select>
</form>
<form action="save.php" method="post" >
    <label>爱好:</label>
    <select multiple="multiple">
      <option value="看书">看书</option>
      <option value="旅游">旅游</option>
      <option value="运动">运动</option>
      <option value="购物">购物</option>
    </select><br>
</form>
- 使用**提交按钮**，提交数据
	```html
	<input   type="submit"   value="提交">
	```
	```html
	<form  method="post" action="save.php">
    	<label for="myName">姓名：</label>
    	<input type="text" value=" " name="myName " />
    	<input type="submit" value="提交" name="submitBtn" />
	</form> 
	```
> <form  method="post" action="save.php">
    <label for="myName">姓名：</label>
    <input type="text" value=" " name="myName " />
    <input type="submit" value="提交" name="submitBtn" /><br>
</form> 
- 使用**重置按钮**，重置表单信息
	```html
	<input type="reset" value="重置">
	```
	```html
	<form  method="post" action="save.php">
    	<label for="myName">姓名：</label>
    	<input type="text" value=" " name="myName " />
    	<input type="reset" value="重置" name="resetBtn" />
	</form> 
	```
> <form  method="post" action="save.php">
    <label for="myName">姓名：</label>
    <input type="text" value=" " name="myName " />
    <input type="reset" value="重置" name="resetBtn" /><br>
</form> 
- form表单中的**label标签**
label标签不会向用户呈现任何特殊效果，它的作用是为鼠标用户改进了可用性。
当用户单击选中该label标签时，浏览器就会自动将焦点转到和标签相关的表单控件上
如下例，点击“男”标签，单选框会自动选中
	```html
	<form>
  	<label for="male">男</label>
  	<input type="radio" name="gender" id="male" />
  	<label for="female">女</label>
  	<input type="radio" name="gender" id="female" />
  	<label for="email">输入你的邮箱地址</label>
  	<input type="email" id="email" placeholder="Enter email">
	</form>
	```
> <form>
  <label for="male">男</label>
  <input type="radio" name="gender" id="male" />
  <label for="female">女</label>
  <input type="radio" name="gender" id="female" />
  <label for="email">输入你的邮箱地址</label>
  <input type="email" id="email" placeholder="Enter email">
</form>
