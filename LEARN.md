# 极客时间：重学前端 笔记

## 模块一：javascript

### 1.为什么在 JavaScript 中，0.1+0.2 不能 = 0.3

```javascript
console.log( 0.1 + 0.2 == 0.3)
>false
```

所以实际上，这里错误的不是结论，而是比较的方法，正确的比较方法是使用 JavaScript 提供的最小精度值：

检查等式左右两边差的绝对值是否小于最小精度，才是正确的比较浮点数的方法。这段代码结果就是 true 了。

```javascript
console.log( Math.abs(0.1 + 0.2 - 0.3) <= Number.EPSILON)
```

