# HTML编码规范

HTML
> `HTML`作为描述网页结构的超文本标记语言，在`WEB`应用中广泛地使用，本文档的目标是使`HTML`代码风格保持一致，容易被理解和被维护。

- ### 通用
	- 编码、缩进等通用规范：与[通用编码规范](./common.md)保持一致一致。

- ### DOCTYPE
	- 统一只用`html5 doctype`，需要在文档的第一行声明，确保浏览器按照统一的标准渲染文档，保证展示的一致性。
	
	```
	<!DOCTYPE html>
	```
- ### 标签
	- 标签名字统一使用小写字母
	
	```
	/*bad*/
	<SPAN>This is name.</SPAN>
	
	/*good*/
	<span>This is span.<span>
	```

	- 不允许省略闭合标签
	
	```
	/*bad*/
	<a href="//toursforfun.com">toursforfun

	/*good*/
	<a href="//toursforfun.com">toursforfun</a>
	```
	- 自闭合标签无需添加闭合斜杠 `/`，常见的自闭合标签：`<br>`、`<input>`、`<img>`。

	```
	/*bad*/
	<br/>
	<input/>
	<img/>

	/*good*/
	<br>
	<input>
	<img>
	```

	- 熟记标签的嵌套规则，详见 [HTML DTD Elements](https://www.w3.org/TR/html5/dom.html#elements)
	
	```
	/*bad*/
	<p>
		<div>
			this is toursforfun.
		</div>
	</p>

	/*good*/
	<div>
		<p>
			this is toursforfun.
		</p>
	</div>
	```
	
	- 语义化，语义化标签能够使文档更易阅读，方便维护，利于SEO，常见语义化标签如下：
		- p 段落
		- h1,h2,h3,h4,h5,h6 层级标题
		- strong,em 强调
		- ins 插入
		- del 删除
		- abbr 缩写
		- code 代码标识
		- cite 引述来源作品的标题
		- q 引用
		- blockquote 一段或长篇引用
		- ul 无序列表
		- ol 有序列表
		- dl,dt,dd 定义列表

- ### 属性
	- 属性名字必须使用小写字母,单词与单词之间使用`-`分隔。
	
	```
	/*bad*/
	<div parentId="pid">
		parent element
	</div>

	/*good*/
	<div parent-id="pid">
		parent element
	</div>
	```

	- 布尔类型的属性，建议不添加属性值
	**示例：**

	```
	<input type="text" disabled>
	<input type="text" readonly>
	<input type="checkbox" checked>
	```

	- 自定义属性，建议使用`data-`为属性前缀，方便区分，同时js通过`dataset`访问自定义速度更快。 
	**示例：**

	```
	<input type="text" data-max="10" data-min="1">
	```	

- ### DOCTYPE
	- 统一只用`html5 doctype`，需要在文档的第一行声明，确保浏览器按照统一的标准渲染文档，保证展示的一致性。
	
	```
	<!DOCTYPE html>
	```

- ### IE 兼容模式
	- 使用`meta`标签，保证`IE`默认以最新版本渲染，双核浏览器默认使用`Chrome`内核渲染。

	```
	<meta name="renderer" content="webkit”>
	<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1”>
	```

- ### 命名
	- id：整个页面必须唯一。
	- class：必须以当前模块或者相应的功能命名，不能出现以样式信息的命名。`red-tip`、`yellow-tip`，`danger-tip`、`warning-tip`。
	- 同一个页面，不能使用名字相同的`id`和`name`。
	- `hook`：为了更好地找到与`js`有关的元素，在脚本中使用到的元素`id`和`class`需要使用 `J-`作为前缀，`J-header-section`。

- ### 优化
	- 减少标签的数量：在编写`HTML`代码时，需要尽量避免多余的父节点，减少不必要的嵌套；很多时候，需要通过迭代和重构来使`HTML`变得更少。
	- 尽量遵循`HTML`标准和语义，但是不应该以浪费实用性作为代价；任何时候都要用尽量小的复杂度和尽量少的标签来解决问题。
	- 可访问性：负责主要功能按钮需要放置在最前面。
	- `html`结构一定要有逻辑性，从上到下，从左到右，尽量避免使用定位或者浮动来将页面“拼”到一起，这样在结构上面尽量能够让`js`操作更加方便，提高代码的可读性和可维护性。
	- 注释：页面复杂会导致页面过长，代码比较杂乱，建议每个大的功能块注释上当前模块的名字，以便查阅，能够使用`include`引入就使用`include`引入。

