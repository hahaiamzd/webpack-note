Bundle:
> 可以由许多不同模块生成，源文件经过加载和编译过程后，生成的最终产物。

Module:
> 我们所编写的代码文件，或者说通过 webpack 处理的文件，都将被视为一个模块.webpack配置文件中有一个 module 字段，在 module 下有一个  rules 字段，rules下就是处理模块的规则，配置哪类的模块，交给哪类loader来处理。
```javascript
module: {
    rules: [
      {
        test: /\.css$/,
        use: [
          {
            loader: "style-loader"
          }, {
            loader: "css-loader"
          }
        ]
      },
      ...
    ]
  },
```

chunk:
> webpack源码中的 Chunk.js 有这么一段注释：
```javascript
/**
 * A Chunk is a unit of encapsulation for Modules.
 * Chunks are "rendered" into bundles that get emitted when the build completes.
 */
```
> 意思就是一个chunk是一个或者多个模块的封装单元，Chunk在构建完成的时候就呈现为bundle。翻译成人话就是，Chunk是webpack在处理过程中的代码块,bundle是处理完后的产出代码块。产生Chunk的途径有几种：
> 1. enrty入口 2.异步加载模块 3. 代码分割 4.内置或者配置的plugin（后续再深入了解）