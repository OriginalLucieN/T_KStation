## JS高级

一、原型：

```html
funtion Person(){

};

Person.prototype.name = 'xxx';

Person.prototype.age= 22;

Person.prototype.action= function(){

	console.log(this.name);

};

var person1 = new Person();

person1.name;
// 修改原型的属性
person1.__proto__.name = 'yyy';// 注意：直接修改原型的属性，所有原型 constructor构造函数指向的函数的属性都跟着改变。
var person2 = new Person();
console.log(Person.prototype.isPrototypeOf(person2));


// 混合使用构造函数和原型
function Person(name,age){
	this.name = name;
	this.age = age;
	//this.action = function(){
	//	return this.name;
	//}
}
Person.prototype.action = function(){
	return this.name;
}
var  aa = new Person('xxx',25);
console.log(aa.action());
```



二、继承：

```
function Action(){	

}

Action.prototype.canDo = function(){

	console.log('吃饭睡觉。。。');

}

function Ben(){}

Ben.prototype = new Action();

var aa = new Ben();

aa.canDo();



练习：
// call()   apply()
// call和apply的作用都是在特定的作用域中将函数绑定到另外一个对象上去运行，即可以用来重新定义函数的执行环境，两者仅在定义参数方式上有所区别
function ParentType(name,age){
	this.name = name;
	this.age = age;
};
ParentTyoe.prototype.getParentName = function(){
    return this.name;
}
function SonType(){
	ParentType.call(this,'xxx',32);  // 子类调用父类并传参
    this.name = 'tt';
}
SonType.prototype = new ParentType();
SonType.prototype.getSonName = function(){
    return this.name;
}
var aa = new SonType();
aa.name;
aa.age;
```









##### 闭包递归

```
闭包：
function checkScope(){
	var scope = 'son';
	return function sonScope(){
        var scope = 'son2';
        return scope;
	}
}
checkScope()();


var fun = (function checkScope(){
	var scope = 'son';
	return function sonScope(){
        var scope = 'son2';
        return scope;
	}
}());
fun();

// 传参
function setup(x){
    var i = 0;
    return function feedback(){
        return x[i++];
    }
}
var next = setup(['a','b','c']);
next();



递归： 自身调自身
function fact(num){
    if(num<=1){
        return 1;
    }else{
		return num * fact(num - 1);
	}
}
fact(4);
```

