# Webpack-example
A webpack example

运行步骤：

  1、
  ```javascript 
      $npm install 
  ```
  （下载node_modules 产生node_modules 文件夹）
  
  2、 
  ```javascript 
  $ webpack entry.js bundle.js --module-bind 'css=style!css'  
  ```
  （编译entry.js到bundle.js 中  利用Loder加载css 依赖css-loader style-loader 两个module 已存在package.json 中 第一步npm install 即可下载所需模块。所以加载css require("./style.css")即可否则不使用Loder加载css需要这样：require("!style!css!./style.css")。)
  
  3、 最后浏览器打开index.html
  
  详情 https://zhaoda.gitbooks.io/webpack/content/loader.html 
  
  # 使用配置文件
  配置文件

Webpack 在执行的时候，除了在命令行传入参数，还可以通过指定的配置文件来执行。默认情况下，会搜索当前目录的 webpack.config.js 文件，这个文件是一个 node.js 模块，返回一个 json 格式的配置信息对象，或者通过 --config 选项来指定配置文件。
继续我们的案例，在根目录创建 package.json 来添加 webpack 需要的依赖：
```javascript
{
  "name": "webpack-example",
  "version": "1.0.0",
  "description": "A simple webpack example.",
  "main": "bundle.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [
    "webpack"
  ],
  "author": "zhaoda",
  "license": "MIT",
  "devDependencies": {
    "css-loader": "^0.21.0",
    "style-loader": "^0.13.0",
    "webpack": "^1.12.2"
  }
}
```

运行 npm install。
然后创建一个配置文件 webpack.config.js：
```javascript
var webpack = require('webpack')

module.exports = {
  entry: './entry.js',
  output: {
    path: __dirname,
    filename: 'bundle.js'
  },
  module: {
    loaders: [
      {test: /\.css$/, loader: 'style!css'}
    ]
  }
}
```

同时简化 entry.js 中的 style.css 加载方式：
require('./style.css')
最后运行 webpack，可以看到 webpack 通过配置文件执行的结果和上一章节通过命令行 webpack entry.js bundle.js --module-bind 'css=style!css 执行的结果是一样的。
