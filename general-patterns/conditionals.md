# 条件语句
使用 `if` `else` 的模式及反模式

```javascript
// 普通模式
if (type === 'foo' || type === 'bar') {}

// 替代方案-1，正则
if (/^(foo|bar)$/.test(type)) {}

// 替代方案-2，对象查找（当if < 5时较优）
if (({foo:1, bar:1})[type]) {}

// 替代方案-3，二分查找法。当存在查找范围值时，这个方法最优
if (value < 6) {
  if (value < 3) {
    if (value == 0) {
      return result0
    }
    else if (value == 1) {
      return result1
    }
    else {
      return result2
    }
  }
  else {
    if (value == 3) {
      return result3
    }
    else if (value == 4) {
      return result4
    }
    else {
      return result5
    }
  }
}
else {
  if (value < 8) {
    if (value == 6) {
      return result6
    }
    else {
      return result7
    }
  }
  else {
    if (value == 8) {
      return result8
    }
    else if (value == 9) {
      return result9
    }
    else {
      return result10
    }
  }
}
	
// 替代方案-4，对象/数组查表法。当单个键和单个值之间存在逻辑映射时最有用
if (value == 0) {
  return result0
}
else if (value == 1) {
  return result1
}
else if (value == 2) {
  return result2
}
// 转为
var results = [result0, result1, result2]
return results[value]

// 替代方案-5，禁用逻辑运算符简化简单语句
var type = 'foo', type2 = 'bar', result = 0
type == 'foo' && result++
console.log(result) // 1
!type == 'foo' || result++
console.log(result) // 2
type == 'foo' && type2 == 'bar' && result++
console.log(result) // 3
type == 'foo' && type2 == 'bar' && result == 3 && (result = 0) // 使用括号包裹，避免无效的赋值
console.log(result) // 0
type == 'OOF' || result++ //等价于: type != 'OOF' && result++;
console.log(result) // 1			
```
> 性能测试：[http://jsperf.com/if-this-or-that](http://jsperf.com/if-this-or-that)

## 参考资料
- [http://paulirish.com/2009/perf/](http://paulirish.com/2009/perf/)