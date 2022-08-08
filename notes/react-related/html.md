# Basic

**将模型字符串显示到页面**

例子：
```
const str = `<span>Hello world</span>`

<div className="divStyle">
    <div style={{width:'120px',borderRadius:'40% 0%',color:'#627d9b',backgroundColor:'#a2caf8'}}
        dangerouslySetInnerHTML={{
            __html: str.replace(/world/gi, txt => `<strong>${txt}</strong>`),
        }}
    />
</div>

scss文件：
.divStyle {
    > div > span > strong {
        color: #a1190f !important;
    }
}
```

vue:
```
domPropsInnerHtml='bar'
```