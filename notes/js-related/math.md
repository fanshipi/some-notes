# Basic #

**Math.round与toFiexed的区别**

Math.round(num)：四舍五入，只能取整数，返回结果为数字，可直接进行数值操作；

toFixed(d)：四舍五入，可以为任意小数位数四舍五入，返回的是字符串，不可直接进行数值操作。

例保留三位小数：

val= 0.23438040912151337，

Math.round(val*Math.pow(10,3))/Math.pow(10,3)  ，结果返回0.234

val.toFixed(3)， 结果返回'0.234'