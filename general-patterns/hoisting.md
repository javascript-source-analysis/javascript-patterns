# 声明提升
```javascript
// 反模式
wontchange = 'global' // 全局变量
willchange = 'global' // 全局变量
function func_bad() {
  alert(wontchange) // "global"
  alert(willchange) // "undefined" (声明提升，但未赋值)
  var willchange = 'local' // 函数内创建同名的局部变量
  alert(willchange) // "local"
}
func_bad()

// 前面的代码实际运行如下
wontchange = 'global' // 全局变量
willchange = 'global' // 全局变量
function func() {
  var willchange // 声明提升，默认为 undefined
  alert(wontchange) // "global"
  alert(willchange) // "undefined"
  willchange = 'local'
  alert(willchange) // "local"
}
func()
```

## 参考资料
- [http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/](http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/)