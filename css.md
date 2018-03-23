# CSS编码规范
> CSS 作为网页样式的描述语言，在web应用中一直有着广泛的应用。本文档的目标是使 CSS 代码风格保持一致，容易被理解和被维护。虽然本文档是针对 CSS 设计的，但是在使用各种 CSS 的预编译器(如 less、sass、stylus 等)时，适用的部分也应尽量遵循本文档的约定。

- ### 通用
	- 编码、缩进等通用规范：与[通用编码规范](./common.md)保持一致一致。

- ### 选择器
	- 当使用多个选择器的时候，每个选择器需要单独占一行，选择器名字单词与单词之间使用`-`分隔开。

	```
	/*bad*/
	.one,.two,.three{
		color: red;
		line-height: 1.5em;
	}
	
	/*good*/
	.one,
	.two,
	.three{
		color: red;
		line-height: 1.5em;
	}
	```
	- `>`、`+`、`~`选择器的两边需要保留一个空格。
	
	```
	/*bad*/
	.one>.two+.three~.four{
		color:red;
	}
	
	/*good*/
	.one > .two + .three + .four{
		color: red;
	}
	```

	- 属性选择器中的值必须用双引号包围，规则与`html`属性一致。

	```
	./*bad*/
	.one[name=one]{
		color: red;
	}

	.two[name='two']{
		color: blue;
	}

	/*good*/
	.one[name="one"]{
		color: red;
	}

	.two[name="two"]{
		color: blue;
	}
	```

	- 如无必要，不得为`id`、`class`选择器添加类型选择器进行限定。
	
	```
	/*bad*/
	p.one{
		color: red;
	}

	div#two{
		color: blue;
	}

	/*good*/
	.one{
		color: red;
	}
	
	#two{
		color: blue;
	}
	```

- ### 属性
	- 属性缩写：不强制要求，建议能够缩写的尽量缩写，例如border、margin、padding等。
	- 书写顺序：应按功能进行分组，并以 Formatting Model（布局方式、位置） > Box Model（尺寸） > Typographic（文本相关） > Visual（视觉效果） 的顺序书写，以提高代码的可读性。另外，如果包含 content 属性，应放在最前面。
	- > **解释：**
		- Formatting Model 相关属性包括：position / top / right / bottom / left / float / display / overflow 等
		- Box Model 相关属性包括：border / margin / padding / width / height 等
		- Typographic 相关属性包括：font / line-height / text-align / word-wrap 等
		- Visual 相关属性包括：background / color / transition / list-style 等
	
	```
	.sidebar {
		/* formatting model: positioning schemes / offsets / z-indexes / display / ...  */
		position: absolute;
		top: 50px;
		left: 0;
		overflow-x: hidden;
		
		/* box model: sizes / margins / paddings / borders / ...  */
		width: 200px;
		padding: 5px;
		border: 1px solid #ddd;
		
		/* typographic: font / aligns / text styles / ... */
		font-size: 14px;
		line-height: 20px;
		
		/* visual: colors / shadows / gradients / ... */
		background: #f5f5f5;
		color: #333;
		transition: color 1s;
	}	
	```
- ### !important
	- 禁止使用`!important`声明，因为如果要覆盖该属性，会必须再写`!important`才行，久而久之，会造成代码难以维护。
	
	```
	/*bad*/
	.one{
		color: red!important;
	}
	.one .two{
		color: blue!important;
	}

	/*good*/
	.one{
		color: red;
	}
	.one .two{
		color: blue;
	}
	```

- ### z-index
	- 如果能够通过调整HTML结构或者定位来实现元素分层、覆盖，就尽量不要使用z-index。
	- 页面太多z-index属性难以管理，造成不必要的bug。
	- z-index规则：
		- `0-99`:用于页面普通元素，非全局的功能模块使用。
		- `100-199`:用于全局页面模块，例如：header、footer、toolbar,sidebar等。
		- `200-299`:全局功能性的模块，例如：model、dialog、tooltip、mask等。
		- `300-*`:全局其他特殊模块。

- ### 字体参考
	- font-family 属性中的字体族名称应使用字体的英文 Family Name，其中如有空格，须放置在引号中。

字体 | 操作系统 | Family Name
-----|----------|------------
宋体 (中易宋体) | Windows | SimSun
黑体 (中易黑体) | Windows | SimHei
微软雅黑 | Windows | Microsoft YaHei
微软正黑 | Windows | Microsoft JhengHei
华文黑体 | Mac/iOS | STHeiti
冬青黑体 | Mac/iOS | Hiragino Sans GB
文泉驿正黑 | Linux | WenQuanYi Zen Hei
文泉驿微米黑 | Linux | WenQuanYi Micro Hei

- ### Media Query
	- Media Query 不得单独编排，必须与相关的规则一起定义。

- ### Expression
	- 禁止使用express表达式

	```
		/*good*/
		/*header styles*/
		@media (...) {
		    /*header styles*/
		}
		
		/*main styles*/
		@media (...) {
		    /*main styles*/
		}
		
		/*footer styles*/
		@media (...) {
		    /*footer styles*/
		}
		
		/*bad*/
		/*header styles*/
		/*main styles*/
		/*footer styles*/
		
		@media (...) {
		    /*header styles*/
		    /*main styles*/
		    /*footer styles*/
		}
	```
	- Media Query 如果有多个逗号分隔的条件时，应将每个条件放在单独一行中。

- ### 优化
	- 嵌套尽量不要超过三层，会导致性能问题。
	- 每个选择器之间使用回车换行。
	- 使用margin左右居中，不使用 `margin:0 auto;`，使用 `margin: auto` 即可。
	- 选择器命名方法，思想可以参考`BEM`命名法，根据功能模块来定义选择器，而不是根据`UI`的样式、或者`HTML`的结构来命名、嵌套。
	- 注释：模块名字、特殊操作等需要添加注释，以便查阅。
	- 为了防止页面选择器重名，不能使用`list`、`app`、`wrap`、`main`、`item`等名字，需要加上功能块的名字,选择器名字不宜过长。
	
	```
	/*bad*/
	.main-wrap{//整体包裹
		width: 1200px;
		margin:0 auto;
		.list{
			.item{
				.item-detail{
					color: #252525;
				}
			}
			.item-red{
				color: red;
			}
			.item-yellow{
				color: red;	
			}
		}
	}

	/*good*/
	/*整体包裹功能块块*/
	.main-wrap{
		width: 1200px;
		margin: auto;
	}
	
	/*信息列表模块*/
	.info-list{
		.info-item{
		}
		//每个选择器之间分隔开来。
		.info-item-danger{//危险信息
			color:red;
		}

		.info-item-warning{
			color: yellow;
		}
	}
	```

- ### 参考
	- [BEM的定义](http://www.w3cplus.com/css/bem-definitions.html)
	- [CSS编码规范](https://github.com/ecomfe/spec/blob/master/css-style-guide.md)