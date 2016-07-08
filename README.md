### js相关特别用法

  1、判断对象是否为空 Object.keys(obj).length==0, 

    Object.prototype.toString.call(2) // "[object Number]"
    Object.prototype.toString.call('') // "[object String]"
    Object.prototype.toString.call(true) // "[object Boolean]"
    Object.prototype.toString.call(undefined) // "[object Undefined]"
    Object.prototype.toString.call(null) // "[object Null]"
    Object.prototype.toString.call(Math) // "[object Math]"
    Object.prototype.toString.call({}) // "[object Object]"
    Object.prototype.toString.call([]) // "[object Array]"

    var type = function (o){
      var s = Object.prototype.toString.call(o);
      return s.match(/\[object (.*?)\]/)[1].toLowerCase();
    };

    type({}); // "object"
    type([]); // "array"
    type(5); // "number"
    type(null); // "null"
    type(); // "undefined"
    type(/abcd/); // "regex"
    type(new Date()); // "date"
  
  2、对象方法中的this指向这个对象,闭包函数指向window

    var myobj = {
    	foo : "bar",
    	func : function () {
    		var self = this;
    		console.log(this.foo);//bar
    		console.log(self.foo);//bar
    		(function (){
    			console.log(this.foo);//undefined
    			console.log(self.foo);//bar
    		}())
    	}
    };
    myobj.func();
    
  3、创建对象的几种方法

    混合方式创建
    function Car (name,price){
      this.name = name;
      this.price = price;
    }
    Car.prototype.sell = function(){
      alert("我是" + this.name + ",我现在卖" + this.price+"万元")
    } 
    var camry = new Car('凯美瑞'，27)；
    camry.sell();

    原型方式创建
    function Dog(){
      
    }
    Dog.prototype.name = "旺财";
    Dog.prototype.eat = function(){
      alert(this.name + "是个吃货");
    }
    var wangcai = Dog();
    wangcai.eat();

    对象字面量方式
    Person = {firstname:"Mark",lastname:"yun",age:25,eyecolor:"black"};
    
  4、变量对象(VO),是一个与执行上下文相关的特殊对象，它存储着在上下文中声明的以下内容。

    变量 (var, 变量声明);
    函数声明 (FunctionDeclaration, 缩写为FD);
    函数的形参
    
  5、变量对象 分为全局上下文变量对象跟函数上下文变量对象。

    全局上下文变量对象 
    (VO === this === global)
    函数上下文变量对象 
    (VO === AO, 并且添加了<arguments>和<formal parameters>)，Arguments有三个属性，callee ,length ,properties-indexes
    
  6、变量必须要用var声明,如果没有用var 声明的，只不过是window的一个属性罢了，属性可以用delete直接删除，而用var声明的变量不可以用delete直接删除。
  
  7、函数声明可以覆盖变量声明，如果变量声明并且复制，则不能被函数声明所覆盖
  
  8、js事件 addEventListener是推荐的指定监听函数的方法。它有如下优点：http://javascript.ruanyifeng.com/dom/event.html#toc0

    可以针对同一个事件，添加多个监听函数。
    能够指定在哪个阶段（捕获阶段还是冒泡阶段）触发回监听函数。false,冒泡阶段，true捕获阶段，其他事件监听都是处于冒泡阶段
    除了DOM节点，还可以部署在window、XMLHttpRequest等对象上面，等于统一了整个JavaScript的监听函数接口。
    
  9、事件传播的三个阶段 事件传播的最上层对象是window，接着依次是document，html（document.documentElement）和body（document.dody）

    第一阶段：从window对象传导到目标节点，称为“捕获阶段”（capture phase）。
    第二阶段：在目标节点上触发，称为“目标阶段”（target phase）。
    第三阶段：从目标节点传导回window对象，称为“冒泡阶段”（bubbling phase）。
    
  10、Array.prototype.slice.call(div_list) 将伪数组转化为真正的数组；
    
  
  
    

  

