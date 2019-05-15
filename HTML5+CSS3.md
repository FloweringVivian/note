# HTML5 + CSS3

### 1.媒体查询

```javascript
body {
  background-color: #f00;
}
@media screen and (min-width: 960px) and (max-width: 1080px) {
  body {
    background-color: #0f0;
  }
}
@media screen and (max-device-width: 960px) {
  body {
    background-color: #0f0;
  }
}
```

媒体查询能检测哪些特性？最常用的就是以下4个：

* width: 视口宽度
* height: 视口高度
* device-width: 设备屏幕的宽度
* device-height: 设备屏幕的高度

移动端页面需要加入meta标签，控制浏览器按照其视口的实际大小来渲染页面

```javascript
<meta name="viewport" content="width=device-width,initial-scale=1.0">
```

禁止用户缩放：

```javascript
<meta name="viewport" content="initial-scale=1.0,user-scalable=no">
```

