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
>lets just install `jquery` and `lodash`
>`npm install -S jquery`
>`npm install -S lodash`

#### for example
>module1 is `jquery`
>for example add this code inside of it
```js
    var $ = require('jquery');

    $('h1').html('new text');
```
>than run webpack
`webpack`
>module2 is `lodash`
>add `var people` and
>for example load random data from here <https://www.mockaroo.com/>
>lets `alert` and see how many female people here
>```js
    var femaleCount = _.filter(people, {gender: 'Female'}).length;
    alert(femaleCount + 'females!');
```
>let's run webpack again
> `webpack`