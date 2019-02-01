# 回调模式
什么时候你将函数A通过参数形式传给函数B，并且被调用。这时函数A便是回调函数。

```javascript
var complexComputation = function () {}

var findNodes = function (callback) {
  var nodes = []
  var node = complexComputation()
  
  // 如果 callback 是可调用的函数，并调用它
  if (typeof callback === 'function') {
    callback(node)
  }
  
  nodes.push(node)
  return nodes
}

// 这是一个回调函数
var hide = function (node) {
  node.style.display = 'none'
}

// 找到节点通过回调函数隐藏它们
var hiddenNodes = findNodes(hide)

// 你也可以使用匿名函数，想这样
var blockNodes = findNodes(function (node) {
  node.style.display = 'block'
})
```

## 参考资料
- [http://www.jspatterns.com/](http://www.jspatterns.com/)
- [http://shop.oreilly.com/product/9780596806767.do?sortby=publicationDate](http://shop.oreilly.com/product/9780596806767.do?sortby=publicationDate)