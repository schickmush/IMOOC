### 1. Markdown是什么？
- **Markdown**是一种轻量级标记语言，它以纯文本形式(易读、易写、易更改)编写文档，并最终以HTML格式发布。  
- 笔者使用的本地编辑器为MarkdownPad2，默认处理器不具备代码高亮的功能，需在工具 → 选项 → Markdown中，设置处理器为GitHub风格      

### 2. Markdown基础语法    
#### 2.1 标题
两种形式：  
1）使用`=`和`-`标记一级和二级标题。
> 一级标题   
> `=========`   
> 二级标题    
> `---------`

效果：
> 一级标题   
> =========   
> 二级标题
> ---------  

2）使用`#`，可表示1-6级标题。
> \# 一级标题   
> \## 二级标题   
> \### 三级标题   
> \#### 四级标题   
> \##### 五级标题   
> \###### 六级标题    

效果：
> # 一级标题   
> ## 二级标题   
> ### 三级标题   
> #### 四级标题   
> ##### 五级标题   
> ###### 六级标题

#### 2.2 段落
段落的前后要有空行。若想在段内强制换行的方式是使用**两个以上**空格加上回车（引用中换行省略回车）。

#### 2.3 区块引用
在段落的每行或者只在第一行使用符号`>`,还可使用多个嵌套引用，如：
> \> 区块引用  
> \>> 嵌套引用  

效果：
> 区块引用  
>> 嵌套引用

#### 2.4 代码区块
代码区块的建立是在每行加上4个空格或者一个制表符（如同写代码一样）。如    
普通段落：

void main()    
{    
    printf("Hello, Markdown.");    
}    

代码区块：

    void main()
    {
        printf("Hello, Markdown.");
    }

**注意**:需要和普通段落之间存在空行。

#### 2.5 强调
在强调内容两侧分别加上`*`或者`_`，如：
> \*斜体\*，\_斜体\_    
> \*\*粗体\*\*，\_\_粗体\_\_    
> \*\*\*粗斜体\*\*\*, \_\_\_粗斜体\_\_\_

效果：
> *斜体*，_斜体_    
> **粗体**，__粗体__    
> ***粗斜体***，___粗斜体___

#### 2.6 列表
无序列表: 使用`·`、`+`、或`-`标记
> \-（+\*） 第一项   
> \-（+\*） 第二项   
> \-（+\*） 第三项   

**注意**：标记后面最少有一个_空格_或_制表符_。若不在引用区块中，必须和前方段落之间存在空行。

效果：
> + 第一项
> + 第二项
> + 第三项

嵌套列表：   
> \+ 列表一   
> \+ 列表二   
> &nbsp;&nbsp;&nbsp;\+ 列表二-1   
> &nbsp;&nbsp;&nbsp;\+ 列表二-2   
> &nbsp;&nbsp;&nbsp;\+ 列表二-3      

效果：
>+ 列表一
>+ 列表二
>   + 列表二-1
>   + 列表二-2
>   + 列表二-3

有序列表: 是将上述的符号换成数字,并辅以`.`，如：
> 1 . 第一项   
> 2 . 第二项    
> 3 . 第三项    

效果：
> 1. 第一项
> 2. 第二项
> 3. 第三项

#### 2.7 分割线
分割线最常使用就是三个或以上`*`，还可以使用`-`和`_`。

#### 2.8 链接
链接可以由两种形式生成：**行内式**和**参考式**。    
行内式：
> \[younghz的Markdown库\]\(https:://github.com/younghz/Markdown "Markdown"\)。   
> 直接链接：\<https://github.com>

效果：
> [younghz的Markdown库](https:://github.com/younghz/Markdown "Markdown")。  
> 直接链接：<https://github.com>

参考式：
> \[younghz的Markdown库1\]\[1\]    
> \[younghz的Markdown库2\]\[2\]    
> \[1\]:https:://github.com/younghz/Markdown "Markdown"    
> \[2\]:https:://github.com/younghz/Markdown "Markdown"    

效果：
> [younghz的Markdown库1][1]    
> [younghz的Markdown库2][2]

[1]: https:://github.com/younghz/Markdown "Markdown"
[2]: https:://github.com/younghz/Markdown "Markdown"

**注意**：上述的`[1]:https:://github.com/younghz/Markdown "Markdown"`不出现在区块中。

#### 2.9 图片
添加图片的形式和链接相似，只需在链接的基础上前方加一个`！`，如：  
\!\[\]\(https://github.com/schickmush/GitHub-Learning/blob/master/resource/leslie.jpg).
![](https://github.com/schickmush/GitHub-Learning/blob/master/resource/leslie.jpg).

#### 2.10 反斜杠`\`
相当于反转义作用。使符号成为普通符号。

#### 2.11 符号'`'
起到标记作用。如：
>\`ctrl+a\`

效果：
>`ctrl+a`    

#### 2.13 删除线
在文字前后加\~~或\<s>HTML标签，如：   
> \~\~删除\~\~
> \<s>删除\</s>

效果：
> ~~删除~~
> <s>删除</s>

#### 2.14 上标和下标   
> X\<sub>2\</sub>  
> O\<sup>2\</sup>  

效果：
> X<sub>2</sub>   
> O<sup>2</sup>

### 3. Markdown扩展    
#### 3.1 目录   
分为隐藏式目录，和非隐藏式目录  
隐藏式：\[TOCM]  
非隐藏式：\[TOC]

#### 3.2 缩写
鼠标移动到缩写词可显示原单词，前提是开启识别HTML标签时，已默认开启
> The \<abbr title="Hyper Text Markup Language">HTML\</abbr> specification is maintained by the \<abbr title="World Wide Web Consortium">W3C\</abbr>.  

效果：
> The <abbr title="Hyper Text Markup Language">HTML</abbr> specification is maintained by the <abbr title="World Wide Web Consortium">W3C</abbr>.

#### 3.3 代码段高亮
在代码段前加上 '\```javascript'、'\```html'等

#### 3.4 任务列表
> \- [x] GFM task list 1   
> \- [ ] GFM task list 2   

效果：
- [x] GFM task list 1   
- [ ] GFM task list 2   

#### 3.5 绘制表格
> \| 项目        | 价格   |  数量  |    
> \| --------   | -----:  | :----:  |      
> \| 计算机      | $1600   |   5     |    
> \| 手机        |   $12   |   12   |     
> \| 管线        |    $1    |  234  |     

效果：   

| 项目        | 价格   |  数量  |     
| --------   | :-----:  | :----:  |     
| 计算机      | $1600   |   5     |      
| 手机        |   $12   |   12   |      
| 管线        |    $1    |  234  |       

### 4. 学习资源
[开源在线 Markdown 编辑器](https://pandao.github.io/editor.md/index.html)
