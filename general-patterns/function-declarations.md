# 函数声明
创建匿名函数并将它们分配给变量

## 反模式
```javascript
function getData() {}
```
> 但它有一个优点：可以在函数声明前调用它。

## 首选
```javascript
var getData = function() {};
```
优点：
- 让你更明白函数是一个对象
- 让你养成强制执行分号结尾的习惯（PS:个人认为知道何时追加分号比总是追加分号要好）
- 没有太多与函数功能及范围的历史包袱

## 命名函数表达式
```javascript
var getData = function getData() {};
```
优点：
- 为调试器提供显式函数名称：帮助堆栈检查
- [Can break IE, coffeescript doesn't do function names](https://github.com/jashkenas/coffee-script/issues/366)

## 命名函数表达式 + F
```javascript
var getData = function getDataF () {};
```
优点：
- 摆脱堆栈的跟踪（匿名函数）
- Doesn't break an IE (well, unless there's a function name collision of the sort described here: https://github.com/jashkenas/coffee-script/issues/366#issuecomment-242134)

## 参考资料
- [http://ejohn.org/blog/javascript-as-a-first-language/](http://ejohn.org/blog/javascript-as-a-first-language/)
- [http://kangax.github.com/nfe/](http://kangax.github.com/nfe/)