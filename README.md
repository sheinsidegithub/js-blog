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
  
    function Car (name,price){
      this.name = name;
      this.price = price;
    }
    Car.prototype.sell = function(){
      alert("我是" + this.name + ",我现在卖" + this.price+"万元")
    } 

    

  

