### css中的 font 属性 ###

----------
> **在css中的font是一个聚会属性, 它是(font-style/font-weight/font-variant/font-size/font-family)属性的聚合**

**顺序很重要! font属性的值至少需要两个值,并且有顺序.**  

	font:<font-size><font-family>  
这是font的基本声明,用值来替换即如下:

	font:100% sans-serif;  
重点是,**font属性一定要包含这两个值, 并且它们的顺序也一定要是 `font-size font-family` .**如果不是这样的话,那么任何浏览器都会忽略整个font属性.

如果你希望在font属性里面有其他的属性的话,那么所有的值(除了line-height以外)都必须在这二两个必需值得前面.

	font:bold italic 100% sans-serif;
	font:italic bold small-caps 100% sans-serif;
如果任何一个值放在两个必需属性的后面或中间,那么浏览器会忽视整个font属性.

### CSS中的 line-height 属性 ###

----------


1. **line-height属性的 继承性 很重要**

		body{line-height: 1.2}
2. **如果希望在 font 属性中包括 line-height 值,那么用如下代码**

		body{font: italic bold small-caps 100%/1.2 sans-serif;}
这是整个CSS语言中唯一合法出现 `斜杠/` 地方,`font 和　line-height`之间没有空格
3. line-height单位,建议**在所有的情况下都不要给 line-height 设置单位(em、px),而是用一个数字**

		ul {font-size:15px; line-height:1em;}
		li {font-size:10px}
		samll {font-szie:80%}
如果 **ul>li>small** 是这样的嵌套关系,那么他们的行高等于:

		ul {font-size:15px; line-height:1em;}
		li {font-size:10px} 		// 15px
		samll {font-szie:80%}		// 15px
是的,**浏览器会根据父容器的 `font-size` 计算出 `1em = 15px`, 然后浏览器把该 `计算过的值` 作为 `line-height` 赋予给子元素, 而不是让子元素重新计算!**  
px 就更不用说了,同样是作为一个 `固定的值` 作为 `line-height` 赋予给子元素.  

	所以我们希望整个容器都是按文字的 `1倍行高` 的话,代码如下:

		ul {font-size:15px; line-height:1}
		li {font-size:10px} 		// 10px
		samll {font-szie:80%}		// 8px

  

 
