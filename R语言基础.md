 ## R语言基础 ##
[课程链接：R语言基础](https://www.imooc.com/learn/546)
### 第一章 数据结构 ###
- 5种基本对象类型：字符character、数值numeric、整数integer、复数complex、逻辑logical
- 赋值：使用箭头赋值
	```
	> x <- 1
	> class(x)
	[1]"numeric"
	```
	```
	> x <- 2L   #V数字后+L，表示整数
	> class(x)
	[1]"integer"
	```
	```
	> x <- 1+2i #复数
	> class(x)
	[1]"complex"
	```
- 4种基本数据属性：名称name、维度dimensions、类型class、长度length
- **向量**
	```
	x <- vector("character",length=10)  #10个空字符串的向量
	x1 <- 1:4         #int[1:4]
	x2 <- c(1,2,3,4)  #num[1:4]
	as.character(x2)  #强制转换
	names(x1) <- c("a","b","c","d")  #给变量命名
	```
	```
	> x1
	a b c d 
	1 2 3 4
	```
- **矩阵**
	
	方法一：matrix
	```
	x <- matrix(nrow=3,ncol=2)       #三行两列的空矩阵
	x1 <- matrix(1:6,nrow=3,ncol=2)  #按列填充
	rbind(x2,x3)      #将两个矩阵按行拼接
	cbind(x2,x3)      #将两个矩阵按列拼接
	```
	```
	> x1
	     [,1] [,2]
	[1,]    1    4
	[2,]    2    5
	[3,]    3    6
	> dim(x1)  #查看维度
	[1] 3 2
	> attributes(x1)  #查看属性
	$dim
	[1] 3 2
	```
	方法二：改变向量维度
	```
	y <- 1:6
	dim(y) <- c(2,3)  #按列填充
	```
	```
	> y
	     [,1] [,2] [,3]
	[1,]    1    3    5
	[2,]    2    4    6
	```
	方法三：array
	```
	x <- array(1:24,dim=c(4,6))  #按列填充
	```
- **列表**：list，可以包含不同类型的元素
	```
	l1 <- list("a",2,10L,3+4i,TRUE)
	l2 <- list(a=1,b=2,c=3)
	l3 <- list(c(1,2,3),c(4,5,6,7))
	```
	```
	> x <- matrix(1:6,nrow=2,ncol=3)
	> dimnames(x) <- list(c("a","b"),c("c","d","e"))  #给矩阵的行列命名
	> x
	  c d e
	a 1 3 5
	b 2 4 6
	```
- **因子**：factor，处理分类数据 有序/无序
	```
	> x <- factor(c("female","female","male","male","female"))
	> x
	[1] female female male male female
	Levels:female male   #当前因子包含两个水平，在前的为基线水平
	> table(x)    #查看两个水平出现的频率
	x
	female   male 
	     3      2 
	> unclass(x)  #1代表female，2代表male
	[1] 1 1 2 2 1
	```
- **缺失值**
	
	NaN：一般表示数字的缺失值
	
	NA：更广的缺失值，如整数的NA，字符型的NA
	
	NaN属于NA，NA不属于NaN
	```
	> x <- c(1,NA,2,NA,3)
	> is.na(x)
	[1] False True False True False
	> is.nan(x)
	[1] False False False False False
	```
	```
	> x <- c(1,NaN,2,NaN,3)
	> is.na(x)
	[1] False True False True False
	> is.nan(x)
	[1] False True False True False
	```
- **数据框**：data frame
	
	存储表格数据，可视为各元素长度相同的列表
	```
	> df <- data.frame(id=c(1,2,3,4),name=c("a","b","c","d"),gender=c(TRUE,TRUE,FALSE,FALSE))
	> df
		  id	name	gender
	1	1	 a	  TRUE
	2	2	 b	  TRUE
	3	3	 c	  FLASE
	4	4	 d	  FLASE
	```
	```
	data.matrix(df2)  #将数据框转换为矩阵，前提是数据框所有元素是同类型元素
	```
- **日期**：date
	```
	> x <- date()
	> x
	[1] "Mon Jan 29 20:35:20 2018"
	> class(x)
	[1] "character"
	```
	```
	> x2 <- Sys.Date()
	> x2
	[1] "2018-01-29"
	> class(x2)
	[1] Date
	```
	```
	> x3 <- as.Date("2015-01-01")
	> x4 <- as.Date("2016-01-01")
	> x4-x3
	Time difference of 365 days
	> as.numeric(x4-x3)
	[1] 365
	```
	```
	> weekdays(x3)
	[1] "星期四"
	> months(x3)
	[1] "一月"
	> quarters(x3)
	[1] "Q1"
	> julian(x3)   #距离1970-01-01的天数
	[1] 16436  
	```
- **时间**
	
	POSIXct:整数，常用于存入数据框
	
	POSIXlt：列表，包含星期、年、月、日等信息
	```
	> x <- Sys.time()
	> x
	[1] "2018-01-29 20:49:25 CST"
	> class(x)
	[1] "POSIXct" "POSIXt"
	```
	```
	> p <- as.POSIXlt(x)
	> p
	[1] "2018-01-29 20:49:25 CST"
	> class(x)
	[1] "POSIXlt" "POSIXt"
	> names(unclass(p))
	[1] "sec" "min" "hour" "mday" "mon" "year"
	[7] "wday" "yday" "isdst" "zone" "gmtoff"
	> p$sec
	[1] 25.97932
	```
	```
	> x1 <- "一月 1,2015 01:01"
	> strptime(x1,"%B %d,%Y %H:%M")  #提取时间信息
	[1] "2015-01-01 01:01:00 CST"
	```

### 第二章 构建子集 ###
- **R的数组下标是从1开始**
- 基本方法：
	- []：提取一个或多个类型相同的元素
	- [[]]：从列表或数据框中提取元素 
	- $：按名字从列表或数据框中提取元素
- 向量的子集
	```
	x[1]
	x[1:5]
	x[x>5]
	x[x>5 & x<7]
	x[x<3 | x>7]
	```
- 矩阵的子集
	```
	x[1,2]             #第一行的第二列，以向量形式输出
	x[1,2,drop=FALSE]  #第一行的第二列，关掉默认转换向量，以矩阵形式输出
	x[1,]              #第一行
	x[,1]              #第一列
	x[2,c(1,3)]        #第二行的第一列和第三列
	```
- 数据框的子集
	```
	x <- data.frame(v1=1:5,v2=6:10,v3=11:15)
	x$v3[c(2,4)]      #v3的第二、第四个元素
	x[,2]             #x的第二列，即x[,"v2"]
	x[(x$v1<4) & (x$v2>=8),]
	```
	```
	> x$v1>2
	[1] FALSE FALSE TRUE TRUE TRUE
	> which(x$v1>2)
	[1] 3 4 5
	```
- 列表的子集
	
	单括号，名字+内容
	```
	> x <- list(id=1:4,height=170,gender="male")
	> x[1]           #第一个元素，相当于x["id"]
	$id
	[1] 1 2 3 4 
	> x[c(1,3)]      #第一个和第三个元素
	$id
	[1] 1 2 3 4
	$gender
	[1] "male"
	```
	双括号，仅内容
	```
	> x[[1]]
	[1] 1 2 3 4
	> x$id
	[1] 1 2 3 4
	```
	列表模糊匹配
	```
	> l <- list(asdfghj=1:10) 
	> l$a
	 [1]  1  2  3  4  5  6  7  8  9 10
	> l[["a"]]
	NULL
	> l[["a",exact=FALSE]]
	 [1]  1  2  3  4  5  6  7  8  9 10
	```
- 处理缺失值
	```
	> x <- c(1,NA,2,NA,3)
	> is.na(x)                          #判断是否为缺失值
	[1] FALSE  TRUE FALSE  TRUE FALSE
	> x[!is.na(x)]                      #提取不是缺失值的元素
	[1] 1 2 3
	> y <- c("a","b",NA,"c",NA)
	> z <- complete.cases(x,y)          #x，y中都不为NA的则为TRUE
	> z
	[1]  TRUE FALSE FALSE FALSE FALSE
	```
	利用R自带的数据集airquality，提取子集中没有缺失值的前十行
	```
	> library(datasets)
	> head(airquality)
	> g <- complete.cases(airquality)
	> airquality[g,][1:10,]
	```
- 向量化操作
	```
	> x * y     #数值乘
	> x %*% y   #矩阵乘
	```

### 第三章 重要函数的使用 ###
- **str( )**：简洁的表达R中的参数
	```
	> str(lapply)
	function(X,FUN,...)
	```
- **lapply( )**：循环处理**列表**中的每一个元素，返回的是一个**列表**
	```
	> x <- list(a=1:10,b=c(11,21,31,41,51))
	> lapply(x,mean)   #求平均
	$a
	[1] 5.5
	$b
	[1] 31
	```
	```
	> x <- 1:4
	#当传入的参数是向量而不是列表时，R会将向量强制转换为列表
	> lapply(x,runif)  #从一个均匀分布的总体里抽取若干个数出来
	[[1]]
	[1] 0.311446
	[[2]]
	[1] 0.5206289 0.8959686
	[[3]]
	[1] 0.2343986 0.1484248 0.3613301
	[[4]]
	[1] 0.086081290 0.005239313 0.891763911 0.561271967
	#将范围设定为0~100
	> lapply(x,runif,min=0,max=100)
	[[1]]
	[1] 48.86857
	[[2]]
	[1] 32.42744 73.23005
	[[3]]
	[1]  4.324264 75.726922  2.195526
	[[4]]
	[1] 49.85016 92.70952 97.73782 58.29848
	```
	```
	#通过匿名函数和lapply得到x列表中每个矩阵的第一行
	> x <- list(a=matrix(1:6,2,3),b=matrix(4:7,2,2))
	#m代表列表中的每个矩阵，m[1,]表示每个矩阵的第一行
	> lapply(x,function(m) m[1,])
	$a
	[1] 1 3 5
	$b
	[1] 4 6
	```
- **sapply( )**：和lapply一模一样，唯一的不同点是可以对结果进行**化简**，从列表化简成了向量
	```
	> x <- list(a=1:10,b=c(11,21,31,41,51))
	> sapply(x,mean)
	   a    b 
	 5.5 31.0 
	```
- **mapply( )**：lapply的多元版本
	```
	> mapply(rep,1:4,4:1)   #将1~4重复4~1次
	[[1]]
	[1] 1 1 1 1
	[[2]]
	[1] 2 2 2
	[[3]]
	[1] 3 3
	[[4]]
	[1] 4
	```
	```
	#从均值为mean，标准差为std的正态分布总体中抽取n个数据
	> s <- function(n,mean,std){rnorm(n,mean,std)}
	> mapply(s,1:5,5:1,2)
	[[1]]           #s(1,5,2)
	[1] 9.867114
	[[2]]           #s(2,4,2)
	[1] 7.546535 6.465271 
	[[3]]           #s(3,3,2)
	[1] 1.183234 1.853661 5.443392
	[[4]]           #s(4,2,2)
	[1] 2.929521 1.222099 1.082860 3.486434
	[[5]]           #s(5,1,2)
	[1] 0.03681516 2.95913314 2.77878043 3.47994039 1.05551885
	```
- **apply( )**: 沿着**数组**的某一维度处理数据
	```
	> x <- matrix(1:16,4,4)
	> apply(x,2,mean)        #2表示列，求列的平均
	[1]  2.5  6.5 10.5 14.5
	> apply(x,2,sum)         #求列的和
	[1] 10 26 42 58
	> apply(x,1,mean)        #1表示行，求行的平均
	[1]  7  8  9 10
	> apply(x,1,sum)         #求行的列
	[1] 28 32 36 40
	```
	```
	#另一种方式求行、列的平均与和
	> rowSums(x)
	[1] 28 32 36 40
	> rowMeans(x)
	[1]  7  8  9 10
	> colSums(x)
	[1] 10 26 42 58
	> colMeans(x)
	[1]  2.5  6.5 10.5 14.5
	```
	```
	#随机从正态分布中抽取2*3*4个数
	> x <- array(rnorm(2*3*4),c(2,3,4))
	#在第一维和第二维的平面上，沿着第三维求平均
	> apply(x,c(1,2),mean)    
	           [,1]       [,2]      [,3]
	[1,] -0.3044795 -0.8486685 0.9210980
	[2,]  0.4176440 -0.4157241 0.1154303
	```
- **tapply( )**：对向量的子集进行操作
	```
	#正态分布5个数，均匀分布5个数，均值为1、标准差为0的正态分布的5个数
	> x <- c(rnorm(5),runif(5),rnorm(5,1))
	#因子包含3个水平，每个水平下5个元素
	> f <- gl(3,5)
	#把x向量按照f因子的水平进行分组，对每一组求平均
	> tapply(x,f,mean)
	         1          2          3 
	-0.2752000  0.4584916  2.0525776 
	```
- **split( )**：根据因子或因子列表将向量或其他对象分组
	```
	#将x根据f分组，返回的是列表
	> x <- c(rnorm(5),runif(5),rnorm(5,1))
	> f <- gl(3,5)
	> split(x,f)     
	$`1`
	[1]  0.7651133 -0.1675401 -1.4799503  0.2710866  0.4293549
	$`2`
	[1]  0.28491795 0.57107389 0.83696401 0.09875043 0.91549293
	$`3`
	[1]  1.7495093 -1.0219714  2.1046486  0.1376451  1.8151855
	```
	```
	#将airquality数据集按月分组
	> s <- split(airquality,airquality$Month)
	#统计airquality的月份，第一行为月份，第二行为每个月份记录的数目
	> table(airquality$Month)
	 5  6  7  8  9 
	31 30 31 31 30 
	#忽略数据集的NA值，按月计算相关列的平均值
	> sapply(s, function(x) colMeans(x[,c("Ozone","Wind","Temp")],na.rm=TRUE))
	             5        6         7         8        9
	Ozone 23.61538 29.44444 59.115385 59.961538 31.44828
	Wind  11.62258 10.26667  8.941935  8.793548 10.18000
	Temp  65.54839 79.10000 83.903226 83.967742 76.90000
	```
- 排序
	
	sort，对向量进行排序，返回排好序的内容
	
	order，返回排好序的内容的下标 / 多个排序标准
	```
	> x <- data.frame(v1=1:5,v2=c(10,7,9,6,8),v3=11:15,v4=c(1,1,2,2,1))
	> x
	  v1 v2 v3 v4
	1  1 10 11  1
	2  2  7 12  1
	3  3  9 13  2
	4  4  6 14  2
	5  5  8 15  1
	> sort(x$v2)        #对v2进行排序，返回排好序的内容
	[1]  6  7  8  9 10
	> sort(x$v2,decreasing = TRUE)   #降序排列
	[1] 10  9  8  7  6
	> order(x$v2)       #对v2进行排序，返回排好序的内容下标
	[1] 4 2 5 3 1
	> x[order(x$v2),]   #将x按v2排序
	  v1 v2 v3 v4
	4  4  6 14  2
	2  2  7 12  1
	5  5  8 15  1
	3  3  9 13  2
	1  1 10 11  1
	> x[order(x$v4,x$v2),]   #先按v4排，再按v2排
	  v1 v2 v3 v4
	2  2  7 12  1
	5  5  8 15  1
	1  1 10 11  1
	4  4  6 14  2
	3  3  9 13  2
	```
- 总结数据信息
	```
	> head(airquality)     #看前6行
	> tail(airquality)     #看后6行
	> head(airquality,10)  #看前10行
	> any(is.na(airquality$Ozone))   #检查是否存在缺失值
	> sum(is.na(airquality$Ozone))   #查看有多少个缺失值
	> all(airquality$Month < 12)     #检查是不是所有月份都小于12
	
	> summary(airquality) #查看统计信息，包含最小&大值，25%&75%分位点，中位数，平均值，缺失值个数
	     Ozone           Solar.R           Wind       
	 Min.   :  1.00   Min.   :  7.0   Min.   : 1.700  
	 1st Qu.: 18.00   1st Qu.:115.8   1st Qu.: 7.400  
	 Median : 31.50   Median :205.0   Median : 9.700  
	 Mean   : 42.13   Mean   :185.9   Mean   : 9.958  
	 3rd Qu.: 63.25   3rd Qu.:258.8   3rd Qu.:11.500  
	 Max.   :168.00   Max.   :334.0   Max.   :20.700  
	 NA's   :37       NA's   :7                       
	      Temp           Month            Day      
	 Min.   :56.00   Min.   :5.000   Min.   : 1.0  
	 1st Qu.:72.00   1st Qu.:6.000   1st Qu.: 8.0  
	 Median :79.00   Median :7.000   Median :16.0  
	 Mean   :77.88   Mean   :6.993   Mean   :15.8  
	 3rd Qu.:85.00   3rd Qu.:8.000   3rd Qu.:23.0  
	 Max.   :97.00   Max.   :9.000   Max.   :31.0  

	> str(airquality)      #对数据进行简洁的整理
	'data.frame':	153 obs. of  6 variables:
	 $ Ozone  : int  41 36 12 18 NA 28 23 19 8 NA ...
	 $ Solar.R: int  190 118 149 313 NA NA 299 99 19 194 ...
	 $ Wind   : num  7.4 8 12.6 11.5 14.3 14.9 8.6 13.8 20.1 8.6 ...
	 $ Temp   : int  67 72 74 62 56 66 65 59 61 69 ...
	 $ Month  : int  5 5 5 5 5 5 5 5 5 5 ...
	 $ Day    : int  1 2 3 4 5 6 7 8 9 10 ...

	> table(airquality$Month)   #统计
	 5  6  7  8  9 
	31 30 31 31 30
	```
	```
	> titanic <- as.data.frame(Titanic)  #强制转换为数据框
	> head(titanic)
	  Class    Sex   Age Survived Freq
	1   1st   Male Child       No    0
	2   2nd   Male Child       No    0
	3   3rd   Male Child       No   35
	4  Crew   Male Child       No    0
	5   1st Female Child       No    0
	6   2nd Female Child       No    0
	> dim(titanic)    #查看维度
	[1] 32  5
	> summary(titanic)
	  Class       Sex        Age     Survived
	 1st :8   Male  :16   Child:16   No :16  
	 2nd :8   Female:16   Adult:16   Yes:16  
	 3rd :8                                  
	 Crew:8                                  
	                                                                  
	      Freq       
	 Min.   :  0.00  
	 1st Qu.:  0.75  
	 Median : 13.50  
	 Mean   : 68.78  
	 3rd Qu.: 77.00  
	 Max.   :670.00  
	> x <- xtabs(Freq ~ Class + Age,data=titanic)  #查看两个条件交叉起来的频率
	> x
	      Age
	Class  Child Adult
	  1st      6   319
	  2nd     24   261
	  3rd     79   627
	  Crew     0   885
	> ftable(x)    #使表格扁平化
	      Age Child Adult
	Class                
	1st           6   319
	2nd          24   261
	3rd          79   627
	Crew          0   885
	```
	```
	> object.size(airquality)  #查看字节大小
	5496 bytes
	> print(object.size(airquality),units="KB")  #把单位改为KB
	5.4 Kb
	```
