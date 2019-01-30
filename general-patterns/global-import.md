# 全局导入对象问题
通过自执行函数，你可以往内部传入全局对象

```javascript
(function ($, YAHOO) {}(jQuery, YAHOO))
```

## 参考资料
- [http://www.adequatelygood.com/JavaScript-Module-Pattern-In-Depth.html](http://www.adequatelygood.com/JavaScript-Module-Pattern-In-Depth.html)