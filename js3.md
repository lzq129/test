#####  第九章  
1. 创建一个对象有几种方式？分别实现
			1. 对象直接量创建
	`var point = { x: 0 , y: 0 };` 
			2. 关键字new创建
	`var o = new Object( );//创建一个空对象`
			3. Object.create( )创建
	`var o1 = Object.create( { x:1, y:1 } ) ;`
2. 创建一个类 ？并实例化一个对象
	- 如果定义了一个原型对象，然后通过inherit( )函数来创建一个继承自它的对象，这样就定义了一个JavaScript类。
	- 通常，类的实例还需要进一步的初始化，一般是通过定义一个函数来创建并初始化这个新对象。
	- 实例化对象一般通过关键字new实现。
3. 什么事构造函数？
	- 构造函数就是初始化一个实例对象，对象的prototype属性是继承一个实例对象。
	- 构造函数并没有显示返回任何东西。new 操作符会自动创建给定的类型并返回他们，当调用构造函数时，new会自动创建this对象，且类型就是构造函数类型。
	- 也可以在构造函数中显示调用return.如果返回的值是一个对象，它会代替新创建的对象实例返回。如果返回的值是一个原始类型，它会被忽略，新创建的实例会被返回。
	- 因为构造函数也是函数，所以可以直接被调用，但是它的返回值为undefine，此时构造函数里面的this对象等于全局this对象。this.name其实就是创建一个全局的变量name。在严格模式下，当你补通过new 调用Person构造函数会出现错误。
	- 也可以在构造函数中用Object.defineProperty()方法来初始化：
4. 什么事原型对象？
	- 每个构造函数都有一个原型属性prototype，默认的指向它的原型对象：该构造函数的prototype属性。
	- 原型对象的用途是为每个实例对象存储共享的方法和属性，它仅仅是一个普通对象而已。并且所有的实例是共享同一个原型对象，因此有别于实例方法或属性，原型对象仅有一份。
5. 类的继承有几种方式？分别实现（实现是网搜的，勉强能看懂）
	1. js原型实现继承

		```
		function Person(name,age)
		{  
	        this.name=name;  
	        this.age=age;  
		}  
		Person.prototype.sayHello=function()
	    {  
	        alert("使用原型得到Name："+this.name);  
	    }  
	    var per=new Person("asd",21);  
	    per.sayHello();
	     //输出：使用原型得到Name:asd  
	    
	    function Student(){}  
	    Student.prototype=new Person("as",21);  
	    var stu=new Student();  
	    Student.prototype.grade=5;  
	    Student.prototype.intr=function(){  
        alert(this.grade);  
	    }  
	    stu.sayHello();//输出：使用原型得到Name:as。
		```	
		
	2. 构造函数实现继承
	
		```
			function  Parent(name)
			{
				this.name=name; 
				this.sayParent=function()
				{
					alert("Parent:"+this.name);  
				}  
			}  

			function  Child(name,age)
			{
				this.tempMethod=Parent;  
				this.tempMethod(name);  
				this.age=age;  
				this.sayChild=function()
				{
					alert("Child:"+this.name+"age:"+this.age);  
				}
			}
			var parent=new Parent("江剑臣");  
			parent.sayParent(); 
			//输出：“Parent:江剑臣”  
			var child=new Child("李鸣",24);
		    child.sayChild();
		    //输出：“Child:李鸣 age:24”
		```
	3. call，apply实现继承
	
		```
		function  Person(name,age,love)
		{
	        this.name=name;  
	        this.age=age;  
	        this.love=love;  
	        this.say=function say()
	        {  
	            alert("姓名："+name);  
	        }  
	    }  

	    //call方式  
	    function student(name,age)
	    {  
	        Person.call(this,name,age);  
	    }  

	    //apply方式
	    function teacher(name,love)
	    {
		    Person.apply(this,[name,love]);  
			//Person.apply(this,arguments);
			//跟上句一样的效果，arguments  
	    }
		//call与aplly的异同:
		//1,第一个参数this都一样,指当前对象
		//2,第二个参数不一样：call的是一个个的参数列表；apply的是一个数组（arguments也可以）
	
		var per=new Person("武凤楼",25,"魏荧屏"); //输出：“武凤楼”  
	    per.say();  
	    var stu=new student("曹玉",18);//输出：“曹玉”  
	    stu.say();  
	    var tea=new teacher("秦杰",16);//输出：“秦杰”  
	    tea.say();
		```
6. 基于原型继承的类，如果改变原型，该类会不会发生改变？为啥？
	- 我觉得，会发生改变。
	- 毕竟基于原型继承的类，是通过原型链_ _proto_ _ 一层一层向上遍历并继承的，所以若是原型发生改变，那么原型的prototype属性必然发生变化，而原型的prototype属性变化则必然影响之后的类的继承。 
7. instanceof 干嘛的？
	- 检测对象是否属于某个类
	- 强化了“构造函数是类的公有标识”的概念
	- 检查的是构造函数的prototype属性。
	- 如果o继承自c.prototype，则表达式o instanceof c值为true。 
8. constructor是什么的属性？干嘛的？
	- constructor用来识别对象是否属于某个类。
	- 每个函数都有一个prototype属性，这个属性的值是一个对象，这个对象包含唯一一个不可枚举属性constructor，constructor属性的值是一个函数对象。
	- 对象继承的constructor均指代它们的构造函数。这个属性为对象提供了类。
		
		```
		var o =new F();
		//创建类F的一个对象
		o.constructor === F;
		//=>true，constructor属性指代这个类。
		```
