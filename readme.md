此文件夹为 webpack 4.1.0 配置文件，请在 webpack 安装后直接放到项目根目录下，根据操作修改配置文件后，最后删除此 Readme。

- 如果使用了 Scss 语言

在 utils.js 中修改：

```js
exports.cssLoaders = function (options) {
  options = options || {}

  const cssLoader = {
    loader: 'css-loader',
    options: {
      sourceMap: options.sourceMap
    }
  }

  const postcssLoader = {
    loader: 'postcss-loader',
    options: {
      sourceMap: options.sourceMap
    }
  }
```

在 webpack.dev.conf.js 中修改：

```js
module: {
    rules: [
      {
        test: /\.css$/,
        loader: ["vue-style-loader", "css-loader"]
      },
      {
        test: /\.scss$/,
        use: ["vue-style-loader", "css-loader", "sass-loader"],
      },
    ],
  },
```

- 如果使用了 Typescript 语言

在 webpack.base.conf.js 中修改：

```js
module: {
    rules: [
      ...(config.dev.useEslint ? [createLintingRule()] : []),
      {
        test: /\.tsx?$/,
        loader: 'ts-loader',
        exclude: /node_modules/,
        options: {
          appendTsSuffixTo: [/\.vue$/]
        }
      }
    ]
  },
```
