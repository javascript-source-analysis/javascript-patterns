# iife(自执行匿名函数)for循环

```javascript
// 定期输出 i, 但都为5
for (var i = 0; i < 5; i++) {
  setTimeout(function () {
    console.log('regular loop', i)
  }, 3000)
}

// 定期输出 i, 从0-4
for (var i = 0; i < 5; i++) {
  (function (n) {
    setTimeout(function () {
      console.log('iife loop', n)
    }, 3000)
  })(i)
}

// 改用let声明变量, 定期输出 i, 从0-4。需要ES2015支持
for (let i = 0; i < 5; i++) {
  setTimeout(function () {
    console.log('let loop', i)
  }, 1000)
}
```

## 参考资料
- [http://benalman.com/news/2010/11/immediately-invoked-function-expression/](http://benalman.com/news/2010/11/immediately-invoked-function-expression/)