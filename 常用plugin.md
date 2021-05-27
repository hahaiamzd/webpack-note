1. HtmlWebpackPlugin 创建一个包含所有构建bundle的html文件
2. clean-webpack-plugin  每次打包之前清理打包目录下的旧构建文件
3. MiniCssExtractPlugin 为每个包含css的js文件创建一个css文件，支持css和sourceMaps的按需加载。不使用这种抽离css的插件的话，ssr的页面会因为js动态插入css的时候，导致页面样式错乱。（需要配合css-loader使用，用着插件之后则不需要用style-loader了，否则会报错,v4版本以下的webapck只能使用extract-text-webpack-plugin,但是性能有所差距）https://webpack.docschina.org/plugins/mini-css-extract-plugin/