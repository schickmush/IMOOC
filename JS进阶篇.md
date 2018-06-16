## JS进阶篇 ##
[课程链接：JS进阶篇](https://www.imooc.com/learn/10)
### 第一章 数组 ###
- 创建数组
	```
	var myarray=new Array();
	var myarray= new Array(8);  //创建数组的同时，指定长度
	var myarray = new Array(66,80,90,77,59);  //创建数组同时赋值
	var myarray = [66,80,90,77,59];  //直接输入一个数组
	myarray[0];  //第一个人的成绩表示方法
	myarray[2];  //第三个人的成绩表示方法
	```
- 数组属性length
	```
	myarray.length; //获得数组myarray的长度
	```
- 二维数组
	```
	var Myarr = [[0 , 1 , 2 ],[1 , 2 , 3]]
	```

### 第二章 流程控制语句 ###
- **if** 语句
	注意括号
	```
	if(条件1)
	{ 条件1成立时执行的代码}
	else  if(条件2)
	{ 条件2成立时执行的代码}
	...
	else  if(条件n)
	{ 条件n成立时执行的代码}
	else
	{ 条件1、2至n不成立时执行的代码}
	```
- **switch** 语句
	```
	switch(表达式)
	{
	case值1:
	  执行代码块 1
	  break;
	case值2:
	  执行代码块 2
	  break;
	...
	case值n:
	  执行代码块 n
	  break;
	default:
	  与 case值1 、 case值2...case值n 不同时执行的代码
	}
	```
	```
	var myweek =3;//myweek表示星期几变量
	switch (myweek)
	{
	 case 1:
	 document.write("学习理念知识");
	 break;
	 case 2:
	 document.write("学习理念知识");
	 break;
	 case 3: 
	 document.write("到企业实践");
	 break;
	 case 4:
	 document.write("到企业实践");
	 break;
	 case 5:
	 document.write("总结经验");
	 break;
	 default:
	 document.write("周六、日休息和娱乐");
	}
	```
- **for** 循环
	```
	for(初始化变量;循环条件;循环迭代)
	{     
	    循环语句 
	 }
	```
	```
	<script type="text/javascript">
	var num=1;
	for (num=1;num<=6;num++)  
	{   document.write("取出第"+num+"个球<br />");
	}
	</script>
	```
- **while** 循环
	```
	while(判断条件)
	{
	    循环语句
	 }
	```
	```
	<script type="text/javascript">
	var num=0; 
	while (num<=6)   
	{
	  document.write("取出第"+num+"个球<br />");
	  num=num+1;  
	}
	</script>
	```
- **do...while** 循环
	```
	do
	{
	    循环语句
	 }
	while(判断条件)
	```
	```
	<script type="text/javascript">
	   num= 1;
	   do
	   {
	     document.write("数值为:" +  num+"<br />");
	     num++; 
	   }
	   while (num<=5)
	</script>
	```
- **break** 退出循环
	```
	for(初始条件;判断条件;循环后条件值更新)
	{
	  if(特殊情况)
	  {break;}
	  循环代码
	}
	```
	```
	var num;
	for(num=1;num<7;num++)
	{
		if(num==5)
		{brreak;}
		document.write("数值："+num+"<br/>");
	}
	```
	数值：1
	数值：2
	数值：3
	数值：4
- **continue** 继续循环：仅跳过本次循环
	```
	for(初始条件;判断条件;循环后条件值更新)
	{
	  if(特殊情况)
	  { continue; }
	 循环代码
	}
	```
	```
	var num;
	for(num=1;num<7;num++)
	{
		if(num==5)
		{continue;}
		document.write("数值："+num+"<br/>");
	}
	```
	数值：1
	数值：2
	数值：3
	数值：4
	数值：6

### 第三章 函数 ###
- 函数调用
	- 第一种情况：在`<script>`标签内调用。
		```
		 <script type="text/javascript">
		 function add2()
		 {
		      sum = 1 + 1;
		      alert(sum);
		 }
		 add2();     //调用函数，直接写函数名。
		 </script>
		```
	- 第二种情况：在HTML文件中调用，如通过点击按钮后调用定义好的函数。
		```
		<html>
		<head>
		<script type="text/javascript">
		   function add2()
		   {
		         sum = 5 + 6;
		         alert(sum);
		   }
		</script>
		</head>
		<body>
		<form>
		<input type="button" value="click it" onclick="add2()">  
		//按钮,onclick点击事件，直接写函数名
		</form>
		</body>
		</html>
		```
- Return 返回函数值
	```
	function add2(x,y)
	{
	   sum = x + y;
	   return sum;    //返回函数值,return后面的值叫做返回值。
	}
	result = add2(3,4);
	```

### 第四章 事件响应，网页交互 ###
- 事件：是可以被 JavaScript 侦测到的行为。 网页中的每个元素都可以产生某些可以触发 JavaScript 函数或程序的事件。
- 主要事件			
	```
	onclick        //鼠标单击事件
	onmouseover    //鼠标经过事件
	onmouseout     //鼠标移开事件
	onchange       //文本框内容改变事件
	onselect       //文本框内容被选中事件
	onfocus        //光标聚集 
	onblur         //光标离开
	onload         //网页导入
	onunload       //关闭网页
	```
- 鼠标单击事件( onclick ）
	```
	<html>
	<head>
	   <script type="text/javascript">
	      function add2(){
	        var numa,numb,sum;
	        numa=6;
	        numb=8;
	        sum=numa+numb;
	        document.write("两数和为:"+sum);  }
	   </script>
	</head>
	<body>
	   <form>
	      <input name="button" type="button" value="点击提交" onclick="add2()" />
	   </form>
	</body>
	</html>
	```
- 鼠标经过事件（onmouseover）/鼠标移开事件（onmouseout）
	
	鼠标经过"确定"按钮时，触发onmouseover事件，调用函数message()，弹出消息框，代码如下:
	```
	<html>
	<head>
	<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
	<title> 鼠标经过事件 </title>
	<script type="text/javascript">
	    function message(){
	      confirm("请输入密码后，再单击确定!"); }
	</script>
	</head>
	<body>
	<form>
	密码:<input name="password" type="password" >
	<input name="确定" type="button" value="确定" onmouseover="message()" />
	</form>
	</body>
	</html> 
	```
	密码:<input name="password" type="password" ><input name="确定" type="button" value="确定" onmouseover="message()" />
	<br>
- 光标聚焦事件（onfocus）/失焦事件（onblur）
	
	当将光标移到文本框内时，即焦点在文本框内，触发onfocus 事件，并调用函数message()。
	
	当光标离开当前获得聚焦对象的时候，触发onblur事件，同时执行被调用的程序。
	```
	<html>
	<head>
	<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
	<title> 光标聚焦事件 </title>
	  <script type="text/javascript">
	    function message(){
		  alert("请输入您现在的职业！");
		}
	  </script>
	</head>
	<body>
	请输入您的职业：<br>
	  <form>
	      <input name="username" type="text" value="职业" onfocus="message()">
	  </form>
	</body>
	</html>
	```
- 内容选中事件（onselect）/文本框内容改变事件（onchange）
	
	当文本框或者文本域中的文字被选中时，触发onselect事件，同时调用的程序就会被执行。
	
	通过改变文本框的内容来触发onchange事件，同时执行被调用的程序。
	```
	<html>
	<head>
	<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
	<title> 内容选中事件 </title>
	<script type="text/javascript">
	  function message(){
	    alert("您触发了选中事件！"); }
	</script>    
	</head>
	<body>
	  <form>
	  个人简介：<br>
	   <textarea name="summary" cols="60" rows="5" onselect= "message()">请写入个人简介，不少于200字！</textarea>
	  </form>
	</body>
	</html> 
	```
	<form>个人简介：
	   <textarea name="summary" cols="60" rows="5" onselect= "message()">请写入个人简介，不少于200字！</textarea>
	</form>
- 加载事件（onload）
	
	事件会在页面加载完成后，立即发生onload事件，同时执行被调用的程序，事件写在`<body>`标签内
	```
	<html>
	<head>
	<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
	<title> 加载事件 </title>
	<script type="text/javascript">
	  function message(){
	    alert("加载中，请稍等…"); }
	</script>    
	</head>
	<body onload="message()">
	  欢迎学习JavaScript。
	</body>
	</html> 
	```
- 卸载事件（onunload）
	
	当用户退出页面时（页面关闭、页面刷新等），触发onUnload事件，同时执行被调用的程序。
	```
	<html>
	<head>
	<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
	<title> 卸载事件 </title>
	<script type="text/javascript">   
	     window.onunload = onunload_message;   
	     function onunload_message(){   
	        alert("您确定离开该网页吗？");   
	    }   
	</script>   
	</head>
	<body>
	  欢迎学习JavaScript。
	</body>
	</html>
	```

### 第五章 JS内置对象 ###
- **Date** 日期对象
	```
	var Udate=new Date(); 
	var d = new Date(2012, 10, 1);  //2012年10月1日
	var d = new Date('Oct 1, 2012'); //2012年10月1日
	get/setDay()          //返回、设置星期，返回的是0-6的数字
	get/setDate()         //返回、设置日期
	get/setFullYear()     //返回、设置年份，用四位数表示
	get/setYear()         //返回、设置年份
	get/setMonth()        //返回、设置月份（一月为0）
	get/setHours()        //返回、设置小时，24小时制
	get/setMinutes()      //返回、设置分钟数
	get/setSeconds()      //返回、设置秒钟数
	get/setTime()         //返回、设置时间（单位为毫秒）,计算从 1970 年 1 月 1 日零时到日期对象所指的日期的毫秒数。
	```
	```
	var mydate=new Date();         //当前时间2014年3月6日
	document.write(mydate+"<br>"); //输出当前时间
	document.write(mydate.getFullYear()+"<br>");   //输出当前年份
	mydate.setFullYear(81); //设置年份
	document.write(mydate+"<br>"); //输出年份被设定为 0081年。
	```
	结果格式依次为：星期、月、日、年、时、分、秒、时区
	```
	Thu Mar 06 2014 10:57:47 GMT+0800
	2014
	Thu Mar 06 0081 10:57:47 GMT+0800
	```
	返回星期
	```
	<script type="text/javascript">
	  var mydate=new Date();//定义日期对象
	  var weekday=["星期日","星期一","星期二","星期三","星期四","星期五","星期六"];
	  var mynum=mydate.getDay();
	  document.write(mydate.getDay());
	  document.write("今天是："+ weekday[mynum]);
	</script>
	```
	```
	5
	今天是：星期五
	```
	如果将目前日期对象的时间推迟1小时，代码如下:
	```
	<script type="text/javascript">
	  var mydate=new Date();
	  document.write("当前时间："+mydate+"<br>");
	  mydate.setTime(mydate.getTime() + 60 * 60 * 1000);
	  document.write("推迟一小时时间：" + mydate);
	</script>
	```
	```
	当前时间：Thu Mar 6 11:46:27 UTC+0800 2014
	推迟一小时时间：Thu Mar 6 12:46:27 UTC+0800 2014
	```
- **String** 字符串对象
	```
	var mystr="I love JavaScript!";
	var myl=mystr.length;              //返回该字符串的长度
	var mynum=mystr.toUpperCase();     //将字符串小写字母转换为大写
	mystr.charAt(2);                   //返回位置2的字符
	str.indexOf("I")                   //返回"I"首次出现的位置
	str.indexOf("v",8)                 //从字符串第8为开始，寻找"v"出现的位置
	mystr.substring(7)                 //提取从位置7到结尾的字符
	mystr.substring(2,6)               //提取从位置2到6的字符
	mystr.substr(7)                    //提取从位置7到结尾的字符
	mystr.substr(2,4)                  //提取从位置2开始，长度为4的字符
	```
	字符串分割
	```
	var mystr = "www.imooc.com";
	mystr.split(".")                   //字符串分割，次数不限
	mystr.split(".", 2)                //字符串分割，两次
	document.write(mystr.split("")+"<br>");    //将字符串分割为字符
	document.write(mystr.split("", 5));
	```
	```
	www,imooc,com
	www,imooc
	w,w,w,.,i,m,o,o,c,.,c,o,m
	w,w,w,.,i
	```
- **Math** 对象
	
	Math对象属性
	```
	Math.PI       //返回圆周率
	Math.E        //返回算术常数e
	Math.LN2      //返回2的自然对数（约等于0.693）
	Math.LOG2E    //返回以2为底的e的对数（约等于1.442）
	Math.SQRT1_2  //返回2的平方根的倒数
	Math.SQRT2    //返回2的平方根
	```
	Math对象方法
	```
	abs(x)	acos(x)	asin(x)	atan(x)	 sin(x)	sqrt(x)
	cos(x)	exp(x)	 log(x)	 tan(x)	  max(x,y)  min(x,y)   	
	pow(x,y)          //返回x的y次幂
	random()          //返回0~1之间随机数
	floor(x)          //向下取整
	ceil(x)           //向上取整
	round(x)          //四舍五入
	atan2(y,x)        //返回由x轴到点(x,y)的角度（以弧度为单位）
	toSource()        //返回该对象的源代码
	valueOf()         //返回Math对象的原始值
	```
- **Array** 数组对象
	
	数组属性
	```
	array.length
	```
	数组方法
	```
	concat()      //连接两个或更多的数组
	join()        //把数组的所有元素放入一个字符串
	pop()         //删除并返回数组的最后一个元素
	shift()       //删除并返回数组的第一个元素
	unshift()     //向数组的开头添加一个或更多元素，并返回新的长度
	push()        //向数组的末尾添加一个或更多元素，并返回新的长度
	reverse()     //颠倒数组中元素的顺序
	slice()       //从某个已有的数组返回选定的元素
	sort()        //排序
	splice()      //删除元素，并向数组添加新元素
	toSource()    //返回该对象的源代码
	toString()    //将数组转换为字符串
	```
	数组连接`concat()`
	```
	<script type="text/javascript">
	  var mya1= new Array("hello!")
	  var mya2= new Array("I","love");
	  var mya3= new Array("JavaScript","!");
	  var mya4=mya1.concat(mya2,mya3);
	  document.write(mya4);
	</script>
	```
	```
	hello!,I,love,JavaScript,!
	```
	指定分隔符连接数组元素`join(分隔符)`，若省略参数，则为逗号
	```
	<script type="text/javascript">
	  var myarr = new Array(3)
	  myarr[0] = "I";
	  myarr[1] = "love";
	  myarr[2] = "JavaScript";
	  document.write(myarr.join("."));
	</script>
	```
	```
	I.love.JavaScript
	```
	选定元素`slice()`，该方法并不会修改数组，而是返回一个子数组。
	```
	<script type="text/javascript">
	  var myarr = new Array(1,2,3,4,5,6);
	  document.write(myarr + "<br>");
	  document.write(myarr.slice(2,4) + "<br>");
	  document.write(myarr);
	</script>
	```
	```
	1,2,3,4,5,6
	3,4
	1,2,3,4,5,6
	```
	数组排序`sort()`，如果不指定<方法函数>，则按unicode码顺序排列
	```
	<script type="text/javascript">
	  function sortNum(a,b) {
	  return a - b;     ////升序，如降序，把“a - b”该成“b - a”
	}
	 var myarr = new Array("80","16","50","6","100","1");
	  document.write(myarr + "<br>");
	  document.write(myarr.sort(sortNum));
	</script>
	```
	```
	80,16,50,6,100,1
	1,6,16,50,80,100
	```

### 第六章 浏览器对象 ###
![](https://github.com/schickmush/IMOOC/blob/master/resources/%E6%B5%8F%E8%A7%88%E5%99%A8%E5%AF%B9%E8%B1%A1.jpg)
- JavaScript 计时器
	
	交互时间：以毫秒计（1s=1000ms）。
	```
	setTimeout(代码,交互时间)    //指定的延迟时间之后执行代码
	clearTimeout(id_of_setInterval)
	setInterval(代码,延迟时间)   //每隔指定的时间执行代码
	clearInterval(id_of_setTimeout)
	```
	我们设置一个计时器，每隔 100 毫秒调用 clock() 函数,并显示时间。当点击按钮时，停止时间，代码如下:
	```
	<head>
	<script type="text/javascript">
    function clock()
	{
      var time=new Date();                     
      document.getElementById("clock").value = time;
	}
	// 每隔100毫秒调用clock函数，并将返回值赋值给i
    var i=setInterval("clock()",100);
	</script>
	</head>
	<body>
	  <form>
	    <input type="text" id="clock" size="50"  />
	    <input type="button" value="Stop" onclick="clearInterval(i)"  />
	  </form>
	</body>
	```
	当我们打开网页3秒后，在弹出一个提示框，代码如下:
	```
	<script type="text/javascript">
		setTimeout("alert('Hello!')", 3000 );
	</script>
	```
	当按钮被点击后，输入域便从0开始计数。
	```
	<head>
	<script type="text/javascript">
	var num=0;
	function numCount(){
	 document.getElementById('txt').value=num;
	 num=num+1;
	 setTimeout("numCount()",1000);
	 }
	</script>
	</head>
	<body>
	<form>
	<input type="text" id="txt" />
	<input type="button" value="Start" onClick="numCount()" />
	</form>
	</body>
	```
- **History** 对象
	
	记录了用户曾经浏览过的页面(URL)，并可以实现浏览器前进与后退相似导航的功能。
	
	语法：
	```
	window.history.[属性|方法]
	```
	属性：
	```
	length   //返回浏览器历史列表中的URL数量
	```
	方法：
	```
	back()       //加载history列表中的前一个URL
	forward()    //加载history列表中的下一个URL
	go()         //加载history列表中的某个具体的页面
	go(-1)       //相当于back()
	go(1)        //相当于forward()
	```
- **Location** 对象
![](https://github.com/schickmush/IMOOC/blob/master/resources/Location%E5%AF%B9%E8%B1%A1%E5%B1%9E%E6%80%A7%E5%9B%BE%E7%A4%BA.png)
	
	用于获取或设置窗体的URL，并且可以用于解析URL。
	
	语法：
	```
	location.[属性|方法]
	```
	属性：
	```
	href       //完整的URL
	protocol   //当前URL协议（http/https)
	host       //主机名和当前URL端口号
	hostname   //当前URL主机名
	port       //当前URL端口号
	pathname   //当前URL的路径部分
	search     //从？开始的URL（查询部分）
	hash       //从#开始的URL锚
	```
	方法：
	```
	assign()     //加载新的文档
	reload()     //重新加载当前文档
	replace()    //用新的文档替换当前文档
	```
- **Navigator** 对象
	
	包含有关浏览器的信息，通常用于检测浏览器与操作系统的版本。
	```
	appCodeName     //浏览器代码名的字符串表示
	appName         //返回浏览器名称
	appVersion      //返回浏览器的平台和版本信息
	platform        //返回运行浏览器的操作系统平台
	userAgent       //返回由客户机发送服务器的user-agent头部的值
	```
- **screen** 对象
	
	语法：
	```
	window.screen.属性
	```
	属性：
	```
	availHeight  //窗口可以使用的屏幕高度，单位像素
	availWidth   //窗口可以使用的屏幕宽度，单位像素
	colorDepth   //用户浏览器表示的颜色位数，通常为32位（每像素的位数）
	pixelDepth   //用户浏览器表示的颜色位数，通常为32位（每像素的位数）（IE不支持此属性）
	height       //屏幕的高度，单位像素
	width        //屏幕的宽度，单位像素
	```

### 第七章 DOM对象 ###
- 文档对象模型DOM（Document Object Model）定义访问和处理HTML文档的标准方法。DOM 将HTML文档呈现为带有元素、属性和文本的树结构（节点树）。
- 节点属性：
	```
	nodeName     //返回一个字符串，其内容是给定节点的名字
	```
	元素节点的 nodeName 与标签名相同，属性节点的 nodeName 是属性的名称，文本节点的 nodeName 永远是 text，文档节点的 nodeName 永远是 document
	```
	nodeType     //返回一个整数，这个数值代表给定节点的类型
	```
	元素 (1) 属性 (2) 文本 (3) 注释 (8) 文档 (9)
	```
	nodeValue    //返回给定节点的当前值
	```
	元素节点的 nodeValue 是 undefined 或 null， 文本节点的 nodeValue 是文本自身，属性节点的 nodeValue 是属性的值

- 遍历节点树：
	```
	childNodes        //返回一个数值，由给定元素节点的子节点构成
	firstChild        //返回第一个子节点
	lastChild         //返回最后一个子节点
	parentNode        //返回一个给定节点的父节点
	nextSibling       //返回给定节点的下一个子节点
	previousSibling   //返回给定节点的上一个子节点
	```
- DOM操作
	```
	createElement(tagName)           //创建一个新的元素节点
	createTextNode()                 //创建一个包含着给定文本的新文本节点
	appendChild()                    //指定节点的最后一个子节点列表之后添加一个新的子节点
	insertBefore(newnode,node)       //将一个给定节点插入到一个元素节点的给定子节点前面
	removeChild(node)                //从一个给定元素中删除一个子节点
	replaceChild(newnode,oldnnode)   //把一个给定父元素里的子节点替换成另一个节点
	getElementById()
	getElementsByName()
	getElementsByTagName()
	getAttribute(name)
	setAttribute(name,value)
	```
	获取属性：
	```
	var anode=document.getElementById("alink");
	var attr1=anode.getAttribute("id")
	var attr2=anode.getAttribute("title")
	```
	div标签内创建一个新的 P 标签，代码如下:
	```
	<div id="test"><p id="x1">HTML</p><p>JavaScript</p></div>
	<script type="text/javascript">
		var otest=document.getElementById("test")
		var newnode=document.createElement("p")
		newnode.innerHTML="This is a new p"
		otest.appendChild(newnode)
	</script>
	```
	创建一个按钮，代码如下：
	```
	<script type="text/javascript">
	   var body = document.body; 
	   var input = document.createElement("input");  
	   input.type = "button";  
	   input.value = "创建一个按钮";  
	   body.appendChild(input);  
	 </script>  
	```
