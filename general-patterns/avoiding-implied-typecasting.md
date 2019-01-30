# 避免隐式转化

```javascript
var zero = 0
// 反模式，这就是为什么 false == 0,"" == 0 为true的原因
if (zero == false) {}

// 首选，总是使用 === or !== 来校验二者的值和类型
if (zero === false) {}
```
> 有些开发者认为使用`==`就足够了，而`===`显得多余。为了避免让人过多的思考`==`是否有意为之，尽量都使用`===`

## 参考资料
- [http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/](http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/)