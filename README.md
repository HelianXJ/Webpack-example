# Webpack-example
A webpack example

运行步骤：

  1、 $npm install         （下载node_modules 产生node_modules 文件夹）
  
  2、 $ webpack entry.js bundle.js --module-bind 'css=style!css'  （编译entry.js到bundle.js 中  利用Loder加载css 依赖css-loader style-loader 两个module 已存在package.json 中 第一步npm install 即可下载所需模块。所以加载css require("./style.css")即可否则不使用Loder加载css需要这样：require("!style!css!./style.css")。)
  
  3、 最后浏览器打开index.html
  
  详情 https://zhaoda.gitbooks.io/webpack/content/loader.html 
