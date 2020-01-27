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