# 单var模式
使用一个`var`声明多个变量。优点如下：
- 提供单一的地址查找函数所有局部变量
- 防止变量定义前被使用的逻辑错误
- 帮助您记住声明变量，从而最大限度地减少全局变量
- 更少的代码量

```javascript
function func() {
	var a = 1
		, b = 2
		, sum = a + b
		, myobject = {}
		, i
		, j;
	// function body...
}
```
> 将逗号前置编写，避免结尾逗号忘加的情况。

## 参考资料
- [http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/](http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/)