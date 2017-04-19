## Webpack tutorial

`npm install -S webpack`

`npm install -g webpack`

`touch webpack.config.js`
>and put this code inside
```js
    var debug = process.env.NODE_ENV !== "production";
    var webpack = require('webpack');

    module.exports = {
      context: __dirname,
      devtool: debug ? "inline-sourcemap" : null,
      entry: "./js/scripts.js",
      output: {
        path: __dirname + "/js",
        filename: "scripts.min.js"
      },
      plugins: debug ? [] : [
        new webpack.optimize.DedupePlugin(),
        new webpack.optimize.OccurenceOrderPlugin(),
        new webpack.optimize.UglifyJsPlugin({ mangle: false, sourcemap: false }),
      ],
    };
```
>now we can run webpack

`webpack`

>to minify all and etc.

`NODE_ENV=production webpack`
>but for Windows users need to type this:
`webpack -p`