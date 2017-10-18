## 移动端

* 移动端弹层水平垂直居中方法

```javascript
.layer{
    position: fixed;
    left: 50%;
    top: 50%;
    -webkit-transform: translate(-50%, -50%);
    -moz-transform: translate(-50%, -50%);
    -o-transform: translate(-50%, -50%);
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
}
```

## jquery

* jquery阻止事件冒泡

```javascript
event.stopPropagation();
```

* jquery判断是否显示或隐藏

```javascript
if($("#test").is(':visible')){...}  //是否显示

if($("#test").is(":hidden")){...}  //是否隐藏
```
