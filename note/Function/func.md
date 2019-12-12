## 函数
- 参数可以加默认值
- 剩余操作符
- name返回函数的名称
- 结构赋值
- 展开操作符

```js

function b(a = 1) {
	return a;
}
b() //1
b(2)  //2
b.name //b
```

```js
function func ({a, b}){
	console.info(a,b);  //1,2
}
func({a:1,b:2})
```

```js
function a({a = 1, b}){
	console.info(a,b); //2,3
}
a(2,3)
```

```js
let a = {a:1, b:2}
let b = {c:3, d:4}
let c = {...a,...b}

```
{a:1, b:2,c:3, d:4}
## 箭头函数
-  [this]问题 指向上当前对象外。

```js
let a = (a)=> {
	console.info(a); //1
}
a(1);

```