9. 怎么设置一个类的私有方法或者属性？
	- 经典的面向对象编程中，经常需要将对象的某个状态封装或隐藏在对象内，只有通过对象的方法才能够访问这些状态，对外只暴露一些重要的状态变量可以直接读写。
	- 一般通过将变量（或参数）闭包在一个构造函数内来模拟实现私有实例字段，调用构造函数会创建一个实例。为此，需要在构造函数内部定义一个函数，并将这个函数赋值给新创建对象的属性。  
10. 构造函数怎么重载？
	- 通过重载这个构造函数方法来让它根据传入参数的不同，来执行不同的初始化方法。  
11. 了解工厂方法 
	- 一个类的方法用于返回类的一个实例。 
12. 怎么防止类的扩展？
	- Object.prevent Extensions( )可以讲对象设置为不可扩展。
	- Object.seal( )则更强大，除了能组织用户给对象添加新属性，还能将当前已有的属性设置为不可配置的，这样就不能删除这些属性了。 
13. 这章剩下的自己了解  这章很重要，不管看得懂看不懂，看完再说，看多了自然就懂了

#####  第十章  
1. 怎么定义一个正则表达式，2个方式
		1. 特殊的直接量语法
		`var pattern = /s$/;`
		2. 构造函数RegExp( )  
		`var pattern = new RegExp("s$");`
2. 什么叫贪婪和非贪婪模式？
	- 贪婪：尽可能多的匹配，且允许后续正则表达式继续匹配。
	- 非贪婪：尽可能少的匹配，匹配到结果就好。  
3. 什么是全局模式？
	- 末尾添加g，表示全局匹配。  
4. 什么是分组？
	- 将匹配的子字符串捕获到一个组名称或编号名称中。当获得匹配结果时，可以通过分组名进行获取。  
5. 什么是引用？ 
	- 通过在需要引用的字符或分组后加（“\”+“一位或多位数字” ）来实现的。
6. 正则有那些个方法？
	- test( ) 方法用于测试字符串参数中是否存正则表达式模式，如果存在则返回true，否则返回false
	- exec( ) 方法用于正则表达式模式在字符串中运行查找，如果 exec() 找到了匹配的文本，则返回一个结果数组。否则，返回 null。
	- search( ) 方法用于检索字符串中指定的子字符串，或检索与正则表达式相匹配的子字符串。
	- match( ) 方法将检索字符串 stringObject，以找到一个或多个与 regexp 匹配的文本。
	- repalce( ) 匹配并替换
	- split( ) 经常使用split方法把字符串分割为字符数组
7. 使用一个正则匹配
 `wefwefwe546wer54640wer068wer4035412wer00414rwer654r7144454`
 找出其中相同数字紧挨的最多的数字并匹配出来，比如`dd3333444hgff5` 相同数字紧挨最多的是3，是3333
	 - = =这个不会写。连续相同可以判别，问题是如果匹配最多的。
8. 匹配邮箱
	- `^[a-z0-9]+([._\\-]*[a-z0-9])*@([a-z0-9]+[-a-z0-9]*[a-z0-9]+.){1,63}[a-z0-9]+$ `
网搜的，叫我写我也写不出=. =。
9. 匹配ip
	-  (\d{1,3}\.){3}\d{1,3}是一个简单的IP地址匹配表达式。要理解这个表达式，请按下列顺序分析它：\d{1,3}匹配1到3位的数字，(\d{1,3}\.}{3}匹配三位数字加上一个英文句号(这个整体也就是这个分组)重复3次，最后再加上一个一到三位的数字(\d{1,3})。
	- 不幸的是，它也将匹配256.300.888.999这种不可能存在的IP地址(IP地址中每个数字都不能大于255)。如果能使用算术比较的话，或许能简单地解决这个问题，但是正则表达式中并不提供关于数学的任何功能，所以只能使用冗长的分组，选择，字符类来描述一个正确的IP地址：((2[0-4]\d|25[0-5]|[01]?\d\d?)\.){3}(2[0-4]\d|25[0-5]|[01]?\d\d?)。 

##### 第十一章  
1. 什么叫解构赋值？ 举个例子
	- 一种混合式赋值被称为解构赋值。
	- 解构赋值中，等号右侧是一个数组或对象（一个结构化的值），指定左侧一个或多个变量的语法和右侧的数组和对象直接量的语法保持格式一致。
	- 当发生解构赋值时，右侧的数组和对象中一个或多个的值就是被提取出来（解构）  ，并赋值给左侧相应的变量名。
	- 还用于初始化用var和let新声明的变量。
	
		```
		let [x,y] = [1,2];
		//等价于let x=1,y=2
		[x,y] = [x+1,y+1];
		//等价于x=x+1,y=y+1
		[x,y] = [y,x];//交换两个变量的值
		console.log([x,y]);//输出[3，2]
		```
2. 了解迭代器，和生成器  
	- 迭代器是一个对象允许它的值集合进行遍历，并保持任何必要的状态以使能够跟踪到当前遍历的“位置”。
	- 迭代器必须包含next( )方法，每次调用next( )都返回集合中的下一个值。
	- 生成器是一个对象，用以表示生成器函数的当前执行状态。它定义了一个next( )方法，后者后恢复生成器函数的执行，知道遇到下一条yield语句位置。此时，生成器中的yield语句的返回值就是生成器的next( )方法的返回值。
3. 剩下的了解同第九章一样，虽然不是很重要，但是对于js进阶是基础 
 
 ##### 第十二章
 1. 安装nodejs,并上网查询如何使
 2. 使用nodejs 输出hello,word
 3. 剩下的自己了解（nodejs安装包已经上传）
 **express没搞**