**[css3 min-content，max-content，fit-content, fill属性](https://www.cnblogs.com/daisygogogo/p/10688490.html)**

css3里有四个属性，用来实现以内容为主的尺寸计算方式，intrinsic sizing

```
width: min-content / max-content / fit-content / fill;
```
其中 fill 关键字，需要加浏览器前缀，并拼接available， 比如width: -webkit-fill-available;

需要提一下的是：max-content 和fit-content， 当元素内容没有超出行宽的时候，最终的宽度都是内容的宽度。而超出行宽的时候，max-content的表现是不换行，出现横向滚动条，fit-content的表现是会换