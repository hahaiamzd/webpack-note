Q1. 关键的步骤有哪些?  

Q2. 每一步的源码解读

A1.  
1.通过webpack-cli或者直接require('webpack')的方式，用webpack函数来启动webpack的打包构建流程。（webpack-cli实则也是使用了require的方式）
2.调用webapck函数，接收config配置信息和环境对象，初始化compiler，在这期间会注册所有webpack内置的插件.

compiler 和 compilation 的区别  
compiler是webpack的核心类，在compiler中存有完整的webpack环境信息，从webpack启动到结束，compiler只会生成一次实例，在compiler中可以读取到webpack config 、 outputPath等信息
compilation包含了每次构建时当前的模块资源、编译生成资源、变化文件等。


process函数用于对webpack 的options进行初始化，实例化各个webpack自己维护的plugin（内置plugin）。

beforeRun和beforeCompile的区别


写一个loader
写一个plugin