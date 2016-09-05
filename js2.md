##### 第五章  
1. 条件语句有那些？怎么使用？
	1.  if语句
	```
	if( expression) 
		statement1
	else
		statement2
	//当expression为真值时执行statement1，反之，执行statement2。
	```
	
	2. else if语句
	```
	if (n==1) 
	{ 
	//执行代码块1 
	}
	else if (n==2) 
	{ 
	//执行代码块2 
	}
	else 
	{
	//之前的条件都为false时，执行此代码块
	}
	```
	
	3. switch语句
	```
	switch(n)
	{
	case 1://n===1,执行代码块1
	break;
	case 2://n===2,执行代码块2
	break;
	default://上述条件不匹配，执行此代码块
	break;
	}
	```

2. 循环语句有那些？怎么使用(**举例**) 
	1.  while语句
	```
	var count = 0;
	while ( count <10 )
	{
		console.log( count );
		count++;
	}
	```
	2.  for语句 
	```
	for (var i=1;i<5;i++)
	{
		var s = 0;
		s = s + i;
		return s;
	}
	//简单求和，s=1+2+3+4=10。
	```
	3. do/while语句
	```
	do
		statement
	while ( expression );
	//至少循环一次
	```
	4. for/in语句
	```
	for(variable in object)
		statement
	//variable通常是一个变量名
	for(var p in o)
		console.log(o[p]);
	//将属性名字赋值给变量p，之后输出每一个属性的值
	```
3. 跳转语句有哪些？怎么使用
	1. break语句
	```
	switch(n)
	{
	case 1://n===1,执行代码块1
	break;
	case 2://n===2,执行代码块2
	break;
	default://上述条件不匹配，执行此代码块
	break;
	}
	//只要不想继续执行整个循环，就可以用break来提前退出。
	```
	
	2. return语句
	```
	for (var i=1;i<5;i++)
	{
		var s = 0;
		s = s + i;
		return s;
	}
	//return语句让解释器跳出函数体的执行，并提供本次调用的返回值。
	```
	3. throw语句 
	```
	throw expression;//语法
	function factorial(x)
	{//如果输入参数是非法的，则抛出一个异常
		if(x<0) throw new Error("x不能使负数");
	//否则，计算出一个值，并正常的返回它
		for(var f=1;x>1;f*=x,x--)/*empty*/
		return f;
	} 
	```
4. return语句干嘛的 
- return语句让解释器跳出函数体的执行，并提供本次调用的返回值。 
5. throw语句干嘛的
- throw语句一般用来显式地抛出异常，可以抛出一个代表错误码的数字，也可以是包含可读的错误消息的字符串。  
6. js的异常处理机制是啥？
- 所谓异常时当发生了某种异常情况或错误时产生的一个信号。抛出异常，就是用信号通知发生了错误或异常情况。捕获异常是指处理这个信号，即采取必要的手段从异常中回复。
- 当抛出异常时，JavaScript解释器会立即停止当前正在执行的逻辑，并跳转至就近的异常处理程序。
- try/catch/finally语句是JavaScript的异常处理机制。
  
7. with、debugger/user strict语句干嘛的？
- with语句用于临时扩展作用链域。语法如下：
with(object)
statement;
- debugger语句用来产生一个断点，使JavaScript代码停止在断点的位置，这时可以使用调试器输出变量的值、检查调用栈等。
- use strict指令的目的是说明后续代码将会解析为严格代码。严格代码以严格模式执行。严格模式对语法的要求更为严苛。



##### 第六章  
1. 创建对象的方式有几种？分别用这几种方式创建对象 
	1. 对象直接量创建
	`var point = { x: 0 , y: 0 };` 
	2. 关键字new创建
	`var o = new Object( );//创建一个空对象`
	3. Object.create( )创建
	`var o1 = Object.create( { x:1, y:1 } ) ;`
2. 什么是对象的原型？
- 指向另外一个对象，本对象的属性继承自它的原型对象。  
- 所有通过对象直接量创建的对象都具有同一个原型对象，并可以通过JavaScript代码Object。prototype获得对原型对象的引用。通过关键字new和构造函数调用创建的对象的原型就是构造函数的prototype属性的值。
- 这一系列链接的原型对象就是所谓的“原型链”。
3. 对象怎么设置属性和查询属性？ 
-通过点（.）或方括号（[ ]）运算符来设置和查询属性。

	```
	var author = book.author;
	//得到book的"author"属性
	var name = author.surname;
	//得到获得author的"surname"属性
	var title = bool["main title"] ;
	//得到book的"main title"属性
	book.edition = 8;
	//给book创建一个名为"edition"的属性
	book["main title"] = "abc";
	//给"main title"属性赋值
	```
