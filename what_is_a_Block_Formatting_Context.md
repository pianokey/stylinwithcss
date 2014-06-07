### 什么是 Block Formatting Context? ###

----------
> #### Block Formatting Context即块格式化上下文,简单来说,就是页面上的一个隔离的独立容器,容器里面的子元素不会在 `布局上` 影响到外面的元素,反之也是如此.####

**如何建立Block Formatting Context**  

不是所有的div都会`建立一个Block Formatting Context`,也不是仅仅只有div才能建立Block Formatting Context.只要条件合适,任何块级元素都可以建立一个新的Block Formatting Context,以下是触发属性:  

> - **float: left / right**
> - **position: absolute**
> - **display: inline-block / inline-table / table-cell / table**
> - **overflow: auto / scroll / hidden (即除 overflow:visible; 外)**

**Block Formatting Context怎样流动**  

Block Formatting Context在文档流中属于正常流。也就是说，它跟 `块级模型、 inline模型、 盒模型的relative position` 属于页面文档流。  
ps.与 `页面文档流` 相对应的,还有 `浮动、 绝对定位（fixed是absolute的一个子集）`  

**Block Formatting Context有什么用**

产生了Block Formatting Context的盒模型会有三个性质,下面分别介绍这3个性质:  

1. **Block Formatting Context会阻止边距折叠**

		前面两个的 div>p结构 中,子元素 p 都设置了margin-top:20px;margin-bottom:20px;结果垂直的外边距折叠成了一个;  
		而第三个div由于生成了 Block Formatting Context(通过overflow:hidden;触发),不会使相邻的边距折叠 
2. **Block Formatting Context可以包含内部元素的浮动**

		三个div都是设置了背景色为ff9900，但前一个div就没有显示出来，因为内部的浮动元素脱离了文档流，不受父元素的控制，那么父元素在文档流中是一个空标签，没有高度和宽度，也就不显示任何颜色；
		而第二个div由于生成了Block Formatting Context（通过overflow:hidden;触发），会包容住里面的浮动元素，这样容器才会有自己的宽度和高度（被子元素撑开），这样就会显示出颜色；
		第三个div同样因为生成了Block Formatting Context（通过float:left;触发），显示出颜色。
3. **Block Formatting Context可以阻止元素覆盖浮动盒模型**	 

	+ 块级元素会被它的兄弟浮动元素覆盖
	+ 触发了 BFC 的元素不会被它的兄弟浮动元素覆盖
	+ 子元素宽度均小于父元素，但父元素宽度不足以容纳一行中所有子元素时，非浮动子元素会下沉
	
### hasLayout vs Block Formatting Context###

----------
你应该已经注意到了，上面的代码都是用overflow:hidden;*zoom:1来定义样式。  
这是因为这段代码为标准浏览器的对应盒模型生成了Block Formatting Context，为非标准的IE6/7则触发了hasLayout。

hasLayout跟Block Formatting Context一样都可以阻止边距折叠、包含浮动元素、阻止元素覆盖浮动盒模型。
关于hasLayout，具体见hasLayout。

[本文相关示例](http://fjdksaljf "本文相关示例")
