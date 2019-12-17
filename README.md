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

$(".selector").prop('selectedIndex', 0);  //选中第一个option
```

* jquery ajax

```javascript
$.ajax({

})
```

* jquery on('click')事件多次重复触发问题

```javascript
$(function(){
    $('#btn1').click(function () {
        $('#btnBind').on('click',function () {
            alert(123);
        });
    });
})
```

如上面的代码，如果你点击多次'btn1'按钮，那么就会绑定多少次click事件到'btnBind'按钮上，on是绑定多少次就触发多少次的。

要想它只绑定一次，可以先'off'然后再'on'。

```javascript
$(function(){
    $('#btn1').click(function () {
        $('#btnBind').off('click').on('click',function () {
            alert(123);
        });
    });
})
```

## js

* 时间戳与日期格式的相互转换

1.将时间戳转换成日期格式：

```javascript
function timestampToTime(timestamp) {
    var date = new Date(timestamp * 1000);//时间戳为10位需*1000，时间戳为13位的话不需乘1000
    Y = date.getFullYear() + '-';
    M = (date.getMonth()+1 < 10 ? '0'+(date.getMonth()+1) : date.getMonth()+1) + '-';
    D = date.getDate() + ' ';
    h = date.getHours() + ':';
    m = date.getMinutes() + ':';
    s = date.getSeconds();
    return Y+M+D+h+m+s;
}
timestampToTime(1403058804);
console.log(timestampToTime(1403058804));//2014-06-18 10:33:24
```

注意：如果是Unix时间戳记得乘以1000。比如：PHP函数time()获得的时间戳就要乘以1000。

2.将日期格式转换成时间戳：

```javascript
var date = new Date('2014-04-23 18:55:49');
// 有三种方式获取
var time1 = date.getTime();  //常用
var time2 = date.valueOf();
var time3 = Date.parse(date);
console.log(time1);//1398250549123
console.log(time2);//1398250549123
console.log(time3);//1398250549000
```

以上三种获取方式的区别：

第一、第二种：会精确到毫秒

第三种：只能精确到秒，毫秒用000替代

以上三个输出结果可观察其区别

注意：获取到的时间戳除以1000就可获得Unix时间戳，就可传值给后台得到。

## angularJs

* datetimepicker

angularjs里引入了bootstrap的日历插件datetimepicker，结果发现gulp打包之前没有问题，但gulp打包以后报错了，原因是jquery系列的js和angular系列的js都压缩到了1个js里，把jquery相关的js和angular相关的js分开压缩到两个js里就好了，顺序如下：

jquery相关js压缩成的js <br>
angular相关js压缩成的js <br>
datetimepicker相关js <br>
angular其他js（directives,service,controller等）

* select

1.数据格式为数组

```javascript
//html
<select ng-model="city" ng-options="c for c in cityList"></select>

//js
$scope.cityList = ["北京", "河北", "河南", "陕西"];

//select默认选中
$scope.city = "北京";
```

2.数据格式为数组对象

如果想要$scope.city的值是name，代码如下：

```javascript
//html
<select ng-model="city" ng-options="c.name as c.name for c in cityList"></select>

//js
$scope.cityList = [
    {"id": 1, "name": "北京"},
    {"id": 2, "name": "河北"},
    {"id": 3, "name": "河南"},
    {"id": 4, "name": "陕西"},
];

//select默认选中
$scope.city = "北京";
```

如果想要$scope.city的值是id，代码如下：

```javascript
//html
<select ng-model="city" ng-options="c.id as c.name for c in cityList"></select>

//js
$scope.cityList = [
    {"id": 1, "name": "北京"},
    {"id": 2, "name": "河北"},
    {"id": 3, "name": "河南"},
    {"id": 4, "name": "陕西"},
];

//select默认选中
$scope.city = 1;
```

3.数据格式为Key-Values数组对象格式

```javascript
//html
<select ng-model="site" ng-options="y.brand for (x, y) in cars"></select>

//js
$scope.cars = {
    car1 : {brand : "BYD", model : "Y50", color : "red"},
    car2 : {brand : "CC", model : "HF", color : "white"},
    car3 : {brand : "JL", model : "JL10D", color : "black"}
};

//select默认选中
$scope.site = "BYD";
```

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

* 文字截断在火狐浏览器不生效

word-break: break-all;在火狐浏览器不生效，原因是加在了span标签上不生效，加在div标签上就生效了。

* strong标签和b标签

strong标签表示加粗强调，b标签表示黑体，已被HTML4废弃，HTML5救回来表示关键字。

## 常见问题

* 当接口返回状态码为302时，浏览器会自动把post请求变为get请求

* 当form表单里只有一个input时，点击button按钮会自动提交表单，刷新页面

* 浏览器network中headers中的Response Headers是在服务器端设置的，Request Headers是前端可以通过ajax设置的

* Bootstrap弹出层model上自定义的弹出层中input输入框失效, 无法输入

做项目过程中，在model弹出层上面又自定义了一个弹出层，自定义弹出层上面有input输入框，但是却获取不了焦点，无法输入。网上找了下原因，这样说的：Bootstrap框架目前只支持一层model层，即当前model层上无法再用model弹出层。 最后找到了解决方案，将弹出层  最外层div的 tabindex属性去掉即可（如下面的代码示例，将tabindex这个属性去掉，不要改变其属性值，改变属性值是没用的）记录一下，免得以后忘记。

```javascript
<div class="modal fade" id="template-modal" tabindex="-1" role="dialog" aria-hidden="true">
```

## SVN

* 将online分支的代码合并到sprint分支

1. 进入到sprint分支的项目根目录，例如dev目录，鼠标右键 -> TortoiseSVN->Merge...

2. Merge type 勾选第一项 Merge a range of revisions -> next

3. URL to merge from 选择online分支的dev目录 -> specific range 点击 show log按钮 -> 勾选要合并的log -> next

4. 默认勾选Compare whitespaces 不用改变 -> Merge

5. 如果有冲突，会高亮显示，选择最后解决冲突

6. 解决冲突：选中冲突源文件-鼠标右键-TortoiseSVN-Edit conflicts (编辑冲突)，解决完冲突以后保存，选择 Mark as resolved

7. 解决完冲突以后提交


