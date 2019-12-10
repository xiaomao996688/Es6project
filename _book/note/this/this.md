## this
this具体指向哪个对象是在运行时基于函数的执行环境动态绑定的
### this指向
大多数情况下
- 作为对象的方法调用
- 作为普通函数调用
- 作为构造器调用
- Function.prototype.call 或Function.prototype.apply 调用
1. 作为对象调用
函数作为对象的方法是被调用时，this指向该对象:
```js
var obj = {
	a: 1,
	getA: function () {
		console.info(this === obj);// true
		// this.a  === 1 //true
	}
}
obj.getA()
```
2. 作为普通函数调用
当函数不作为对象属性时，此时this指向全局对象，在浏览器中window，在node中global
```js
window.name = "globalName";
var getName = function (){
	return this.name ; //globalName
}
//OR
window.name = "globalName"
var myObj = {
	name: 's',
	getName: function () {
		return this.name; //s
	}
}
var getName = myObj.getName;
// getName() //globalName
```
demo 
在ECMAScript的strict模式下，这种情况下的this已经被规定为不会指向全局对象，而是undefined:
```js
	function fun(){
		'use strict'
		alert(this); //输出undefined
	}

```
3. 构造器调用
构造器里的this就指向返回的这个对象
```js

var MyClass = function () {
	this.name = 's'
}
var obj = new MyClass();
console.info(obj.name); // s
````
第二种情况 返回对象则不是this

```js
var MyClass = function () {
	this.name = 's'
	return {
		name:'a'
	}
}

var obj = new MyClass();
console.info(obj.name); // a
`````
第三种情况，构造器不显示返回任何对象
```js
var MyClass = function () {
	this.name = 's';
	return 'a';// 返回string类型
}
var obj = new MyClass 
console.log(obj.name); //s
```

4. Function.prototype.call 或者Function.prototype.apply调用
call与apply可以动态地改变传入函数的this:
```js
var obj1 = {
	name: 'a',
	getName: function () {
		return this.name;
	}
}
var obj2 = {
	name: 'b'
}
console.info(obj1.getName());//a
console.info(obj1.getName.call(obj2));//b
```

## 丢失this问题
```js

var obj = {
	name: 'a',
	getName: function () {
		return this.name
	}
}
console.info(obj.getName()); //a
var getName = obj.getName;
console.info(getName());//undefined
```