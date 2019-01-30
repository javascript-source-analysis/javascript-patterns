# 全局问题
问题在于这些全局性的变量在整个APP和WEB页面共享

```javascript
// 反模式-1，隐式的使用了全局变量
function sum(x, y) {
  result = x + y
  return result
}
// 首选-1
function sum(x, y) {
  var result = x + y
  return result
}

// 反模式-2，隐式的使用了全局变量
function fn() {
  var a = b = 0 // 即 var a = (b = 0)
}

// 首选-2
function fn() {
  var a, b
  a = b = 0
}
```

## 参考资料
- [http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/](http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/)