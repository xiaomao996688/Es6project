## var let const 
- var 声明变量有预解析,let与const声明的变量没有预解析,不存在变量提升,所有会报错
- let和const不允许重复声明
- const与let 存在块级作用域内
- const 变量不得改变值(并不是变量的值不得改动，而是变量指向的那个内存地址所保存的数据不得改动。)
```js
{
	let a = 1;
}
{
	if (true) {
		tem = 'abc'
		let tem //执行报错tem not define
	}
}
{
	const a = 1;
	const a = 3; //报错
}
{
	const a = {
		c:3
	}
	a.c = 4; // 正确
}
````