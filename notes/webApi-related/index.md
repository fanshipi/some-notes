# Basic

**intersection observer**

浏览器提供了这 5 种 Observer：

IntersectionObserver：监听元素可见性变化，常用来做元素显示的数据采集、图片的懒加载
MutationObserver：监听元素属性和子节点变化，比如可以用来做去不掉的水印
ResizeObserver：监听元素大小变化

还有两个与元素无关的：

PerformanceObserver：监听 performance 记录的行为，来上报数据
ReportingObserver：监听过时的 api、浏览器的一些干预行为的报告，可以让我们更全面的了解网页 app 的运行情况

intersectionObserver可以监听视图在视口中的出现与消失. 例如滚动到一个元素(或者多个元素)出现时, observer可以监听到在视口中发生变化的视图(可对比mutation observer:可以监听对元素的属性修改, 对它的子节点的增删改).

代码块：

```
css

#top {
    height: 2000px;
}

#center-left {
    height: 1000px;
    width: 48%;
    display: inline-block;
    background-color: rgb(180, 84, 84);
}

#center-right {
    height: 1000px;
    width: 48%;
    display: inline-block;
    background-color: rgb(142, 117, 117);
}

#bottom {
    height: 300px;
    background-color: rgb(81, 21, 21);
}

html

<div id="top"></div>
<div id="center-left"></div>
<div id="center-right"></div>
<div id="bottom"></div>

js

let observer = new IntersectionObserver((entries) => {
        console.log(111, entries)
    }, {
        thresholds: 0.1
})
console.log(222, observer)
observer.observe(document.getElementById('top'))
observer.observe(document.getElementById('center-left'))
observer.observe(document.getElementById('center-right'))
observer.observe(document.getElementById('bottom'))
```

thresholds是指监听到视图所占比例为多少时可进行function操作, 而且多个被监听元素(目标元素)可以共用一个observer(观察者对象).
