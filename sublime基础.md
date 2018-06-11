## sublime基础 ##
[课程链接：前端开发工具技巧介绍—Sublime篇](https://www.imooc.com/learn/40)
### 快捷键 ###
-  快速找到指定元素：Ctrl + P，Go to Anything
- 快速替换：Ctrl +H，如把页面中所有的mode变成pattern
- 快速复制：Ctrl + Shift +D
- 复制粘贴时，排版更加整齐：Ctrl + Shift +V
- 快速闭合标签：Alt +. （句号） Ctrl + E
- 增加缩进：Ctrl + }
- 减少缩进：Ctrl + {
- 多行游标：
	- Ctrl +D，每按一次多一个光标
	- Ctrl +K，Ctrl +D跳过一次光标
	- 按住Shift键，点击鼠标右键向下拖动鼠标
	- Ctrl +A，Ctrl +Shift +L 产生多行游标
- 命令模式：tools → command palette，Ctrl + Shift +P，可模糊匹配
使用命令模式可减少使用鼠标的次数，加快速度
- 快速转换语言：命令模式中 —— set syntax

### 常用插件 ###
- Emmet插件：
	- 输入“！”，Ctrl + E，直接生成一整段的HTML文档
	- 生成10个ul下的li，输入以下代码，Ctrl + E
		```html
		ul>.item$*10
		```
	- 直接输入script，按Ctrl + E，生成对应标签

- Snippets插件：以模板的方式编程，按Tab键跳跃修改参数
- JavaScript & node JS snippets 插件：可自动补全
- jQuery插件：可自动补全
- DocBlocker插件，快速添加注释
	- 输入/*按回车，补充行注释
	- 输入/**按回车，补充多行注释
	- 在写好的函数上方输入/**按tab键，自动补充函数说明格式
	-  Ctrl+/: 行注释
	-  Ctrl + Shift+/: 块注释
