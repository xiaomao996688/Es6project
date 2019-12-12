##set
set与数学中的集合相似,其中的元素可以是基本值类型。
 - add
 - size
 - delete
 - has
```js
let set = new Set();
// set可以使用forEach来遍历
set.add(1)
set.add(2)
set.add(3)
set.has(3)// true 
set.delete(3)//
set.forEach((item) => {
	console.info(item); // 1,2
})
```

## map
map与数学中的集合相似,其中的元素是以键值对的方式来存储的。
- set
- delete
- has
- get
- size
- clear
```js
let map = new Map();
// map可以使用forEach来遍历
map.set('a',1);
map.set('b',2);
map.set('c',3);
map.forEach((key,value) => {
	console.info(key,value); 
})
map.get('a');//1
map.has('a');// true
map.delete('a');
map.clear()
map.size()
// 1 'a'
// 2 'b'
// 3 'c'
```