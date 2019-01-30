# 使用parseInt()进行数字转化

```javascript
// 模式-1，ECMAScript 5指定默认使用10（十进制），但并非所有浏览器都支持此功能。因此，在使用parseInt时始终指定基数
var month = '06', year = '09'
month = parseInt(month, 8) // 6
year = parseInt(year, 8) // 0
month = parseInt(month, 10) // 6
year = parseInt(year, 10) // 9

// 模式-2，单纯转化数字性的字符串，使用下面方式更方便
+"08" // 8
Number("08") // 8

// 模式-3，位运算符解析数值类型和数值字符串，遇见其它字符则输出 0
("789"|0) // => 789
("sds"|0) // => 0
(8.45|0) // => 8
("8.55"|0) // => 8
```

## 参考资料
- [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt)
- [http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/](http://net.tutsplus.com/tutorials/javascript-ajax/the-essentials-of-writing-high-quality-javascript/)