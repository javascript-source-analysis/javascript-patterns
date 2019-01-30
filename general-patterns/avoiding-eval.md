# 避免使用 eval()

```javascript
// 反模式-1
var property = "name", obj = { name: "John" }
alert(eval("obj." + property))

// 首选-1
alert(obj[property])

// 反模式-2
setTimeout("myFunc()", 1000)
setTimeout("myFunc(1, 2, 3)", 1000)

// 首选-2
setTimeout(myFunc, 1000)
setTimeout(function () {
	myFunc(1, 2, 3)
}, 1000)
// 在支持的浏览器 (i.e. 非 IE)
setTimeout(myFunc, 1000, 1, 2, 3)
```

## 参考资料
- [http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/](http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/)