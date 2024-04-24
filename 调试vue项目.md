# 调试vue项目
1. `vue2`中默认启用`eval-cheap-module-source-map`，此时`eval`指定的`sourceURL=[module]`，该`URL`默认携带`Hash`，例如`src/App.vue?1gh3`，此时无法映射回本地路径，需要修改`devtool: 'source-map'`，去掉`eval`即可
``` javascript
{
    export default {
        configureWebpack: {
            devtool: 'source-map'
        }
    }
}
```

2. 查看`chrome devtools`以及`VSCode debugger`生成的文件名是怎么样的，它们需要在本地文件中存在，才能编辑代码
![alt text](image.png)

3. 修改`launch.json`的`sourceMapPathOverrides`
``` javascript
{
    "sourceMapPathOverrides": {
        "http://127.0.0.1:5173/*": "${workspaceFolder}/*"
    }
}
```
