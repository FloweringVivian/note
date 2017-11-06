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

* 移动端弹层从右往左划出效果CSS实现

```javascript
.layer{
    position: fixed;
    right: 0;
    top: 0;
    -webkit-transition: all .3s ease-in-out;
    transition: all .3s ease-in-out;
    -webkit-transform: translateX(100%);
    transform: translateX(100%);
}
.layer.in{
    -webkit-transform: translateY(0);
    transform: translateY(0);
    -webkit-transform: translateX(0);
    transform: translateX(0);
}
```

* 移动端弹层从下往上划出效果CSS实现

```javascript
.layer{
    position: fixed;
    bottom: 0;
    left: 0;
    -webkit-transition: all .3s ease-in-out;
    transition: all .3s ease-in-out;
    -webkit-transform: translateY(100%);
    transform: translateY(100%);
}
.layer.in{
    -webkit-transform: translateX(0);
    transform: translateX(0);
    -webkit-transform: translateY(0);
    transform: translateY(0);
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

* jquery select操作

```javascript
$(".selector").val("pxx");  //设置value为pxx的项选中

$(".selector").find("option[text='pxx']").prop("selected",true);  //设置text为pxx的项选中

$(".selector").val();  //获取当前选中项的value

$(".selector").find("option:selected").text();  //获取当前选中项的text
```

## angularJs

* datetimepicker

angularjs里引入了bootstrap的日历插件datetimepicker，结果发现gulp打包之前没有问题，但gulp打包以后报错了，原因是jquery系列的js和angular系列的js都压缩到了1个js里，把jquery相关的js和angular相关的js分开压缩到两个js里就好了，顺序如下：

jquery相关js压缩成的js <br>
angular相关js压缩成的js <br>
datetimepicker相关js <br>
angular其他js（directives,service,controller等）

* select



## CSS

* 去掉谷歌浏览器input记住账号或密码时默认出现的黄色背景

直接用css的内阴影来覆盖黄色

```javascript
input:-webkit-autofill { 
    -webkit-box-shadow: 0 0 0px 1000px white inset; 
} 
```

如果要关闭form表单的自动填充功能，加autocomplete="off"，不过有时不管用。

* table表格固定列宽

```javascript
table{
    table-layout:fixed;
}
```








