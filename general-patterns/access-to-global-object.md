# 访问全局对象
访问不带硬编码处理的标识Window

```javascript
// 这种模式可以在ES3, ES5 and ES5-strict下正常运行
var global = (function (g) {
	return g;
})(this);
```

## 参考资料
- [http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/](http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/)