### js相关特别用法

  1、判断对象是否为空 Object.keys(obj).length==0
  
  2、对象方法中的this指向这个对象

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
  3、

  

