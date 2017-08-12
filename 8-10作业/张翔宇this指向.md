#this指向  
***  
#### js中的this指向十分重要，了解js中this指向是每一个学习js的人必学的知识点，今天没事，正好总结了js中this的常见用法，喜欢的可以看看：  

### 全局作用域或者普通函数中this指向全局对象window。  
    //直接打印
    console.log(this) //window
    //function声明函数
    function bar () {console.log(this)}bar()//window
    //function声明函数赋给变量
    var bar = function () {console.log(this)}bar()//window
    //自执行函数
    (function () {console.log(this)})(); //window  
### 方法调用中谁调用this指向谁  
    //对象方法调用  
    var person = {  
    	run: function () {console.log(this)}  
    }  
    person.run() // person  
      
    //事件绑定  
    var btn = document.querySelector("button")
	btn.onclick = function () {
    	console.log(this) // btn
    }  
      
    //事件监听  
    var btn = document.querySelector("button")
	btn.addEventListener('click', function () {
    	console.log(this) //btn
    })  
***  
### 在构造函数或者构造函数原型对象中this指向构造函数的实例  
    //不使用new指向window  
    function Person (name) {
    	console.log(this) // window
    	this.name = name;
	}
	Person('inwe')  
	
	//使用new  
	function Person (name) {
      this.name = name
      	console.log(this) //people
      	self = this
      }
      var people = new Person('iwen')  
       console.log(self === people) //true  
       //这里new改变了this指向，将this由window指向Person的实例对象people  
*** 
  
### 4.通过call/apply调用  
### call()方法  
    function Cat(name){ 
        this.name = name; 
    this.showName = function(){
        alert(this.name);
    }
    }
    function Dog(name){ 
        this.name = name; 
    }
    var cat = new Cat("小明");
    var dog = new Dog("小红"); 
    cat.showName.call(ming,"");
**原本执行结果应该弹出’小猫’，但是由于使用了call方法，相当于把cat下面的showName方法应用于dog,所以弹出的是‘小明'**  

### apply()方法  
    function fn1(a,b){  
       alert(this); 
       return a + b;  
    }
    console.log(fn1.apply(document,[5,6]))  
    弹出的是document，打印的数值为11
> 注意：  
	1.这里call()和apply()都是用来改变this指向的，两者的功能完全一样，只是参数不同      
	2.call第一个参数是this要指向的上下文，后面跟着的参数不固定，都是当成函数的参数传递进去  
	3.apply第一个参数也是this要指向的上下文，后面是一个数组或者类数组，数组的每一项按照顺序当成是函数的参数传递进去  
