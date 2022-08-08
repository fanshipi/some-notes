# Basic

**setState**

setState是异步的，在执行完state后运行函数的方式：this.setState({data},()=>{})；
但是在setTimeout等中却是同步的。

在项目中的constructor调用接口，若是在setState后调用了另一个接口，没有按照以上方式进行，则会造成state的变化而多次调用接口，影响性能；