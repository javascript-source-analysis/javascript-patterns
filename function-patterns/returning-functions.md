# 返回函数模式
一个函数返回其它函数或创建另一个函数

```javascript
var setup = function () {
  console.log(1)
  return function () {
    console.log(2)
  }
}
// 调用 setup 函数
var my = setup() // 1
my() // 2


// 您的setup 函数可以在闭包中存储一些私有数据，并以某种方式使用该数据。
// 你的 setup() 创建了一个计数函数。如下例子，它提供下一个id，但是count变量并未暴露。

var setup = function () {
  var count = 0
  return function () {
    return ++count
  }
}
// 用法
var next = setup()
//next(); // returns 1
//next(); // returns 2
//next(); // returns 3

var newCodes = function () {
  var dCodes = 'one'
  var dCodes2 = 'two'
  return [dCodes, dCodes2]
}

var codes = newCodes()
var dCodes = codes[0] //access the first
var dCodes2 = codes[1] //access the second

var newCodes = function () {
  var dCodes = 'one' // Linked ICDs  
  var dCodes2 = 'two' //Linked CPTs       
  return {
    dCodes: dCodes,
    dCodes2: dCodes2
  }
}

var codes = newCodes()
var dCodes = codes.dCodes //access the one called dcodes
var dCodes2 = codes.dCodes2 //access the one called dcodes2
```

## 参考资料
- [ http://www.jspatterns.com/returning-functions/]( http://www.jspatterns.com/returning-functions/)
