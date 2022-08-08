# Issue
问题字段: TypeError [ERR_INVALID_ARG_TYPE]: The "path" argument must be of type string. Received type undefined

问题复现: 

vue中的 scripts标签中添加的lang='scss'属性，且在已安装scss-loader的前提下，删除lang属性即可；

react: react-scripts版本需要更新(3.x.x to 4.x.x)，可通过npm info react-scripts version查看版本信息。参考链接：[TypeError [ERR_INVALID_ARG_TYPE]: The "path" argument must be of type string. Received type undefined raised when starting react app](https://stackoverflow.com/questions/60234640/typeerror-err-invalid-arg-type-the-path-argument-must-be-of-type-string-re)