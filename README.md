## uglifyjs-webpack-plugin压缩组件库代码

### uglifyjs-webpack-plugin存在的坑

#### 最新版uglifyjs-webpack-plugin有es6语法没有用babel转es5，导致打包报错

#### 解决方案(版本回退)
```
npm i uglifyjs-webpack-plugin@1
```

#### vue.config.js中配置
```
configureWebpack: config => {
   let plugins = [
      new UglifyJsPlugin({
      uglifyOptions: {
      	output: {
          comments: false
        },
        compress: {
          warnings: false,
          drop_debugger: true,
          drop_console: true,
        },
      },
      sourceMap: false,
      parallel: true,
    })
  ];
  config.plugins = [...config.plugins, ...plugins];	
}
```

### 参考链接 
[vue.config.js配置](https://juejin.im/entry/5b4f04adf265da0f5a254a09)     
[打包优化](https://segmentfault.com/a/1190000017008697)    
[github中issues链接](https://github.com/webpack-contrib/uglifyjs-webpack-plugin/issues/362)    
