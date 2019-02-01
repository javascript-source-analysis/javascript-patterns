# Curry函数
用于通过在ECMAScript 5中部分应用一组参数来动态创建新函数，您可以使用bind来实现curring。

```javascript
/***
* 功能应用
***/

// 定义一个函数
var sayHi = function (who) {
	return 'Hello' + (who ? ', ' + who : '') + '!'
}

// 调用函数
sayHi() // "Hello!"
sayHi('world') // "Hello, world!"

// 使用 apply 调用函数
sayHi.apply(null, ['hello']) // "Hello, hello!"

var alien = {
  sayHi: function (who) {
    return 'Hello' + (who ? ', ' + who : '') + '!'
  }
}

alien.sayHi('world') // "Hello, world!"
sayHi.apply(alien, ['humans']) // "Hello, humans!"

// 第二种方式更优秀，减少数组的使用
sayHi.apply(alien, ['humans']) // "Hello, humans!"
sayHi.call(alien, 'humans') // "Hello, humans!"

/***
* 局部应用
***/

// 出于演示目的的无效JavaScript
function add(x, y) {
  return x + y
}

// 我们知道参数
add(5, 4)

// 第一步替换一个参数
function add(5, y) {
  return 5 + y
}

// 第二部替换另一个参数
function add(5, 4) {
  return 5 + 4
}

/***
 currying
 ***/

// 一个curry函数 add()，接受异步的列表参数
function add(x, y) {
  var oldx = x, oldy = y
  if (typeof oldy === 'undefined') { // 局部
    return function (newy) {
      return oldx + newy
    }
  }
  // 完成的功能
  return x + y
}

// 测试
typeof add(5) // "function"
add(3)(4) // 7

// 创建并存储新函数
var add2000 = add(2000)
add2000(10) // 2010

function schonfinkelize(fn) {
  var slice = Array.prototype.slice,
    stored_args = slice.call(arguments, 1)
  return function () {
    var new_args = slice.call(arguments),
      args = stored_args.concat(new_args)
    return fn.apply(null, args)
  }
}

/**
* 这是一个普通的 curry 函数(from kybernetikos)：
* 它比currying的常见例子稍微复杂一些（例如上面的例子），但因为那样，之后便可以以正常方式或以curry方式调用该函数。
* 如果用它调用3次curried函数，返回的函数也是curry函数。
* 例如可以这么写：func(arg1)(arg2)(arg3) 或 func(arg1, arg2, arg3) 或 func(arg1)(arg2, arg3) 等等...
*/

// curry过程需要知道在计算结果之前需要多少个参数
function curry(func, minArgs) {
  if (minArgs == undefined) {
    minArgs = 1
  }
  
  function funcWithArgsFrozen(frozenargs) {
    return function () {
      // 可以在这里进行优化 - 如果没有参数调用,可以返回这个函数
      var args = Array.prototype.slice.call(arguments)
      var newArgs = frozenargs.concat(args)
      if (newArgs.length >= minArgs) {
        return func.apply(this, newArgs)
      }
      else {
        return funcWithArgsFrozen(newArgs)
      }
    }
  }
  
  return funcWithArgsFrozen([])
}

/* * 
* 下面是一些示例用法
* 我使用这些函数在js中实现的函数不可变列表结构，但它们也适用于数组上的普通高阶函数。
* */

var plus = curry(function () {
  var result = 0
  for (var i = 0; i < arguments.length; ++i) {
    result += arguments[i]
  }
  return result
}, 2)

/* 现在你能这么调用
 plus(3,2)         // 正常调用
 plus(3)           // 局部应用 (返回一个向其参数添加3的函数)
 plus(3)(2)        // 完整的应用 (returns 5)
 plus()(3)()()(2)  // returns 5
 plus(3, 2, 4, 5)  // 正常调用可以选择超过最小参数数量
 plus(3)(2, 3, 5)  // 最后这样应用也可以
 */

var minus = curry(function (x) {
  var result = x
  for (var i = 1; i < arguments.length; ++i) {
    result -= arguments[i]
  }
  return result
}, 2)

/**
* 翻转切换函数前两个参数的顺序。它本身就是curry的，它返回的功能也是curry的。如果你想要一个相减数字的函数，它会特别有用
**/

var flip = curry(function (func) {
  return curry(function (a, b) {
    return func(b, a)
  }, 2)
})

/**
* 例子
* minus(5) // returns a function that takes its argument away from 5
* flip(minus)(5) // returns a function that takes 5 away from its argument
 */
```

## 参考资料
- [http://www.jspatterns.com/](http://www.jspatterns.com/)
- [http://shop.oreilly.com/product/9780596806767.do?sortby=publicationDate](http://shop.oreilly.com/product/9780596806767.do?sortby=publicationDate)
