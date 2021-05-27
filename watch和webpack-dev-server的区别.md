cmd:   webpack --watch

watch可以监控依赖图中所有文件的更改，如果其中有一个文件改动，代码将会重新编译。但是需要手动刷新浏览器才能看到效果

webpack-dev-server
启动一个简单的server，具有hmr(hot module replacement 模块热替换)功能，不需要手动刷新浏览器  

**webpack-dev-server 在编译之后不会写入到任何输出文件。而是将 bundle 文件保留在内存中，然后将它们 serve 到 server 中，就好像它们是挂载在 server 根路径上的真实文件一样。如果你的页面希望在其他不同路径中找到 bundle 文件，则可以通过 dev server 配置中的 publicPath 选项进行修改。**


