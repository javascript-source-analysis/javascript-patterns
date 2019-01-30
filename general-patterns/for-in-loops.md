# for-in循环

```javascript
// 声明一个对象
var man = {
	hands:2,
	legs:2,
	heads:1
};

// 添加一个方法到原始对象的原型中
if (typeof Object.prototype.clone === 'undefined') {
	Object.prototype.clone = function () {};
}

// 反模式，for-in循环时未用hasOwnProperty()进行校验是否自有属性
for (var i in man) {
	console.log(i, ":", man[i]);
}
/*
 * 控制台结果：
 * hands : 2
 * legs : 2
 * heads : 1
 * clone: function()
 */

// 优化-1
for (var i in man) {
	if (man.hasOwnProperty(i)) {
		console.log(i, ":", man[i]);
	}
}
/*
 * 控制台结果：
 * hands : 2
 * legs : 2
 * heads : 1
 */

// 优化-2，避免man的hasOwnProperty方法被改写引发问题
for (var i in man) {
	if (Object.prototype.hasOwnProperty.call(man, i)) {
		console.log(i, ":", man[i]);
	}
}

// 优化-3，缓存变量和`Object.prototype.hasOwnProperty`
var i, hasOwn = Object.prototype.hasOwnProperty;
for (i in man) {
	if (hasOwn.call(man, i)) {
		console.log(i, ":", man[i]);
	}
}

// 优化-4，通过`Object.keys(obj)`前置判断是否有自有属性需要处理，避免浪费资源来处理错误的大对象
if (Object.keys(man).length > 0){
	for (var item in man){
	  console.log(item,':',man[item]);
	}
} else { 
	console.log('Empty Object');
}
```

## 参考资料
- [http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/](http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/)