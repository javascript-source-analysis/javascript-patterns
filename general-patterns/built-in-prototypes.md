# 增强内置的原型
它会严重损害可维护性，因为它会降低您的代码的可预测性。下面情景可以考虑使用：
- 在未来的ECMAScript版本或JavaScript的具体实现可能将该功能作为统一的内置方法。
- 检测自定义属性或方法并未存在。也许其它地方实现了该方法，或是浏览器的JavaScript引擎的一部分。
- 你明确的用文档记录下来，并与团队交流清楚了。

```javascript
if (typeof Object.prototype.myMethod !== "function") {
	Object.prototype.myMethod = function () {}
}
```

## 参考资料
- [http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/](http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/)