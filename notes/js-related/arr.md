# Basic #

**slice VS splice**

slice返回的是一个新数组，不会影响原数组；

splice返回的是对原数组所做的修改，会影响原数组；

slice是对数组或者字符串的截取，用法：arr.slice(startIndex,endIndex)；

arr.slice(2)截取从0开始到第2个元素为止（左闭右开）；

arr.slie(-2)截取从数组末尾的元素开始到倒数第2个为止.

**reduce**

arr.reduce(callbakc,[initialvalue])，数组求和，去重，将二元数组转换为一元数组，将多元数组转换为一元数组，对象里的属性求和

1.求和

```
let arr1 = [1,2,3,5,6]
let sum = arr1.reduce((pre,cur,index,arr)=>  pre + cur)
```

2.去重：
```
let arr1 = [11,12,12,11,14,15]
let newArr = arr1.reduce((pre,cur)=>{
        if(!pre.includes(cur)) return pre.concat(cur)
        else return pre
    }, [])
```
3.VS数组对象
```
const deleteObj = (obj)=> {
    var uniques = [];
    var stringify = {};
    for (var i = 0; i < obj.length; i++) {
        var keys = Object.keys(obj[i]);
        keys.sort(function(a, b) {
            return (Number(a) - Number(b));
        });
        var str = '';
        for (var j = 0; j < keys.length; j++) {
            str += JSON.stringify(keys[j]);
            str += JSON.stringify(obj[i][keys[j]]);
        }
        if (!stringify.hasOwnProperty(str)) {
            uniques.push(obj[i]);
            stringify[str] = true;
        }
    }
    uniques = uniques;
    return uniques;
}
```
4.计算字符串重复个数，返回对象
```
let arr1 = ['Alice','Lina','Lena','Yolanda','Alice']
let newObj = arr1.reduce((pre,cur)=>{
    if(cur in pre) {
        return pre[cur]++
    }else{
        return pre[cur]
    }
}, {})
```
5.二元数组=》一元数组
```
let arr1 = [[1,2],[3,4],[5,6]]
let newArr = arr1.reduce((pre,cur)=> pre.concat(cur), [])
```
6.多元数组=》一元数组
```
let arr1 = [[1,2],[3,4],[5,[6,7,8]]]
let newArr = (arr1)=> (
    arr1.reduce((pre,cur)=>
        pre.concat(Array.isArray(cur) ? newArr(cur) : cur)
    , [])
)
```
7.对象里的属性求和
```
let obj = [
        {
            part_name:'listening',
            score:'174'
        }, 
        {
            part_name:'reading',
            score:'224'
        },
        {
            part_name:'writing',
            score:'104'
        }
    ]

let sum = obj.reduce((pre,cur)=> cur.score + pre, 0)
```

**随机取数组中的数据**

数组arr
```
arr = [{age:22,name:'Lena'},{age:33,name:'Mike'},{age:22,name:"Elsa"}...]
```
方法一: Math.random
```
arr.sort((a,b)=> Math.random() - 0.5)（乱序）
```
**注**: Math.random() - 0.5是为了随机取数。

方法二: 乱序下取前面的200个

```
arr.sort((a,b)=> Math.random() - 0.5).filter(item,index=> index < 200)
```
**查找对象数组中某属性的最大值最小值**
```
Math.max.apply(Math,array.map((item)=>{return item.value})
Math.min.apply(Math,array.map((item)=>{return item.value})
```