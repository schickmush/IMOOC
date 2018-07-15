## CSS基础课程 ##
[课程链接:HTML+CSS基础课程](https://www.imooc.com/learn/9)
### 第一章 CSS介绍 ###
- 全称为**层叠样式表 (Cascading Style Sheets)**，它主要是用于定义HTML内容在浏览器内的**显示样式**，如文字大小、颜色、字体加粗等。
- CSS样式由**选择符**和**声明**组成，而声明又由**属性**和**值**组成
网页中所有段落的文字将变成蓝色，而其他的元素（如ol）不会受到影响。
	```css
	p{color:blue}
	```
- CSS注释代码
	```css
	/*注释语句*/
	```

### 第二章 CSS样式基本知识 ###
- 内联式CSS样式，直接写在现有的HTML标签中
	```html
	<p style="color:red;font-size:12px">这里文字是红色。</p>
	```
- 嵌入式CSS样式，写在当前的文件中
	```css
	<style type="text/css">
	span{
	color:red;
	}
	</style>
	```
- 外部式CSS样式，写在单独的一个文件中.在<head>内使用link标签将css样式文件链接到HTML文件内
	```css
	<link href="base.css" rel="stylesheet" type="text/css" />
	```
- 三种方法的优先级：内联式 > 嵌入式 > 外部式，就近原则（离被设置元素越近优先级别越高）

### 第三章 CSS选择器 ###
-  标签选择器：其实就是html代码中的标签     
	为p标签设置12px字号，行间距设置1.6em的样式
	```css
	p{font-size:12px;line-height:1.6em;}
	```
- 类选择器："." 圆点开头

	第一步：使用合适的标签把要修饰的内容标记起来，如下：
	```css
	<span class="stress">胆小如鼠</span>
	```
	第二步：设置类选器css样式，如下：
	```css
	.stress{color:red;}    /*类前面要加入一个英文圆点*/
	```
- ID选择器：'#' 井号开头

	第一步：使用合适的标签把要修饰的内容标记起来，如下：
	```css
	<span id="setGreen">公开课</span>
	```
	第二步：设置类选器css样式，如下：
	```css
	#setGreen{color:green;}
	```
- 类和ID选择器的区别：
	- 在一个HTML文档中，ID选择器只能使用一次。而类选择器可以使用多次。
	- 可以使用类选择器为一个元素同时设置多个样式，ID选择器不可以
		```css
		.stress{color:red;}
		.bigsize{font-size:25px;}
		<p>到了<span class="stress bigsize">三年级</span>下学期时</p>
		```
- 子选择器：">" 大于符号

	用于选择指定标签元素的**第一代子元素**
	
	如下代码会使class名为food下的子元素li加入红色实线边框。
	```css
	.food>li{border:1px solid red;}
	```
- 包含(后代)选择器：空格符号

	用于选择指定标签元素下的**所有后辈元素**
	```css
	.first  span{color:red;}
	```
- 通用选择器：" \* " 星号

	匹配html中**所有标签元素**
	```css
 	* {color:red;}
	```
- 伪类选择符：
	
	允许给html**不存在的标签**（标签的某种状态）设置样式，比如说我们给 a 标签鼠标滑过的状态设置字体颜色变红
	```css
	a:hover{color:red;}
	```
- 分组选择符：使用逗号，为html中多个标签元素设置同一个样式
	```css
	h1,span{color:red;}
	```

### 第四章 CSS的继承、层叠和特殊性 ###
- 继承性

	CSS的某些样式是具有继承性的。继承是一种规则，它允许样式不仅应用于某个特定html标签元素，而且应用于其后代。比如下面代码：如某种颜色应用于p标签，这个颜色设置不仅应用p标签，还应用于p标签中的所有子元素文本，这里子元素为span标签。
	```css
	p{color:red;}
	<p>三年级时，我还是一个<span>胆小如鼠</span>的小女孩。</p>
	```
- 特殊性

	当我们为同一个元素设置了不同的CSS样式代码，那么元素会启用哪一个CSS样式呢? 浏览器是根据权值来判断使用哪种css样式的，权值高的就使用哪种css样式。标签的权值为1，类选择符的权值为10，ID选择符的权值最高为100。
	```css
	p{color:red;} /*权值为1*/
	p span{color:green;} /*权值为1+1=2*/
	.warning{color:white;} /*权值为10*/
	p span.warning{color:purple;} /*权值为1+1+10=12*/
	#footer .note p{color:yellow;} /*权值为100+10+1=111*/
	```
- 层叠性

	如果在html文件中对于同一个元素可以有多个css样式存在并且这多个css样式具有相同权重值怎么办？层叠就是在html文件中对于同一个元素可以有多个css样式存在，当有相同权重的样式存在时，会根据这些css样式的前后顺序来决定，处于最后面的css样式会被应用。如下面代码：最后 p 中的文本会设置为green
	```css
	p{color:red;}
	p{color:green;}
	<p class="first">三年级时，我还是一个<span>胆小如鼠</span>的小女孩。</p>
	```
- 重要性

	我们在做网页代码的时，有些特殊的情况需要为某些样式设置具有最高权值，怎么办？这时候我们可以使用**!important**来解决。如下面代码，这时 p 段落中的文本会显示为red
	```css
	p{color:red!important;}
	p{color:green;}
	<p class="first">三年级时，我还是一个<span>胆小如鼠</span>的小女孩。</p>
	```

### 第五章 CSS格式化排版 ###
- 文字排版
	```css
	body{font-family:"Microsoft Yahei"}          /*字体*/
	body{font-size:12px;color:#666}              /*字号，颜色*/
	p span{font-weight:bold;}                    /*粗体*/
	p a{font-style:italic;}                      /*斜体*/
	p a{text-decoration:underline;}              /*下划线*/
	.oldPrice{text-decoration:line-through;}     /*删除线*/
	```
- 段落排版
	```css
	p{text-indent:2em;}        /*缩进*/
	p{line-height:1.5em;}      /*行间距*/
	h1{letter-spacing:50px;}   /*字母与字母间隔*/
	h1{word-spacing:50px;}     /*单词与单词间隔*/
	h1{text-align:center;}     /*居中*/
	h1{text-align:right;}      /*居右*/
	h1{text-align:left;}       /*居左*/
	```

### 第六章 CSS盒模型 ###
- 元素分类：块状元素、内联元素(又叫行内元素)和内联块状元素。
	- 常见块状元素
		```css
		<div>、<p>、<h1>...<h6>、<ol>、<ul>、
		<dl>、<table>、<address>、<blockquote> 、<form>
		```
	- 常见内联元素
		```css
		<a>、<span>、<br>、<i>、<em>、<strong>、
		<label>、<q>、<var>、<cite>、<code>
		```
	- 常见内联快状元素
		```css
		<img>、<input>
		```
- 块状元素
	- 一个块状元素独占一行
	- 元素的高度、宽度、行高以及顶和底边距都可设置
	- 元素宽度在不设置的情况下，是它本身父容器的100%
	- 设置`display:block`能将元素显示为块状元素。如下代码就是将内联元素a转换为块状元素，从而使a元素具有块状元素特点。
		```css
		a{display:block;}
		```
- 内联元素（行内元素）
	- 和其他元素都在一行上
	- 元素的高度、宽度及顶部和底部边距不可设置；
	- 元素的宽度就是它包含的文字或图片的宽度，不可改变。
	- 块状元素也可以通过代码`display:inline`将元素设置为内联元素
		```css
		div{display:inline;}
		```
- 内联块状元素
	- 和其他元素都在一行上
	- 元素的高度、宽度、行高以及顶和底边距都可设置
	- 代码`display:inline-block`就是将元素设置为内联块状元素
		```css
		<style type="text/css">
		a{
    			display:inline-block;
			width:20px;/*在默认情况下宽度不起作用*/
			height:20px;/*在默认情况下高度不起作用*/
			background:pink;/*设置背景颜色为粉色*/
			text-align:center; /*设置文本居中显示*/
		}
		</style>
		```
- 盒模型
	- 将盒子看为页面元素，盒子内容可以为文字、图片或其他标签元素
	- 内填充 padding
		
		![](https://github.com/schickmush/IMOOC/blob/master/%E5%89%8D%E7%AB%AF%E5%9F%BA%E7%A1%80%E7%AF%87/IMG/padding.PNG)
	- 外边距 margin
	
		![](https://github.com/schickmush/IMOOC/blob/master/%E5%89%8D%E7%AB%AF%E5%9F%BA%E7%A1%80%E7%AF%87/IMG/margin.PNG)
	- 边框 border
		
		![](https://github.com/schickmush/IMOOC/blob/master/%E5%89%8D%E7%AB%AF%E5%9F%BA%E7%A1%80%E7%AF%87/IMG/border.PNG)
	- 盒子的内填充、外边距、边框都有四个方向
	- 关于盒子模型，我们所学的块状标签都具备盒子模型的特征


- 盒模型--边框：border

	边框三属性：粗细、样式和颜色
	```css
	div{border:2px  solid  red;}
	```
	上面是 border 代码的缩写形式，可以分开写：
	```css
	div{
    	border-width:2px;
    	border-style:solid;  /*dashed（虚线）| dotted（点线）| solid（实线）*/
    	border-color:red;
	}
	```
	css 样式中允许只为一个方向的边框设置样式：
	```css
	div{border-bottom:1px solid red;}
	```
- 盒模型--宽度和高度：宽（width）和高（height）
	```css
	div{
    	width:200px;
    	padding:20px;
    	border:1px solid red;
    	margin:10px;    
	}
	```
	![](https://github.com/schickmush/IMOOC/blob/master/resources/%E5%AE%BD%E5%BA%A6%E5%92%8C%E9%AB%98%E5%BA%A6.png)
- 盒模型--填充：padding

	可按顺时针简写，上右下左
	```css
	div{padding:20px 10px 15px 30px;}
	```
	如果上、右、下、左的填充都为10px;可以这么写
	```css
	div{padding:10px;}
	```
	如果上下填充一样为10px，左右一样为20px，可以这么写：
	```css
	div{padding:10px 20px;}
	```
- 盒模型--边界：margin

	语法与padding类似

### 第七章 CSS布局模型 ###
- 流动模型（Flow）

	默认的网页布局模式，**块状元素**都会在所处的包含元素内**自上而下**按顺序垂直延伸分布。**内联元素**都会在所处的包含元素内**从左到右**水平分布显示。

- 浮动模型 (Float)

	可让两个块状元素并排显示。
	```css
	div{
    	width:200px;
    	height:200px;
    	border:2px red solid;
    	float:left;
	}
	<div id="div1"></div>
	<div id="div2"></div>
	```

- 层模型（Layer）：让html元素在网页中精确定位
	- 绝对定位(position: absolute)
	
		这条语句的作用将元素从文档流中拖出来，然后使用left、right、top、bottom属性相对于其最接近的一个具有定位属性的父包含块进行绝对定位。如果不存在这样的包含块，则相对于body元素，即相对于浏览器窗口。
		
		如下面代码可以实现div元素相对于浏览器窗口向右移动100px，向下移动50px。
		```css
		div{
		width:200px;
		height:200px;
		border:2px red solid;
		position:absolute;
		left:100px;
		top:50px;
		}
		<div id="div1"></div>
		```
	- 相对定位(position: relative)
	
		相对于以前的位置移动，移动的方向和幅度由left、right、top、bottom属性确定
	
		如下代码实现相对于以前位置向下移动50px，向右移动100px
		```css
		#div1{
		width:200px;
		height:200px;
		border:2px red solid;
		position:relative;
		left:100px;
		top:50px;
		}
		<div id="div1"></div>
		```
	- 固定定位(position: fixed)
	
		与absolute定位类型类似，但它的相对移动的坐标是**视图（屏幕内的网页窗口）**本身。由于视图本身是固定的，它不会随浏览器窗口的滚动条滚动而变化，除非你在屏幕中移动浏览器窗口的屏幕位置，或改变浏览器窗口的显示大小，因此固定定位的元素会始终位于浏览器窗口内视图的某个位置，不会受文档流动影响
	
		以下代码可以实现相对于浏览器视图向右移动100px，向下移动50px。并且拖动滚动条时位置固定不变。
		```css
		#div1{
		width:200px;
		height:200px;
		border:2px red solid;
		position:fixed;
		left:100px;
		top:50px;
		}
		```
	- Relative与Absolute组合使用（position:relative）
	
		相对于其它元素进行定位
		
		参照定位的元素必须是相对定位元素的前辈元素
		```css
		#box1{
		width:200px;
		height:200px;
		position:relative;    /*参照定位的元素必须加入position:relative*/
		}
		#box2{
		position:absolute;  /*定位元素加入position:absolute，便可以进行偏移定位了*/
		top:20px;
		left:30px;         
		}
		<div id="box1">
		<div id="box2">相对参照元素进行定位</div>
		</div>
		```

### 第八章 CSS代码缩写，占用更少带宽
- 盒模型代码简写

	如果top、right、bottom、left的值相同，可缩写为
	```css
	margin:10px;
	```
	如果top和bottom值相同、left和 right的值相同，可缩写为
	```css
	margin:10px 20px;
	```
	如果left和right的值相同，可缩写为
	```css
	margin:10px 20px 30px;
	```
- 颜色值缩写

	当你设置的颜色是16进制的色彩值时，如果每两位的值相同，可以缩写一半。

	例子1：
	```css
	p{color:#000000;}
	p{color: #000;}
	```
	例子2：
	```css
	p{color: #336699;}
	p{color: #369;}
	```
- 字体缩写
	```css
	body{
    	font-style:italic;
    	font-variant:small-caps; 
    	font-weight:bold; 
    	font-size:12px; 
    	line-height:1.5em; 
    	font-family:"宋体",sans-serif;
	}
	```
	可缩写成：
	在缩写时 font-size 与 line-height 中间要加入“/”斜扛
	```css
	body{font:italic  small-caps  bold  12px/1.5em  "宋体",sans-serif;}
	```

### 第九章 单位和值 ###
- 颜色值
	- 英文命令颜色
		```css
		p{color:red;}
		```
	- RGB颜色
		```css
		p{color:rgb(133,45,200);}
		p{color:rgb(20%,33%,25%);}
		```
	- 十六进制颜色
		```css
		p{color:#00ffff;}
		```
- 长度值
	- 像素：px
	- em：
	就是本元素给定字体的 font-size 值，如果元素的 font-size 为 14px ，那么 1em = 14px；如果 font-size 为 18px，那么 1em = 18px
		```css
		p{font-size:12px;text-indent:2em;}
		```
	- 百分比
		```css
		p{font-size:12px;line-height:130%}
		```

### 第十章 CSS样式设置小技巧 ###
- 水平居中
	- 行内元素：`text-align:center`
		```css
		<style>
  		.txtCenter{text-align:center;}
		</style>

		<body>
  		<div class="txtCenter">我想要在父容器中水平居中显示。</div>
		</body>
		```
	- 定宽块状元素：块状元素的宽度width为固定值
	设置“左右margin”值为“auto”来实现居中
		```css
		<style>
		div{
    		border:1px solid red;
    		width:200px;           /*定宽*/
    		margin:20px auto;      /* margin-left 与 margin-right 设置为 auto */
		}
		</style>

		<body>
  		<div>我是定宽块状元素，哈哈，我要水平居中显示。</div>
		</body>
		```
	- 不定宽块状元素：块状元素的宽度width不固定
		- 加入 `table` 标签，利用table标签的长度自适应性，可以被看做一个定宽度块元素，然后再利用定宽度块状居中的margin的方法，使其水平居中。
			```css
			<style>
			table{border:1px solid; margin:0 auto;}
			</style>

			<div>
 			<table>
  			<tbody>
    			<tr><td>
    			<ul>
        			<li>我是第一行文本</li>
        			<li>我是第二行文本</li>
				<li>我是第三行文本</li>
    			</ul>
    			</td></tr>
  			</tbody>
 			</table>
			</div>
			```
		- 设置 `display: inline` 方法：与第一种类似，显示类型设为**行内元素**，进行不定宽元素的属性设置
			```css
			<style>
			.container{text-align:center;}

			/* margin:0;padding:0（消除文本与div边框之间的间隙）*/
			.container ul{
    			list-style:none;
    			margin:0;
    			padding:0;
    			display:inline;
			}

			/* margin-right:8px（设置li文本之间的间隔）*/
			.container li{
    			margin-right:8px;
    			display:inline;
			}
			</style>

			<body>
			<div class="container">
    			<ul>
        			<li><a href="#">1</a></li>
        			<li><a href="#">2</a></li>
        			<li><a href="#">3</a></li>
    			</ul>
			</div>
			</body>
			```
		- 设置 `position:relative` 和 `left:50%`：利用 相对定位 的方式，将元素向左偏移 50% ，即达到居中的目的
			```css
			<style>
			.container{
    			float:left;
    			position:relative;
    			left:50%
			}

			.container ul{
    			list-style:none;
    			margin:0;
    			padding:0;
    			position:relative;
    			left:-50%;
			}

			.container li{
				float:left;
				display:inline;
				margin-right:8px;
			}
			</style>

			<body>
			<div class="container">
    			<ul>
        			<li><a href="#">1</a></li>
        			<li><a href="#">2</a></li>
        			<li><a href="#">3</a></li>
    			</ul>
			</div>
			</body>
			```
- 垂直居中
	- 父元素高度确定的单行文本
	
		设置父元素的 height 和 line-height 高度一致来实现的
		```css
		<style>
		.container{
		height:100px;
		line-height:100px;
		background:#999;
		}
		</style>
		<div class="container">
		hi,imooc!
		</div>
		```
	- 父元素高度确定的多行文本
		- 使用插入 `table` 标签，同时设置 vertical-align：middle
			```css
			table td{height:500px;background:#ccc}

			<body>
			<table><tbody><tr><td class="wrap">
			<div>
			<p>看我是否可以居中。</p>
			</div>
			</td></tr></tbody></table>
			</body>
			```
		- 设置块级元素的 `display` 为 `table-cell`（设置为表格单元显示），激活 `vertical-align` 属性，但注意 IE6、7 并不支持这个样式, 兼容性比较差。
			```css
			<style>
			.container{
			height:300px;
			background:#ccc;
			display:table-cell;      /*IE8以上及Chrome、Firefox*/
			vertical-align:middle;   /*IE8以上及Chrome、Firefox*/
			}
			</style>

			<div class="container">
			<div>
				<p>看我是否可以居中。</p>
				<p>看我是否可以居中。</p>
				<p>看我是否可以居中。</p>
			</div>
			</div>
			```
- 隐性改变display类型

	当为元素（不论之前是什么类型元素，display:none 除外）设置以下 2 个句之一：
`position : absolute `
`float : left` 或 `float:right `

	元素的display显示类型就会自动变为以 `display:inline-block`（块状元素）的方式显示，当然就可以设置元素的 width 和 height 了，且默认宽度不占满父元素。
	```css
	<style>
	.container a{
	    position:absolute;
	    width:200px;
	    background:#ccc;
	}
	</style>
	<br>
	<div class="container">
	    <a href="#" title="">进入课程请单击这里</a>
	</div>
	```
	





