# 垫片嗅探

```javascript
// 反模式
Array.prototype.map = function() {}

// 好的
if (!Array.prototype.map) {
	Array.prototype.map = function() {}
}

// 更好的
if (typeof Array.prototype.map !== "function") {
	Array.prototype.map = function() {}
}

// 如果你想自己实现，你可以调用toString()，native函数它应该返回一个字符串
console.log(Array.prototype.map.toString().replace(/\s/g, '*'))
// "*function*map()*{*****[native*code]*}*"  // IE
// "function*map()*{*****[native*code]*}" // FF
// "function*map()*{*[native*code]*}" // Chrome

// 正常的检查可以修复这个问题
console.log(Array.prototype.map.toString().replace(/\s/g, ''))
// "functionmap(){[nativecode]}"

function shim(o, prop, fn) {
  var nbody = 'function' + prop + '(){[nativecode]}'
  if (o.hasOwnProperty(prop) &&
    o[prop].toString().replace(/\s/g, '') === nbody) {
    // native!
    return true
  }
  // shim
  o[prop] = fn
}
// 这是原生的
shim(
	Array.prototype, 'map',
	function(){/*...*/}
)

// 这是新增的
shim(
	Array.prototype, 'mapzer',
	function(){console.log(this)}
)
;[1,2,3].mapzer() // [1,2,3]
```

## 参考资料
- [http://www.jspatterns.com/shim-sniffing/](http://www.jspatterns.com/shim-sniffing/)