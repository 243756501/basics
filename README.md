###


ajax.html    -  ajax深入
array.html   -  常规数组操作
basic.html   -  常用工具方法




###知识拓展
---
#网站优化

图片懒加载
图片sprite
css合并
js合并
数据本地存储
数据网络缓存
---

---
#常见问题
移动端1像素边框问题
收到分辨率DPI差异 高清手机屏幕上1px由2x2像素甚至更多来渲染的

用transform:scale来进行缩放
.border-bottom::after {
    content: " ";
    position: absolute;
    left: 0;
    bottom: 0;
    width: 100%;
    height: 1px;
    background-color: #e4e4e4;
    -webkit-transform-origin: left bottom;
    transform-origin: left bottom;
}
//然后通过媒体查询来适配
/* 2倍屏 */
@media only screen and (-webkit-min-device-pixel-ratio: 2.0) {
    .border-bottom::after {
        -webkit-transform: scaleY(0.5);
        transform: scaleY(0.5);
    }
}

/* 3倍屏 */
@media only screen and (-webkit-min-device-pixel-ratio: 3.0) {
    .border-bottom::after {
        -webkit-transform: scaleY(0.33);
        transform: scaleY(0.33);
    }
}

或者采用viewport,js获取设备像素比 动态创建meta标签

   (function() {
       var scale = 1.0;
       if (window.devicePixelRatio === 2) {
           scale *= 0.5;
       }
       if (window.devicePixelRatio === 3) {
           scale *= 0.333333;
       }
       var text = '<meta name="viewport" content="initial-scale=' + scale + ', maximum-scale=' + scale +', minimum-scale=' + scale + ', width=device-width, user-scalable=no" />';
       document.write(text);       
    })();
---


---

#HTML5新增api

document.querySelector()和document.querySelectorAll()方法

根据css选择器找到对应元素,前者返回单个元素,后者返回元素数组

classList属性

之前js操作class属性常用className,classList属性提供便捷的操作方法
ul.classList.item(index)  //返回对应位置的class名称
ul.classList.add("className")  //添加class,并不是覆盖的操作
ul.classList.remove("className") //删除class
ul.classList.contains("className")  //判断是否含有某个class

全屏 FullScreen

document.documentElement
//全屏
requestFullscreen()
mozRequestFullScreen()
webkitRequestFullscreen()
msRequestFullscreen()
//退出全屏 只能通过document对象调用
document.exitFullscreen()
mozExitFullScreen()
webkitExitFullscreen();

页面可见性

可监听对应事件
visibilitychange mozvisibilitychange webkitvisibilitychange msvisibilitychange

预加载

类似于mui的预加载 其原理都是预先加载 快速呈现
---

---
#基础扫盲
行内元素和块级元素
关键是否占一行 有两个元素自动换行

行内
span a br img input label textarea...
块级
div dl  p ul li form h1 hr...


数组深浅拷贝
对于字符串类型，浅复制是对值的复制，
对于对象来说，浅复制是对对象地址的复制，并没   有开辟新的栈，也就是复制的结果是两个对象指向同一个地址，修改其中一个对象的属性，则另一个对象的属性也会改变，
而深复制则是开辟新的栈，两个对象对应两个不同的地址，修改一个对象的属性，不会改变另一个对象的属性。


---