# jade html loader for webpack

## Usage

``` javascript
var html = require("jade-html!./file.jade");
// => returns file.jade content as html
```

Allows you to get HTML back instead of a function reference. I found this
useful for templates which render server side.

Possible options are (all passed to jade.compile()):

* self   - set the context

* pretty - boolean, output pretty html or not

* locals - set locals

Don't forget to polyfill `require` if you want to use it in node.
See [enhanced-require](https://github.com/webpack/enhanced-require) documentation.


### How to use locals:

inside your webpack config file:

```javascript
module.exports = {
    module: {
        loaders: {
        // here is as usual
         { test: /\.jade$/,  loader: 'raw-loader!jade-html-loader' },
        }
    },
    jadeLoader: {
    //here you can set any of compiler options, and locals as well
     locals: {
      bem: require('bem-jade')({
        prefix: '',
        element: '__',
        modifier: '--',
        default_tag: 'div',
      })
    },

    basedir: __dirname + '/src'
    }
}
```

## License

MIT (http://www.opensource.org/licenses/mit-license.php)

