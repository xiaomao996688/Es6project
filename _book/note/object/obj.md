##  es对象新增方法
- Object.is()
- Object.assign() //浅拷贝
- Object.keys() // 可遍历（enumerable）属性的键名。
- Object.values()
- Object.entries()  
- super 调用父级方法
- Object.setPrototypeOf()
- Object.getPrototypeOf()
新增for ... of方法
```js
var a = {} , b ={};
Object.is(a,b) // false
```
```js
let obj = {a:1};
// 指的是吧这个对象的地址给了另一个对象。
let a = Object.assign(obj,{b:2})
console.info(a); //{a:1,b:2}

let b = Object.keys(a); // a,b

let c = Object.values(a);//1,2
let d = Object.entries(a); //[["a","1"],["b","2"]]
```
```js
// for of无法循环遍历对象
let obj = [2,3,4]

for (let key of obj) {
	console.info(key); // 2,3,4
}

```
```js
// super
let  animal = {
	run () {
		return 'run'
	}
}
let cat = {
	__proto__: animal, // OR Object.setPrototypeOf()
	run() {
		console.log(super.run());
	}
}
// Object.setPrototypeOf(cat,animal)
// console.info(Object.getPrototypeOf(cat)); === animal
cat.run()

```