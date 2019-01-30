# for 循环

```javascript
var myarray = []

// 次优
for (var i = 0; i < myarray.length; i++) {}

// 优化-1，缓存数组长度，
for (var i = 0, max = myarray.length; i < max; i++) {}

// 优化-2，单var模式。缺陷：拷贝代码片段的时候会有些麻烦。
var i, max
for (i = 0, max = myarray.length; i < max; i++) {}

// 优化-3，将`i++`替换为`i += 1`或`i = i+1`，避免这类诡异的写法
var i, max
for (i = 0, max = myarray.length; i < max; i += 1) {}

// 首选-1
var i
for (i = myarray.length; i--;) {}

// 首选-2
var i = myarray.length
while (i--) {}
```

## 参考资料
- http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/