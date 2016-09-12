#### 第十三章  
 1. 什么叫做bom，什么叫做dom？
	 - 一些呈现静态信息的页面，叫做文档（document）。
	 - DOM是一个使程序和脚本有能力动态的访问和更新文档的内容、结构以及样式的平台和语言中立的借口。
	 - DOM——文档对象模型，它代表和操作文档的内容。
	 - BOM定义了JavaScript可以进行操作的浏览器的各个功能部件的借口。
 2. window属于bom还是dom，document呢？
	 - window是BOM对象，而非JavaScript对象，不过恰好为EMCAscript中所定义的Global对象。
	 - 由于window包含了document，因此JavaScript可以直接通过使用window的document对象来访问、检索、修改文档内容与结构。
	 -  document对象又是DOM的根节点，所以可以理解为BOM包含了DOM。即浏览器提供出来给予访问的是BOM对象，而BOM对象再访问到DOM对象，从而js可以操作浏览器以及浏览器读取到的文档。 
 3. 熟悉window对象和document对象
	 - Window对象也是全局对象。Window对象处于作用域链的顶部，它的属性和方法实际上是全局变量和全局函数。Window对象有一个引用自身的属性，叫做window。
	 - Document对象表示显示在窗口中的文档。它有一些重要方法，如getElementById( )，可以基于元素id属性的值返回单一的文档元素。
 4. 获取dom节点的方式有哪些？举例
	```
		document.getElementById(elementId)
		document.getElementsByName(elementName)
		document.getElementsByTagName(tagName)
	```  
 5. 什么是html事件处理程序？
	- 事件处理程序是响应某个事件的函数：如onclick()；也称为事件侦听器。 
	- 类似onclick的事件处理程序属性，用相同名字对应到HTML属性，并且可以把JavaScript代码放在HTML属性里来定义事件处理程序。  
 6. 怎么执行一段js? 
	 -  JavaScript程序的执行有两个阶段。
	 -  第一阶段，载入文档内容，并执行`<script>`元素里的代码（包括内联脚本`<script>`和外部脚本src）。脚本通常按文档里出现的顺序执行。从上到下，按照它在条件、循环以及其他控制语句中的出现顺序执行。
	 -  第二阶段，文档加载完成，且所有脚本执行完成之后，这个阶段是一部的，且由事件驱动的。
	 -  事件驱动阶段，Web浏览器调用事件处理程序函数（第一阶段离得HTML事件处理程序，或之前调用的事件处理程序来定义），来响应异步发生的事件。通常是响应用户输入。也可以由网络活动、运行时间或者JavaScript代码中的错误来触发。
 7. dom的加载顺序？  
	 - 解析HTML结构。
	 - 加载外部脚本和样式表文件。
	 - 解析并执行脚本代码。
	 - 构造HTML DOM模型。
	 - 加载图片等外部文件。
	 - 页面加载完毕。
 8. 什么是同步加载脚本设备么是异步加载脚本，什么是延迟加载脚本？比较异同
	 - 脚本的执行只在默认情况下是同步和阻塞的。
	 - 延迟的脚本会按它们在文档里的出现顺序执行。
	 -  异步脚本在它们载入后执行，意味着脚本可能会无需执行。  
 9. 了解js的线程模式和执行时间线  
 10. 了解js的兼容性  
 11. 了解浏览器的同源策略
 12. 尝试写一个ajax去请求www.baidu.com这个页面，会不会成功，分析原因  
 13. 了解xss(跨站脚本)和dos（拒绝服务攻击）
	
 
##### 第十四章  
 1. setTimeout 和setInterval的异同
	 - 都可以用来注册在指定的时间之后单次或重复调用的函数。
	 - setTimeout( )和setInterval( )都返回一个值，分别可以传递给clearTimeout( )和clearInterval( )用于取消这个函数的执行。
	 - setInterval( )和setTimeout( )一样，只是前者会在指定的毫秒数的间隔里重复调用。
 2. 了解location对象 
 3. 了解Navigator对象
 4. 了解Screen对象
 5. 这章主要就是了解看看，不用记住，知道有这些玩意，这些玩意是干嘛的就够了
 
##### 第十五章  
 1. 获取dom节点
			1. 通过顶层document节点获取
		```
		document.getElementById(elementId)
		document.getElementsByName(elementName)
		document.getElementsByTagName(tagName)
		```
			2. 通过父节点获取
				```
				parentObj.firstChild;
				parentObj.lastChild;
				parentObj.childNodes ;
				parentObj.children;
				parentObj.getElementsByTagName(tagName);
				```
			3. 通过临近节点获取
				```
				neighbourNode.previousSibling;
				neighbourNode.nextSibling;
				```
			4. 通过子节点获取
				```
				childNode.parentNode ：获取已知节点的父节点。
				```
 2. 设置dom节点属性
	 - 表示HTML文档元素的HTMLElement对象定义了读/写属性，它们映射了元素的HTML属性。
	 - HTMLElement定义了通用的HTML属性（如id、标题lang和dir）的属性，以及事件处理程序属性（如onclick）。
	 - 特定的Element子类型为其父元素定义了特定的属性。如查询一张图片的URL，可以使用表示`<img>`元素的HTMLElement对象的src属性：
		```
			var image = document.getElementById("myimage");
			var imgurl = image.src;      //src属性是图片的URL
			image.id === "myimage"   //判定要查找图片的id
		```
	 - Element类型还定义了getAttribute( ) 和setAttribute( )方法来查询和设置非标准HTML属性，也可以用来查询和设置XML文档中元素上的属性。
 3. 设置标签css
	 - 通过CSS选择器选取元素
 4. 添加删除节点（**想在哪加就在哪加**）
	 - 插入节点即添加节点，可以用Node的appendChild( )方法或inserBefore( )将节点插入到文档中。
	 -  removeChild( )方法是从文档树中删除一个节点。父节点调用，删除子节点。 
 5. 创建节点 
	 - 创建新的Element节点可以使用document.createElement( )方法。
 6. 替换节点 
	 - replaceChild( )方法删除一个子节点并用一个新的节点取而代之。
 7. 学会使用节点片段（**DocumentFragment**）
	 - DocumentFragment是一种特殊的Node，它作为其他节点的一个临时的容器。它是独立的，其父节点总是null。
 8. 了解各种坐标
 9. 了解查询元素各种尺寸 
 10. 了解处理表单  
 11. 了解添加事件处理
 12. 这章同上，全是了解
 
##### 第十六章  
 1. 同上各种了解（要每一个字都看到，记不住没关系，要知道有）