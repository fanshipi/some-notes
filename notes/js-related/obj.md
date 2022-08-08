# Basic #
**Object.freeze**

Object.freeze(obj):对一个对象进行冻结，理论上来说，对于冻结的对象（属性为string，number，bool），是不允许修改属性值，不允许添加属性、删除属性，特殊情况除外：例如
```
let obj={
   a:{...}  / a:[...]
}
```
obj对象的属性a为对象、函数或者数组（函数和数组也是对象）时，可更改，若要实现不可更改，则可进行深入冻结。
```
function deepFreeze(obj) {
    let propNames = obj.getOwnPropertyNames(obj)
    propNames.forEach(item=>{
          let props = obj[item]
          if(typeof props=='object' && props !== null)  
            deepFreeze(props)
     })
    return Object.freeze(obj)
}
```
**对象结构{a:'aaa',b:'bbb'}转换为a&b结构**

利用query-string包的处理：
```
import queryString from 'query-string';
const fn = (obj)=> (queryString.stringify(obj));
```
**深浅拷贝**

1.基本数据类型保存在栈中，引用类型保存在堆中；

2.栈的大小是固定的，堆的大小是无限的。而引用类型的数据是动态的，基本数据类型相对来说比较稳定，占用内存比较小；

3.堆内存是无序存储。

基本数据类型的复制只是简单的赋值，对一个数据的修改不影响另外一个数据；

引用类型的复制，复制的是引用对象的地址，及当前数据及引用数据指向同一个指针存储位置，修改其中一个必定会影响另外一个，深拷贝可以解决这个问题；

深拷贝的方法：

方法一

```
JSON.parse(JSON.stringify(obj))
```

缺点：会抛弃对象的constructor，深拷贝之后，不管这个对象原来的构造函数是什么，在深拷贝之后都会变成object，这种方法能正确处理的只有Number,String,Boolean,Array，扁平对象，也就是说，只有可以转化成JOSN格式的对象才可以这样用，像function没办法转成JOSN；

方法二：lodash库的_cloneDeep(obj)

方法三：jquery的$.extend()

参考链接：[JS深拷贝和浅拷贝的实现](https://www.jianshu.com/p/cf1e9d7e94fb)

**节流 & 防抖**

防抖：指触发事件后在 n 秒内函数只能执行一次，如果在 n 秒内又触发了事件，则会重新计算函数执行时间。

1.非立即执行；

2.立即执行；

--自己理解：重复触发，会计算是否是在n秒内触发的，如果在n秒内触发，则会重新计算时间，让事件执行

节流：指连续触发事件但是在 n 秒中只执行一次函数。节流会稀释函数的执行频率（时间戳，定时器）

---自己理解：强制执行，无论触发多少次，都只执行这n秒内的一次

[节流防抖](https://segmentfault.com/a/1190000018445196)

**对象是否包含某个key属性**

之前我用来判断一个对象是否包含某个key值时，是通过Object.keys(obj).indexof(key)来判断，若为-1，则不包含；
其实可以用

key in obj简单直接的判断是否包含，包含为true,否则为false；

Reflect.has(obj,key)，包含key为true,否则为false====》Reflect的用法

# Issue #

**关于保证object属性的顺序问题**

网上搜了关于“保证Object属性的顺序问题”，看了两篇吧，

一是Reflect.ownKeys(obj)可以实现，

二是Object.
ownPropertyKeys，

三是lodash的isequal；

在项目中试了前面两种方法，不知道是否有其他的条件要求，还是本身实现不了输出object属性的顺序问题，最终没有实现。
是通过Object.keys(obj).sort((a,b)=>a.charCodeAt(0)-b.charCodeAt(0)),加了排序才实现了这个要求

参考链接：

1.[js能够保证object属性的输出顺序吗？](http://jartto.wang/2016/10/25/does-js-guarantee-object-property-order/)

2.[Object.keys(..)对象属性的顺序？](https://juejin.im/post/6844903796062191624)

