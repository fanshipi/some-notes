# Issue

**less-loader**

出现的问题: [ ant-design-landing-issue](https://github.com/ant-design/ant-design-landing/issues/235) ,指定版本及config-overrides设置

**form**

在antd的form表单中，用getDecorator双向绑定数据，initialValue可控，若是用在Select框中，有可能出现value值改变了，列表也有，但是value却不出现在框中的现象。解决办法：取消使用getDecorator双向绑定，可用Select的Value属性，另form表单的setFieldsValue属性可以动态控制值

**list & checkbox**

在list列表的actions中添加Checkbox会出现的问题：

1.选择了checkbox之后翻页，checked会保持选中状态；

2.若是给checkbox添加了key后，checked呈未选中状态；

解决办法：手动控制checkbox

```
<Checkbox key={item.id} onChange={val => {
    this.setState({
          list: this.state.list.map((_item) => {
              if(_item.id === item.id) {
                   item.checked = val
              }
              return _item
         })
     })
}} />
```