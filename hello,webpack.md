# hello webpack

## 中文文档
https://webpack.docschina.org/concepts/
## meaning:
- 配合ping-node和ping-mng两个项目来加深对webpack的理解

## target:
1. 把ping-mng静态资源上cdn （base） √
2. 输出一份webpack的学习文档 (Better)
3. 手撸一个plugins （best）

## 基本概念
webpack有<font color=red>6</font>种基本属性  
- entry
- output
- loader
- plugin
- mode
- browser compatibility

### 1.entry (<font color=red>lack demo</font>)
在多页面应用的时候，可以注入多个入口起点，多页应用之间可以复用入口起点之间的代码和模块

### 2.output (<font color=red>lack demo</font>)
webpack配置可以有多个入口起点，但是只能有一份出口配置。（注意是配置，而不是只能有一个出口文件）

output.publicPath = 【此输出目录对应的公开URL】

Q1:js能不能用contenthash? 怎么用？  
A1:要根据webpack的版本而定，就目前发现3.x.x版本的不支持，4.0.0的支持

Q2:如何进行splitChunks？

code splitting 主要有两种  
1.通过entry配置手动分离代码和SplitChunkPlugin去重和分离chunk（值得一提的是webpack V5.0.0beta版本中增加了dependOn属性，entry对象中的元素可以为对象了，并且可以通过手动的方式配置各个入口bundle中的依赖https://webpack.docschina.org/guides/code-splitting/）  

2.针对动态代码拆分时，可以用ECMAScipt田中的import()来实现

Q3:webpack中如何配置babel?  
https://webpack.js.org/loaders/babel-loader/

安装babel-loader @babel/core @babel/preset-env webpack

Q4:chunkhash和contenthash不能与HMR共存

Q5:可以通过SplitChunksPlugin中的cacheGroup选项，来实现将第三方库都提取到单独的文件中.(以此再配合浏览器的缓存机制，可以减少请求量，减轻server的压力)

Q6:引入css-loader与style-loader的时候，必须要保证css-loader在style-loader的左边。（因为webpack读取loader的顺序是从右到左，从下到上，需要先用css-loader转译css文件，再通过style-loader把css通过style标签插入到html当中）


Q7:tree-shaking的含义
移除js上下文中未引用的代码。
使用要求：（生产环境默认打开，测试环境需要再optimization中配置usedExports为true）
1.确保模块使用的是ES2015的模块语法 import export  
2.确认没有compiler将ES2015模块语法转换为CommonJS模块  
3.在package.json增加sideEffects属性。（sideEffects可以通知webpack哪些文件是不受tree-shaking影响的）

Q8: webpack.config.js文件中不能设置node的当前环境(但是可以用来判断当前是什么环境)

Q9: shim 用于识别出哪些使用了非ESM、CommonJs、AMD规范化的(模块例如使用jq的模块)。同时可以用来polyfill一些浏览器能力。

Q10:DllPlugin与SplitChunksPlugin的差别  
虽然两者都可以拆分出不经常更新的依赖文件，但使用DllPlugin进行第二次打包，是不会重新去编译新的依赖文件的，而SplitChunksPlugin会重新编译。但是使用DllPlugin是全量引入的，所以无法做到按需加载。https://juejin.im/post/5dccea0df265da0bc53c7523  

Q11: shim与polyfill的区别  
shim是一个库，它利用旧环境的能力，来实现一个新的API.  
polyfill是针对浏览器的一种补丁，当浏览器不支持某种能力的时候，就可以加载对应的polyfill，以此来实现某种能力。
polyfill可以说是shim在浏览器端的一种子集，而polyfill是会前置判断浏览器是否不支持某种能力，再进行引入的。而shim的话是在环境之中直接全局引入，并不会先判断环境是否已有对应得能力(api).  https://juejin.im/post/5e23cd206fb9a0300a4505db

Q12: PWA的使用
webpack中也可以开箱即用pwa功能，workbox-webpack-plugin插件实现了用简易的配置就可以使用service workder

Q13: webpack集成了TypeScript

Q14: CSP (content-security-policy)