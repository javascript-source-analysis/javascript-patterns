# switch模式
风格约定：
- 每个`case`与`switch`对齐
- 每个`case`语句中使用前代码缩进
- 每个`case`语句结尾有明确的break
- 避免使用fall-throughs(即有意不使用break，使程序按照顺序执行)。如果希望使用该模式，请在标注注明，避免给后来者造成疑惑。
- 用`default`语句作为结束，当所有`case`都不匹配时能有一个默认。

```javascript
// 反模式
var inspect_me = 0, result = ''
switch (inspect_me) {
  case 0:
    result = 'zero'
    break
  case 1:
    result = 'one'
    break
  default:
    result = 'unknown'
}

// 首选-1，因为它更快更容易重复使用和阅读
var results = {
  0: 'zero',
  1: 'one'
}
result = results[inspect_me] || 'unknown'

// 首选-2
var resultFuncs = {
  0: function () {
    return 'zero'
  },
  1: function () {
    return 'one'
  }
}

result = (resultFuncs[inspect_me] || function () {
  return 'unknown'
})()
```

## 参考资料
- [http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/](http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/)