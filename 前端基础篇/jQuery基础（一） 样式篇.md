## jQuery基础（一）样式篇 ##
[课程链接：jQuery基础 —— 样式篇](https://www.imooc.com/learn/418)
### 第一章 初始jQuery ###
- jQuery是一个轻量级的JavaScript库，核心是JavaScript，但功能强大了不少，不仅兼容了CSS3，还兼容各种浏览器。写得少，做的更多。
- 优点：容易上手、强大的选择器、解决浏览器的兼容、完善的事件机制、出色的Ajax封装、丰富的UI
- 环境搭建
	-  jQuery 分 2 个系列版本 1.x 与 2.x，主要的区别在于 2.x 不再兼容 IE6、7、8浏览器，这样做的目的是为了兼容移动端开发。由于减少了一些代码，使得该版本比 jQuery 1.x 更小、更快。本课程为了兼容性问题，使用的是 1.9 版本。
	-  jQuery 每一个系列版本分为：压缩版(compressed) 与 开发版(development)，我们在开发过程中使用开发版（开发版本便于代码修改及调试），项目上线发布使用压缩版（因为压缩版本体积更小，效率更快）
	-  jQuery是一个JavaScript脚本库，不需要特别的安装，只需要我们在页面 <head> 标签内中，通过 script 标签引入 jQuery 库即可
	```
	<!DOCTYPE HTML>
	<html>
	<head>
	    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
	    <script type="text/javascript" src="https://www.imooc.com/static/lib/jquery/1.9.1/jquery.js"></script>
	    <title>环境搭建</title>
	</head> 
	<body>
	    <script type="text/javascript"> alert($) </script>
	</body>
	</html>
	```
- jQuery对象与DOM对象

	通过一个简单的例子，简单区分下jQuery对象与DOM对象：
	我们要获取页面上这个id为imooc的p元素，然后给这个文本节点增加一段文字：“您好！通过慕课网学习jQuery才是最佳的途径”，并且让文字颜色变成红色。
	```
	<p id=”imooc”></p>
	```
	普通处理，通过标准JavaScript处理：
	```
	var p = document.getElementById('imooc');
	p.innerHTML = '您好！通过慕课网学习jQuery才是最佳的途径';
	p.style.color = 'red';
	```
	jQuery的处理：
	```
	var $p = $('#imooc');
	$p.html('您好！通过慕课网学习jQuery才是最佳的途径').css('color','red');
	```
	通过jQuery方法包装后的对象，是一个类数组对象。它与DOM对象完全不同，唯一相似的是它们都能操作DOM。
- jQuery对象转化成DOM对象
	- 利用数组下标的方式读取到jQuery中的DOM对象
		
		HTML代码
		```
		<div>元素一</div>
		<div>元素二</div>
		<div>元素三</div>
		```
		JavaScript代码
		```
		var $div = $('div')     //jQuery对象
		var div = $div[0]       //转化成DOM对象
		div.style.color = 'red' //操作dom对象的属性
		```
	- 通过jQuery自带的get()方法
		```
		var $div = $('div')     //jQuery对象
		var div = $div.get(0)   //通过get方法，转化成DOM对象
		div.style.color = 'red' //操作dom对象的属性
		```
- DOM对象转化成jQuery对象

	通过$(dom)方法将普通的dom对象加工成jQuery对象

	HTML代码
	```
	<div>元素一</div>
	<div>元素二</div>
	<div>元素三</div>
	```
	JavaScript代码
	```
	var div = document.getElementsByTagName('div'); //dom对象
	var $div = $(div); //jQuery对象
	var $first = $div.first(); //找到第一个div元素
	$first.css('color', 'red'); //给第一个元素设置颜色
	```

### 第二章 jQuery选择器 ###
- 基础选择器
	```
	$( "#id" )        //id选择器，单选
	$( ".class" )     //类选择器，多选
	$( "element" )    //元素选择器
	$( "*" )          //全选择器
	```
- 层级选择器
	```
	$("parent > child")       //子选择器
	$("ancestor descendant")  //后代选择器
	$("prev + next")          //相邻兄弟选择器
	$("prev ~ siblings")      //一般兄弟选择器
	```
- 基本筛选选择器
	```
	$(":first")           //匹配第一个元素
	$(":last")            //匹配最后一个元素
	$(":not(selector)")   //过滤选择器，去除不匹配元素
	$(":eq(index)")       //选择索引值为index的元素
	$(":gt(index)")       //选择索引值大于给定index的元素,greater than
	$(":lt(index)")       //选择索引值小于给定index的元素,less than
	$(":even")            //选择索引值为偶数的元素
	$(":odd")             //选择索引值为奇数的元素
	$(":header")          //选择所有标题元素，如h1,h2,h3
	$(":lang(language)")  //选择指定语言的所有元素
	$(":root")            //选择该文档的根元素
	$(":animated")        //选择所有正在执行动画效果的元素
	```
	例如：
	```
	$(".div:first")
	$(".div:last")
	$("input:not(:checked) + p")
	```
- 内容筛选选择器
	```
	$(":contains(text)")    //选择所有包含指定文本的元素
	$(":has(selector)")     //选择元素中至少包含指定选择器的元素
	$(":empty")             //选择所有没有子元素的元素
	$(":parent")            //选择所有含有子元素或者文本的元素
	```
	例如：
	```
	$(".div:contains('imooc')")
	$(".div:has(span)")
	```
- 可见性筛选选择器
	```
	$(":visible")     //选择所有显示的元素
	$(":hidden")      //选择所有隐藏的元素
	```
	这里神奇的是 width和height都为0时，元素内有文本在网页中可见但事实上属性是不可见的。而visibility设置为hidden和opacity设置为0虽然不可见但是事实上占用空间所以属性是可见的

	我们有以下几种方式可以隐藏一个元素：
	- CSS display的值是none。
	- type="hidden"的表单元素。
	- 宽度和高度都显式设置为0。
    - 一个祖先元素是隐藏的，该元素是不会在页面上显示
    - CSS visibility的值是hidden
    - CSS opacity的指是0
- 属性筛选选择器
	```
	$("div[name]")             //匹配含有name属性的div元素
	$("div[name='test']")      //匹配name值为test的div元素
	$("div[name|='test']")     //匹配name值为test，或以test为前缀(用-连接)的div元素
	$("div[name~='test']")     //匹配name用空格分隔的值中包含一个test的div元素
	$("div[name!='test']")     //匹配name值不为test的div元素
	$("div[name*='test']")     //匹配name值包含test的div元素
	$("div[name^='test']")     //匹配name值开头为test的div元素
	$("div[name$='test']")     //匹配name值结尾为test的div元素
	$("div[id][name^='test']") //匹配有id属性且name值开头为test的div元素
	```
- 子元素筛选选择器

	不常使用，其筛选规则比起其它的选择器稍微要复杂点
	```
	$(":first-child")       //老大筛选器 
	$(":last-child")        //老幺筛选器 
	$(":only-child")        //独生子女筛选器 
	$(":nth-child(n)")         //排行老几筛选器
	$(":nth-last-child(n)")    // 排行倒数老几筛选器 
	```
	`:first`只匹配一个单独的元素，比如div下的第一个a；`:first-child`选择器可以匹配多个，即为每个父级元素匹配第一个子元素。同理`:last`和`:last-child`
- 表单元素选择器
	```
	$(":input")    //选择所有input,textarea,select,button元素
	$(":text")     //匹配文本框
	$(":password") //匹配密码框
	$(":radio")    //匹配单选按钮
	$(":checkbox") //匹配复选框
	$(":submit")   //匹配提交按钮
	$(":image")    //匹配图像
	$(":reset")    //匹配重置按钮
	$(":button")   //匹配按钮
	$(":file")     //匹配文件
	```
	`$(':password') == $('[type=password]')`
- 表单对象属性筛选选择器
	```
	$('input:enabled')      //选取可用的表单元素
	$('input:disabled')     //选取不可用的表单元素
	$('input:checked')      //选取被选中的input元素
	$('option:selected')    //选取被选中的option元素
	```
- 特殊选择器this
	- this，表示当前的上下文对象是一个html对象，可以调用html对象所拥有的属性和方法
	- $(this),代表的上下文对象是一个jquery的上下文对象，可以调用jQuery的方法和属性值。
	```
	p.addEventListener('click',function(){
    	//this === p
    	this.style.color = "red";
	},false);
	```
	```
	$('p').click(function(){
	    //把p元素转化成jQuery的对象
	    var $this= $(this) 
	    $this.css('color','red')
	})
	```

### 第三章 jQuery的属性与样式 ###
- 特性** Attribute**
	```
	.attr(属性名)          //获取属性的值
	.attr(属性名,属性值)    //设置属性的值
	.attr(属性名,函数值)    //设置属性的函数值
	.removeAttr(属性名)    //移除属性，注意A大写
	```
	```
	<input type="text" value="回调拼接value" />
	$("input:").attr('value',function(i, val){
	    return '通过function设置' + val})
	```
	回调函数由两个参数：被选元素列表中当前元素的下标，以及原始（旧的）值
	```
	通过function设置回调拼接value
	```
- 特性**Attribute**与属性**Property**的区别

	Attribute是dom节点自带的属性，如html中常用的id、class、title、align等：
	```
	<div id="immooc" title="慕课网"></div>
	```	
	Property是这个DOM元素作为对象，其附加的内容，例如,tagName, nodeName, nodeType,, defaultChecked, 和 defaultSelected 
- **.html()** 方法
	```
	html()                //不传入值，获取集合中第一个匹配元素的HTML内容
	.html( htmlString )   //设置每一个匹配元素的html内容
	.html( function(index, oldhtml) )   //用来返回设置HTML内容的一个函数
	```
- **.text()** 方法
	```
	.text()         // 得到匹配元素集合中每个元素的合并文本，包括他们的后代
	.text( textString )      //用于设置匹配元素内容的文本
	.text( function(index, text) )    //用来返回设置文本内容的一个函数
	```
- **.html**与**.text**的异同:
	- .html与.text的方法操作是一样，只是在具体针对处理对象不同
	- .html处理的是元素内容，.text处理的是文本内容
	- .html只能使用在HTML文档中，.text 在XML 和 HTML 文档中都能使用
	- 如果处理的对象只有一个子文本节点，那么html处理的结果与text是一样的

- **.val()** 方法
 	
	主要是用于处理表单元素的值，比如 input, select 和 textarea。
	```
	.val()     //无参数，获取匹配的元素集合中第一个元素的当前值
	.val( value )    //设置匹配的元素集合中每个元素的值
	.val( function )   //一个用来返回设置值的函数
	```
	.val()方法和.html()相同，如果其应用在多个元素上时，只能读取第一个表单元素的"value"值，但是.text()和他们不一样，如果.text()应用在多个元素上时，将会读取所有选中元素的文本内容。

- 增加样式 **.addClass()**
	```
	.addClass( className )   //为每个匹配元素所要增加的一个或多个样式名
	.addClass( function(index, currentClass)) //返回一个或更多用空格隔开的要增加的样式名
	```
	```
	<p class="orgClass">
	$("p").addClass("newClass")
	```
	p元素的class实际上是 class="orgClass newClass"
	样式只会在原本的类上继续增加，通过空格分隔

- 删除样式 **.removeClass()**
	```
	.removeClass( className )
	.removeClass( function(index, class) ) 
	```
	```
	$('.right > div:first').removeClass(function(index,className){
		//className = aa bb imoocClass
		//把div的className赋给下一个兄弟元素div上作为它的class
		$(this).next().addClass(className)
		return 'imoocClass'    //删除自己本身的imoocClass
	})
	```
- 切换样式 **.toggleClass()**
	动态添加删除Class，一次执行相当于addClass，再次执行相当于removeClass
	```
	.toggleClass( className )   //切换样式
	.toggleClass( className, switch )  //一个布尔值，用于判断样式是否应该被添加或移除
	.toggleClass( switch )  //一个用来判断样式类添加还是移除的布尔值
	.toggleClass( function(index, class, switch) , switch )
	//用来返回在匹配的元素集合中的每个元素上用来切换的样式类名的一个函数
	```
	```
    <script type="text/javascript">
    //给所有的tr元素加一个class="c"的样式
	$("#table tr").toggleClass("c"); 
    //给所有的偶数tr元素切换class="c"的样式
    //所有基数的样式保留，偶数的被删除
    $("#table tr:odd").toggleClass("c");
    //第二个参数判断样式类是否应该被添加或删除
    //true，那么这个样式类将被添加;
    //false，那么这个样式类将被移除
    //所有的奇数tr元素，应该都保留class="c"样式
    $("#table tr:even").toggleClass("c", true); 
	//这个操作没有变化，因为样式已经是存在的
    </script>
	```
- 样式操作 **.css()**
	```
	.css( propertyName )  //获取匹配元素的样式属性
	.css(propertyName, value )  //设置CSS
	.css( propertyName, function )  //可以传入一个回调函数，返回取到对应的值进行处理
	```