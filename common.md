# 通用编码规范

## 字符编码
所有项目文件统一使用`UTF-8`编码，且不含有`BOM`头。

## 缩进
所有缩进使用4个空格缩进，可在编辑器统一设置。
> Sublime Text3 在右下角Tab Size 中选中 `Indent Using Spaces`、`Tab Width:4`。
> 科普：[写代码时，缩进使用tab还是空格](https://www.zhihu.com/question/19960028)

## 命名规范
- 项目命名
	- 单词与单词之间使用`-`隔开。

	```
	bad: proj_detail、projDetail

	good: proj-detail
	```
- 目录命名
	- 同上
- 文件命名
	- 同上
- 编码命名
	- 变量命名：变量命名统一使用驼峰命名，比如：`tourGuide` 、 `orderDetail`。
	```
	bad: 
		TourGuide、OrderDetail

	good: 
		tourGuide、orderDetail		
	```
	- 变量声明
		- 一个函数作用域中所有的变量声明都提升到函数首部，除了 `for` 、 `while` 、 `if` 里面使用的一次性变量，`var` 的数量不做限制，但是要统一，一行定义一个变量。
		```
		bad:
			var a=1,b=2,c=3;
			var a=1;var b=2;var c=3;
		
		good:
			var a = 1,
				b = 2,
				c = 3;
		
			var a = 1;
			var b = 2;
			var c = 3;
		```
	- 常量命名
		- 常量命名统一大写，单词之间使用下划线`_`分隔。
		```
		bad:
			var max_num = 100;
			var minNum = 0;
		
		good:
			var MAX_NUM = 100;
			var MIN_NUM = 0;
		```
	- 常量声明
		- 常量声明
	
	- 函数
		- 函数命名
	- 类
		- 类命名单词首字母统一使用大写。
		```
		bad:
			function attributeSelector(){
			}
			
			function upgrade_selector(){
			}
	
		good:
			function AttributeSelector(){
			}
			
			function UpgradeSelector(){
			}
		```
	- 括号
		- 花括号`{}`，为了代码的易读性，花括号左边需要添加空格，切需要在语句的左右边； `if` 、 `for` 等，不管中间有多少代码，必须加上花括号，右边花括号需要单独占一行。
		```
		bad:
			if(a === b)
			{}
			
			.detail-wrapper
			{
				border: 1px solid #ddd;
			}

				if(a === c)
			return 1

		good:
			if(a === b) {
				
			}
			
			.detail-wrapper {
				border: 1px solid #ddd;
			}
			
			if(a === c) {
				return 1;
			}
			
		```
	- 引号
	- 分号
		- 所有语句结束必须用分号 `;` 结尾。
		```
		bad:
			if(a === b) {
				return 1
			}
			
			.detail-wrapper{
				border: 1px solid #ddd
			}
		
		good:
			if(a === b) {
				return 1;
			}
			
			.detail-wrapper{
				border: 1px solid #ddd;
			}
		```
	- 空格
		- 所有运算符的左边右边需要有空格隔开。
		- 制表符使用4个空格，这样使得在所用环境下获得一致的唯一方法。
		```
		bad:
			var a=1;
			
			for(var i=0;i<10;i++)
			
		good:
			var a = 1;
			
			for(var i = 0; i < 10; i++)
			
		```
	- ES6 的使用（TODO）
		- let
		- const
		- String Template