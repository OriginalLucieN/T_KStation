JS高级

一、面向对象之创建对象

1.var obj = new Object();通过new关键字创建

2.1var obj2 = {};对象字面量.简单字面量

obj2.name = 'xxx';

2.2var obj3 = 

{

​	name:'bobie',

​	age:25，

​	todo:function(){

​	},

​	address: 'zz'

} 嵌套字面量



3.构造函数

function Person(name,age){	

​	this.name = name;

​	this.age = age;

​	this.todo = function(){

​		return this.name;

​	}

}

var person = new Person('yl',25);实例化

person.todo();



// 构造函数和普通函数的区别

// this指向 -- 构造函数的this指向创建的对象实例上,普通函数指向函数的调用者

// 调用方式 -- 构造函数需要new实例化，普通函数直接调用你

//  命名方式 -- 构造函数首字母大写，普通函数遵循驼峰命名法即可



二、面向对象之属性

var obj  = {};

obj  .name = 'xxx';

1.属性、属性的删除

属性的获取和设置 -- . / [] （区别：.是取自身属性，[]可以是变量）

属性的删除 -- delete obj.name



2.属性的检测

2.1 in 运算符

console.log('name' in obj); // 返回 false/true

2.2 hasOwnProperty()

console.log(o.hasOwnProperty('name')); // 返回 false/true

2.3 != undefined  / !==undefined 

console.log(o.name !== undefined); // 不准确 (例如：obj.name = 'undefined')



3.枚举属性

// for in 

var o  = {x:1,y:2,z:3}

for(var a in o){console.log(a);} // x,y,z

for(var a in o){console.log(o[a]);} // 1,2,3



4.序列化对象

