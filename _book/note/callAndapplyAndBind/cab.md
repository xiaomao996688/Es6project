## 借用Array.prototype对象上的方法
注意：
1. 对象本身要可以存取属性
2. 借用和这个方法的对象的length属性可读写

```js
var obj = [1,2,3]

Array.protorype.push.call(obj,4)

```

## call 和 apply 和
call、bind和apply最常见的用途是改变函数内部的this指向
- call传递的第二个是单个参数，不能是数组或类数组、集合。
- apply的第二个参数必须是一个数组或者类数组或者集合
- 使用bind返回的仍然是一个函数，所以我们还可以在调用的时候再进行传参

```js
//  bind实现
Function.prototype.bind = function () {
	var self = this;
	// 拿到参数中的this
	var context = Array.prototype.shift.call(arguments);
	// 拿到剩余传递的参数
	var args = Array.prototype.slice.call(arguments);
	return function () {
		// 拿到传进来的this,拿到的参数与再次传进来的参数拼接起来
		self.apply(context,Array.prototype.concat(args, Array.prototype.slice.apply(arguments)))
		// 把this指向context
	}
}

```