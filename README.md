### js相关特别用法

  1、判断对象是否为空 Object.keys(obj).length==0
  
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

  7、

  

