配置中的devtool的作用：用于控制是否生成，如何生成source map
值得注意的是：devtool不能和SourceMapDevToolPlugin/EvalSourceMapDevToolPlugin等插件一起使用，因为devtool配置选项在内部已经添加过这些插件，如果一起使用，则应用了两次插件