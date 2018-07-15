## R语言之数据可视化 ##
[课程链接：R语言之数据可视化](https://www.imooc.com/learn/640)

完整的数据分析流程：
- 定义研究问题，定义理想的数据集，确定能获取什么数据，获取数据，清理数据
- 探索性分析（数据可视化），统计分析，建模等
- 解释/交流结果（数据可视化），挑战结果（有没有其他可能），书写报告

### 第一章 了解数据特征 ###
- 观测（observation）、变量（variable）、数据矩阵（data matrix）
- 变量类型
	- 数值变量：连续、离散
	- 分类变量：无序、有序
- 数值变量的特征和可视化
	- 数据集中趋势的测量：均值、中位数、众数
	- 数据分散趋势的测量：值域（max-min）、方差、标准差、四分位距
	- 稳健统计量：受极端值影响小，如中位数、四分位差
	- 一个变量的可视化：柱状图（histogram）、点图（dot plot）、箱图（box plot）
	- 两个变量的可视化：散点图（scatter plot）
- 分类变量的特征和可视化
	- 一个变量的可视化：频率表（frequency table）、条形图（bar plot）
	- 两个变量的可视化：关联表、相对频率表、分段条形图、马赛克图
- 分类变量 + 数据变量的可视化：并排箱图（side-by-side box plot）

### 第二章 基本绘图系统 ###
- 绘图包：graphics包
- plot ( x,y ) 函数：
	
	重要参数：xlab /ylab（坐标轴标签）/lwd（线宽）/lty（线类型）/pch（点类型）/col（颜色）
- Par( ) 函数：用于设置全局参数（作用于R中的所有plot绘图）
	
	重要参数：bg（背景颜色），mar（边距），las（汉字排版）mfrow（把画板分为几行）mfcol（把画板分为几列）
	```
	> par("bg")
	[1] "white"
	> par("col")
	[1] "black"
	> par("mar")         
	[1] 5.1 4.1 4.1 2.1   #分别为：下，左，上，右
	> par("mfrow")
	[1] 1 1
	> par("mfcol")
	[1] 1 1
	```
	```
	par(mfrow=c(1,2))        #分为一行两列
	hist(airquality$Temp)
	hist(airquality$Wind)    #两张图一行显示
	```
- 举例：
	```
	#绘制频率图
	hist(airquality$Wind,xlab="wind")
	#绘制箱图
	boxplot(airquality$Wind,xlab="wind",ylab="speed(mph)")
	#绘制并排箱图
	boxplot(Wind~Month,airquality,xlab="wind",ylab="speed(mph)")
	#绘制散点图
	plot(airquality$Wind,airquality$Temp)
	```
	```
	#分月绘制散点图，并做回归线 + 图例
	> library(graphics)
	> with(airquality,plot(Wind,Temp,            # main参数：标题
		main="Wind and Temp in NYC",type="n"))   # type=n,除了散点其他都有，绘制背景图
	> with(subset(airquality,Month==9),
		points(Wind,Temp,col="red"))
	> with(subset(airquality,Month==5),
		points(Wind,Temp,col="blue"))
	> with(subset(airquality,Month %in% c(6,7,8)),
		points(Wind,Temp,col="black"))
	#回归线拟合数据，拟合模型为lm，Temp~Wind，左边是y，右边是x
	> fit <- lm(Temp~Wind,airquality)
	> abline(fit,lwd=2)
	> legend("topright",pch=1,                 # pch=1，保持和散点图相同大小的点
		col=c("red","blue","black"),
		legend=c("Sep","May","other"))
	```
	![](https://github.com/schickmush/IMOOC/blob/master/%E6%95%B0%E6%8D%AE%E5%88%86%E6%9E%90%E7%AF%87/IMG/1.png)

### 第三章 Lattice绘图系统 ###
- Lattice包函数：
	
	xyplot / bwplot / histogram / stripplot / dotplot / splom / levelplot / contourplot
- 特别适用于观测变量间的交互：在变量z的不同水平，变量y如何随变量x变化
- 格式：xyplot ( y ~ x | f * g, data )
- 举例：
	```
	> library(lattice)
	# |右边没有，说明考察的不是交互作用，只考察两个变量之间的关系，相当于散点图
	> xyplot(Temp~Ozone,data=airquality)
	```
	```
	#按月份分类显示
	> airquality$Month <- factor(airquality$Month)  #首先将月份转换为分类变量
	> xyplot(Temp~Ozone | Month,data=airquality,layout=c(5,1))
	```
	![](https://github.com/schickmush/IMOOC/blob/master/%E6%95%B0%E6%8D%AE%E5%88%86%E6%9E%90%E7%AF%87/IMG/2.PNG)
	```
	> library(lattice)
	> set.seed(1)           #设置种子点，使每次产生的随机数一样
	> x <- rnorm(100)
	> f <- rep(0:1,each=50)      #0和1分别出现50次
	> y <- x+f-f*x+rnorm(100,sd=0.5)
	> f <- factor(f,labels = c("Group1","Group2"))    #转换成分类变量
	> xyplot(y~x | f,panel=function(x,y){        #个性化设置
		panel.xyplot(x,y)
		panel.abline(v=mean(x),h=mean(y),lty=2)  #lty表示线的类型
		panel.lmline(x,y,col="red")    #添加回归线拟合
		})
	```
	![](https://github.com/schickmush/IMOOC/blob/master/%E6%95%B0%E6%8D%AE%E5%88%86%E6%9E%90%E7%AF%87/IMG/3.PNG)

### 第四章 ggplot2绘图系统 ###
- 拥有独特的图层（layer）
	- Data
	- Aesthetics：x-axis / y-axis / color / fill / size / labels / alpha / shape / linear width / linear type
	- Geometries：point / line / histogram / bar / boxplot
	- Facets：columns / rows
	- Statistics：binning / smoothing / descriptive / inferential
	- Coordinates：cartesian / fixed / polar / limits
	- Themes

- **qplot ( ) 函数** 
	```
	#分月显示
	> library(ggplot2)
	> airquality$Month <- factor(airquality$Month)  #转换为分类变量
	> qplot(Wind,Temp,data=airquality,color=Month)  #用颜色分类
	> qplot(Wind,Temp,data=airquality,shape=Month)  #用形状分类 
	> qplot(Wind,Temp,data=airquality,size=Month)   #用大小分类
	> qplot(Wind,Temp,data=airquality,color=I("red"))  #统一颜色
	> qplot(Wind,Temp,data=airquality,size=I(3))       #统一大小 
	```
	![](https://github.com/schickmush/IMOOC/blob/master/%E6%95%B0%E6%8D%AE%E5%88%86%E6%9E%90%E7%AF%87/IMG/4.PNG)
	```
	#根据点，拟合回归线，阴影部分是置信空间
	> qplot(Wind,Temp,data=airquality,geom=c("point","smooth"))
	```
	![](https://github.com/schickmush/IMOOC/blob/master/%E6%95%B0%E6%8D%AE%E5%88%86%E6%9E%90%E7%AF%87/IMG/5.PNG)
	```
	> qplot(Wind,Temp,data=airquality,facets=.~Month)  #每列代表不同的月份
	> qplot(Wind,Temp,data=airquality,facets=Month~.)  #每行代表不同的月份
	```
	![](https://github.com/schickmush/IMOOC/blob/master/%E6%95%B0%E6%8D%AE%E5%88%86%E6%9E%90%E7%AF%87/IMG/6.PNG)
	```
	#只传入一个变量，会默认为柱状图
	> qplot(Wind,data=airquality,facets=Month~.)
	```
	![](https://github.com/schickmush/IMOOC/blob/master/%E6%95%B0%E6%8D%AE%E5%88%86%E6%9E%90%E7%AF%87/IMG/7.PNG)
	```
	#只传入y，不传入x，散点图，会按照风速出现的顺序绘制
	> qplot(y=Wind,data=airquality,facets=Month ~.)
	```
	![](https://github.com/schickmush/IMOOC/blob/master/%E6%95%B0%E6%8D%AE%E5%88%86%E6%9E%90%E7%AF%87/IMG/8.PNG)
	```
	#累加的柱状图，不同月份用不同颜色表示
	> qplot(Wind,data=airquality,fill=Month)
	```
	![](https://github.com/schickmush/IMOOC/blob/master/%E6%95%B0%E6%8D%AE%E5%88%86%E6%9E%90%E7%AF%87/IMG/9.PNG)
	```
	#频率分布的轮廓图
	> qplot(Wind,data=airquality,geom="density",color=Month)
	```
	![](https://github.com/schickmush/IMOOC/blob/master/%E6%95%B0%E6%8D%AE%E5%88%86%E6%9E%90%E7%AF%87/IMG/10.PNG)
	```
	#频率分布的点阵图
	> qplot(Wind,data=airquality,geom="dotplot")
	```
	![](https://github.com/schickmush/IMOOC/blob/master/%E6%95%B0%E6%8D%AE%E5%88%86%E6%9E%90%E7%AF%87/IMG/11.PNG)
- **ggplot ( ) 函数** 
	
	分图层。第一个参数是数据集，第二个参数是美学相关的层，第三个参数是统计信息层。
	```
	#散点图
	> ggplot(airquality,aes(Wind,Temp))+
		geom_point(color="steelblue",alpha=0.4,size=3)  # alpha设置透明度

	#按月绘制散点图
	> ggplot(airquality,aes(Wind,Temp))+
		geom_point(aes(color=factor(Month)),alpha=0.4,size=3)

	#添加统计信息层
	> ggplot(airquality,aes(Wind,Temp))+
		geom_point()+      #点层
		geom_smooth()      #统计信息层，回归线+置信区间阴影，也可用stat_smooth()

	#点层和统计信息层可以不同时存在
	> ggplot(airquality,aes(Wind,Temp))+
		geom_smooth()

	#选择回归方式，关掉置信区间
	> ggplot(airquality,aes(Wind,Temp))+
		stat_smooth(method="lm",se=FALSE)  #选择线性回归

	#按月份绘制回归线
	>ggplot(airquality,aes(Wind,Temp,col=factor(Month)))+
		stat_smooth(method="lm",se=FALSE)

	#对月份进行颜色分类，但对总体进行回归分析
	> ggplot(airquality,aes(Wind,Temp,col=factor(Month),group=1))+
		geom_point()+
		stat_smooth(method="lm",se=FALSE)
	```
	```
	#手动通过调色板确定颜色
	> library(RColorBrewer)
	#从Dark2调色板中选取5个颜色，第六个颜色为黑色
	> myColors <- c(brewer.pal(5,"Dark2"),"black")  
	> ggplot(airquality,aes(Wind,Temp,col=factor(Month)))+
		geom_point()+
		stat_smooth(method="lm",se=FALSE,aes(group=1,col="All"))+
		stat_smooth(method="lm",se=FALSE)+
		scale_color_manual("Month",values=myColors)
	```
	![](https://github.com/schickmush/IMOOC/blob/master/%E6%95%B0%E6%8D%AE%E5%88%86%E6%9E%90%E7%AF%87/IMG/12.PNG)
	```
	#每个月一列，分列显示
	> ggplot(airquality,aes(Wind,Temp,col=factor(Month)))+
		geom_point()+
		stat_smooth(method="lm",se=FALSE)+
		scale_color_manual("Month",values=myColors)+
		facet_grid(.~Month)
	```
	![](https://github.com/schickmush/IMOOC/blob/master/%E6%95%B0%E6%8D%AE%E5%88%86%E6%9E%90%E7%AF%87/IMG/13.PNG)
	```
	#改变主题
	> ggplot(airquality,aes(Wind,Temp,col=factor(Month)))+
		geom_point()+
		stat_smooth(method="lm",se=FALSE)+
		scale_color_manual("Month",values=myColors)+
		facet_grid(.~Month)+
		theme_classic()
	```
	![](https://github.com/schickmush/IMOOC/blob/master/%E6%95%B0%E6%8D%AE%E5%88%86%E6%9E%90%E7%AF%87/IMG/14.PNG)
- **RColor**
	
	grDevice包：**colorRamp()** & **colorRampPalette()**
	```
	#用RGB表示颜色
	> pal <- colorRamp(c("red","blue"))
	> pal(0)    #red
	     [,1] [,2] [,3]
	[1,]  255    0    0
	> pal(1)    #blue
	     [,1] [,2] [,3]
	[1,]    0    0  255
	> pal(0.5) 
	      [,1] [,2]  [,3]
	[1,] 127.5    0 127.5
	> pal(seq(0,1,len=10))
	           [,1] [,2]      [,3]
	 [1,] 255.00000    0   0.00000
	 [2,] 226.66667    0  28.33333
	 [3,] 198.33333    0  56.66667
	 [4,] 170.00000    0  85.00000
	 [5,] 141.66667    0 113.33333
	 [6,] 113.33333    0 141.66667
	 [7,]  85.00000    0 170.00000
	 [8,]  56.66667    0 198.33333
	 [9,]  28.33333    0 226.66667
	[10,]   0.00000    0 255.00000
	```
	```
	#用十六进制表示颜色
	> pal <- colorRampPalette(c("red","yellow"))
	> pal(1)
	[1] "#FF0000"
	> pal(2)
	[1] "#FF0000" "#FFFF00"
	> pal(10)
	 [1] "#FF0000" "#FF1C00" "#FF3800" "#FF5500" "#FF7100"
	 [6] "#FF8D00" "#FFAA00" "#FFC600" "#FFE200" "#FFFF00"
	```
	RColorBrewer包：**brewer.pal()**
	```
	> library(RColorBrewer)
	> cols <- brewer.pal(3,"Greens")  #从Greens调色板取3个颜色
	> display.brewer.pal(3,"Greens")  #显示这3个颜色
	> pal <- colorRampPalette(cols)   
	> image(volcano,col=pal(20))      #以3个颜色为端点，取20个颜色
	```
	![](https://github.com/schickmush/IMOOC/blob/master/%E6%95%B0%E6%8D%AE%E5%88%86%E6%9E%90%E7%AF%87/IMG/15.PNG)

- R支持的图形设备
	```
	#把图画到文件设备中，以pdf为例
	> pdf(file="myfig.pdf")
	> with(airquality,plot(Wind,Temp,main="Wind and Temp in NYC"))
	> dev.off()    #关掉图形设备
	> getwd()      #显示当前工作路径，找到pdf文件
	```
	```
	#将屏幕设备的图copy到png里
	> with(airquality,plot(Wind,Temp,main="Wind and Temp in NYC"))
	> dev.copy(png,file="mycopy.png")
	> dev.off()
	```


