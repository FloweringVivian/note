# HTML5 + CSS3

### 1.媒体查询

```javascript
body {
  background-color: #f00;
}
@media screen and (max-width: 960px) {
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
