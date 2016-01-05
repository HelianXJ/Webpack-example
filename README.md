# Webpack-example
A webpack example

运行步骤：

  $npm install 下载node_modules 产生node_modules 文件夹
  
  $ webpack entry.js bundle.js --module-bind 'css=style!css' 编译entry.js到bundle.js 中  利用Loder加载css 依赖css-loader style-loader 两个
  module 已存在package.json 中 第一步npm install 即可下载所需模块。
  
  所以加载css require("./style.css") 即可 否则不使用Loder 加载css需要这样：require("!style!css!./style.css")。
  
  最后浏览器打开index.html
