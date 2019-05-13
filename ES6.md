# ES6

## 迭代器和for-of循环

### 1.for-of循环

```javascript
for (var value of myArray) {
  console.log(value);
}
```

* 这是最简洁、最直接的遍历数组元素的语法
* 这个方法避开了for-in循环的所有缺陷
* 与forEach()不同的是，它可以正确响应break、continue和return语句