4. 怎么删除对象的属性？
- 使用delete运算符可以删除对象的属性。
 	`delete book.author;//bool不再有属性author`
 	
-   delete只是断开属性和宿主对象的联系，而不会去操作属性中的属性。
5. 怎么检查对象的属性是否存在？
- 对象可以看做属性的集合，通过检测集合中成员的所属关系——判断某个属性是否存在于某个对象中。可以通过in运算符、hasOwnPreperty( )和propertyIsEnumerable( )方法来完成这个工作，甚至仅通过属性查询也可以做到这一点。

		```
		var o = { x: undefined; }
		//属性被显示赋值为undefined
		o.x !== undefined;
		//false：属性存在，但值为undefined
		o.y !== undefined;
		//false：属性不存在
		"x" in o;
		//true：属性存在
		"y" in o;
		//false:属性不存在
		delete o.x;
		//删除属性x
		"x" in o;
		//false:属性不再存在
		```
6. 怎么枚举对象的属性？
- 通过for/in循环遍历对象中所有可枚举的属性，并把属性名称赋值给循环变量。对象继承的内置方法不可枚举的，但在代码中给对象添加的属性都是可枚举的。

		```
		var o = { x:1, y:2, z:3 };
		//三个可枚举的自有属性
		o.propertyIsEnumerable( "toString" );
		//false：不可枚举
		for(p in o) //遍历属性
		console.log(p);
		//输出x、y、z，不会输出toString
		``` 
- 另外两个用以枚举属性名称的函数：
		`Object.key()`
		`Object.getOwnPropertyNames()`
7. getter 和setter是啥？
- 由getter和setter定义的属性称作“存取器属性”。
- 调用getter( )查询存取器属性时，返回值就是属性存取表达式的值。
- 设置存取器属性的值时，调用setter( )，将赋值表达式右侧的值当做参数传入setter，可忽略返回值。
8. 什么是对象的原型属性？
- 对象的原型属性是用来继承属性的
- 原型属性是在实例对象创建之初就设置好的
- 通过对象直接量创建的对象使用Object.prototype作为它们的原型；new创建的则用构造函数的prototype属性作为原型；Object.create( )创建的对象则用第一个参数作为它们的原型。  
9. 什么是对象的类属性 ？
- 是一个标识对象类型的字符串。
- 想要获得对象的类，可以调用对象的toString( )方法，然后提取已返回的字符串的第8个到倒数第二个位置之间的字符。
- 此外，为保证正确性，还须间接地调用function call( )方法。
10. 对象与字符串互转的方式？
- 对象序列化指将对象的状态转换为字符串，也可以将字符串还原为对象。  

##### 第七章  
1. 创建数组的方式有那些？用这几种方式创建数组 
	1. 数组直接量创建
	`var a = [1,2,3,5,6,7];`
	2. new创建
	` var a = new Array(1,2,3,"a","c","b");`
2. 读写的创建的数组 

		```
		var a = ["world"];
		var value = a[0];//读第0个元素
		a[1] = 3.14;//写第1个元素
		i = 2;
		a[i] = 3;//写第2个元素
		a[i+1] = "hello";
		a[a[i]] = a[0];
		//读第0个和第2个元素，写第3个元素
		``` 
3. 数组的几种内置方法有那些？ 分别是干嘛的？
	1. 添加 
	- 向数组添加元素
					
			```
					var a = [];
					a[0] = "zero";
					a[1] = "one";
					a.push("two");
					//在数组末尾添加一个元素
			```
	2. 删除
	- 删除数组元素
	
			```
			var a = [1,2,3];
			delete a[1];
			1 in a;
			//false：数组索引1并未在数组中定义
			a.length;
			//=>3：delete操作不影响数组长度
			```
4. 怎么遍历数组？
	1. for循环
		
		```
		var keys = Object.keys(o);
		//获得o对象属性名组成的数组
		var values = [];
		for(var i=0;i<keys.length;i++)
		{
			var key = keys[i];
			//获得索引处的键值
			values[i] = o[key];
			//在values数组中保存属性值
		}  
		```
	2. for/in循环
	- 由于for/in循环能够枚举继承的属性名，在数组上不应该使用for/in循环。
	3. forEach( )方法
		
		```
		var data = [1,2,3,4,5];
		var sumOfSquares = 0;
		data.forEach(function(x)
		//把每个元素传递给此函数
		{
			sumOfSquares += x*x;//平方相加
		} );
		sumOfSquares;
		//=>55：1+4+9+16+25
		```
5. 多维数组的创建与读写？(**举例**)
	
	```
	//创建二维数组
	var table = new Array(10);
	for(var i=0;i<table.length;i++)
		table[i] = new Array(10);
	table[1][2] = 2;//写
	var s = table[0][0];//读
	```
