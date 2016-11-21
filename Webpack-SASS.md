# Compile SASS files with webpack

## Required Packages
```
npm install --save webpack
npm install --save-dev node-sass css-loader style-loader sass-loader
npm install --save-dev extract-text-webpack-plugin
```
Webpack configuration file `webpack.config.js`
```
const path = require('path');
var ExtractTextPlugin = require('extract-text-webpack-plugin');

const SRC_DIR = path.resolve(__dirname, 'src');
const DIST_DIR = path.resolve(__dirname, 'dist');

module.exports = {
  entry: SRC_DIR + '/app.js',
  output: {
    path: DIST_DIR,
    filename: '/js/app.bundle.js'
  },
  module: {
    loaders: [
      ...
      {
        test: /\.scss$/,
        include: SRC_DIR,
        loader: ExtractTextPlugin.extract('style-loader', 'css-loader!sass-loader')
      }
    ]
  },
  plugins: [
    ...
    new ExtractTextPlugin('/css/app.bundle.css')
  ]
};

```
