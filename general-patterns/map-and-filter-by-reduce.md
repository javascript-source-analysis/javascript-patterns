# 通过Reduce处理Map和Filter

```javascript
// 基础例子
const euro = [29.76, 41.85, 46.5]
const above30 = euro.reduce((total, amount) => {
  if (amount > 30) {
    total.push(amount)
  }
  return total
}, [])
console.log('above30', above30)

// 使用 async/await
async function foo() {
  try {
    var values = await getValues()
    return values.reduce(async function (values, value) {
      values = await values
      values.push(await asyncOperation(value))
      return values
    }, [])
  }
  catch (err) {
    console.log('We had an ', err)
  }
}
foo().then(console.log)
```

## 参考资料
- [https://medium.freecodecamp.org/reduce-f47a7da511a9](https://medium.freecodecamp.org/reduce-f47a7da511a9)
- [https://code.tutsplus.com/tutorials/a-primer-on-es7-async-functions--cms-22367](https://code.tutsplus.com/tutorials/a-primer-on-es7-async-functions--cms-22367)