6. 字符串是否可读写？
- 可读难写 
7. 什么叫类数组？
 - 从一个常规对象开始，增加了一些属性，称为类数组。
 - 拥有length属性，其它属性（索引）为非负整数(对象中的索引会被当做字符串来处理，可以当做是个非负整数串来理解)不具有数组所具有的方法
##### 第八章  
1. 函数怎么定义？
- 函数是参数化的，它只定义一次，但可以被执行或调用任意次；函数也是对象，程序可以随意操控它们。
- 函数由function关键字来定义，其后依次跟上函数名标识符，一对圆括号，一对花括号。
	`function a(x){//函数体 }//其中圆括号里是形参` 
2. 怎么嵌套函数？
- 将函数整个放入另一函数充当函数体就是嵌套函数。
- 嵌套函数的变量作用域规则：它们可以访问嵌套它们的函数的参数和变量。  
3. 怎么调用函数 ？
- 作为函数调用
- 作为方法调用
- 作为构造函数调用
- 通过它们的call( )和apply( )方法间接调用 
4. 什么叫方法？ 怎么调用方法？
- 一个方法无非是保存在一个对象的属性里的JavaScript函数。
- 通过实例对象完成对函数的调用的操作叫方法。
- 一般使用点"."或方括号"[ ]"进行调用；  
5. 什么叫构造函数调用 ？
- 如果函数或者方法调用之前带有关键字new，它就构成函数调用。
-  构造函数调用创建一个新的对象，这个对象继承自构造函数的prototype属性。
6. 怎么间接调用函数？  （**举例**）
- call( )和apply( )可以用来间接地调用函数。
- 任何函数可以作为任何对象的方法来调用。
		
		```
		f.call(o);
		f.apply(o);
		o.m = f;//将f存储为o的临时方法
		o.m( ); //调用它，不传入参数
		```
7. 什么叫实参什么叫形参？
- 实参即具有实际意义的值。
- 形参是虚假的不存在的值，只是表现形式是一个参数，但并无实际意义。  
8. 什么叫可选形参？
- 当调用函数的时候传入的实参比函数声明时指定的形参个数少，剩下的形参都将设置为undefined值。
- 需要给省略的参数赋一个合理的默认值。  
9. 怎么设置参数的默认值？
	
	```
	//将对象o中可枚举的属性名追加至数组a中，并返回这个数组a
	//如果省略a，则创建一个新数组并返回这个新数组
	function getPropertyNames(o,/*optional*/a)
	{
		a = a || [];//如果未定义，则使用新数组
		for(var property in o) 
			a.push(property);
			return a; 
	}  
	//这个函数调用可以传入1个或2个实参
	var a = getPropertyNames(o);//将o的属性存储到一个新数组中
	getPropertyNames(p,a);//将p的属性追加至数组a中
	```
10. 如果参数不定长怎么办？
- 在函数体内，标识符arguments是指向实参对象的引用，实参对象是一个类数组对象，这样可以通过数字下表就能访问传入函数的实参值，而不是一定要通过名字来得到实参。  
11. callee 是谁的属性？干嘛用的？
- callee是实参对象定义的属性
-  非严格模式下，callee属性指代当前正在执行的函数。
-  在匿名函数中可通过callee来地柜调用自身。
12. 参数列表过长一般都是怎么处理的？
- 通过名/值对的形式来传入参数。  
13. 什么叫闭包？  （**重点，这里要细读，我没法通过题目的测定你是否了解，但是这玩意必须要了解，我估计你目前看多少次都不会了解，至少要形成一个印象，以后时间久了自然就通了**）
- 闭包可以捕捉到单个函数调用的局部变量，并将这些局部变量用做私有状态。
- 闭包可以一直保存捕捉到的局部变量（和参数）。
- 一个函数作为返回值嵌套在另一个函数里面返回时，捕捉到的函数内部的局部变量（和参数）一直被保存下来，嵌套的函数及其外部函数组成的整体，姑且称之为闭包。
14. call和apply方法干嘛的？
- call( )和apply( )可以用来间接地调用函数。 
- 对于call( )来说，第一个调用上下文实参之后的所有实参就是要传入待调用函数的值。
- apply( )方法和call( )类似，但传入实参的形式和call( )有所不同，它的实参都放入一个数组当中。
`f.call(o,1,2)`
`f.apply(o,[1,2])`
15. bind方法干嘛的？
- 将函数绑定至某个对象。  
16. 什么叫高阶函数？
- 操作函数的函数称为高阶函数，它接收一个或多个函数作为参数，并返回一个新函数。  
17. 什么是不完全函数 ？
-  我们有一个函数 A，它会将传入的未知数量的部分参数保存起来，并返回另一个函数 B。当你呼叫函数 B 时，它会用这些保存了的参数呼叫函数 C。（网搜的解释）