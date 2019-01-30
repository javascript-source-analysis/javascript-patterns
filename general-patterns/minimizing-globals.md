# 最小化全局
```javascript
// 反模式
myglobal = 'hello' // antipattern
console.log(myglobal) // "hello"
console.log(window.myglobal) // "hello"
console.log(window['myglobal']) // "hello"
console.log(this.myglobal) // "hello"

// 使用一个对象储存所有信息
prefix_myglobal = {
  method: function () {},
  property: 'hello'
}
```

## 参考资料
- [http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/](http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/)