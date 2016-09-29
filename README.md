# frontend-cheatsheet
Use this project as a cheatsheet/starter kit for developing front end applications. I'll be adding more stuff as I start exploring modules.

## Basic Setup
1. Installing `webpack` for bundling all the dependencies into a single file.
2. Installing `babel` packages for transpiling ES2015.
3. Setting up `UglifyJsPlugin`.

```
npm init
npm install --save-dev webpack
npm install --save-dev babel-core babel-preset-es2015
npm install --save-dev babel-loader
npm install --save babel-polyfill
```
Webpack configuration file `webpack.config.js`
```
const webpack = require('webpack');

module.exports = {
  entry: './src/app.js',
  output: {
    path: './dist',
    filename: 'app.bundle.js'
  },
  module: {
    loaders: [{
      test: /\.js$/,
      exclude: /node_modules/,
      loader: 'babel-loader'
    }]
  },
  plugins: [
    new webpack.optimize.UglifyJsPlugin({
      compress: {
        warnings: false,
      },
      output: {
        comments: false,
      },
    }),
  ]
};
```
Babel configuration file `.babelrc`
```
{ "presets": [ "es2015" ] }
```
