# sharp-image-loader
> Sharp image loader module for webpack.

There is also [sharp-loader](https://www.npmjs.com/package/sharp-loader), but I needed a loader which allows access to the entire [Sharp API](http://sharp.dimens.io/en/stable/), and would return a (one) image instead of a (responsive) set. This also allows subsequent loaders (e.g. [image-webpack-loader](https://www.npmjs.com/package/image-webpack-loader)) to execute succesfully.

## Install
`$ npm install sharp-image-loader`

## Usage
See the examples below. Please note if you plan to load more than one version of the same image, it is recommended to use a module like [file-loader](https://www.npmjs.com/package/file-loader), to ensure each version of the same image has a different name. Using a hash would work, for example.

### Example 1
```js
{
  module: {
    rules: [{
      test: /\.jpg$/,
      use: [
        'file-loader?name=img/[name].[hash:4].[ext]',
        {
          loader: 'sharp-image-loader',
          options: {
            height: 192,
            width: 192
          }
        }
      }
    }]
  }
};
```

### Example 2
```js
const url = require('./image.jpg?width=192&height=192');
```

## Changelog
See the [Changelog](./CHANGELOG.md) for a list of changes.

## License
    The MIT License (MIT)

    Copyright (c) 2017 Mark van Seventer

    Permission is hereby granted, free of charge, to any person obtaining a copy of
    this software and associated documentation files (the "Software"), to deal in
    the Software without restriction, including without limitation the rights to
    use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
    the Software, and to permit persons to whom the Software is furnished to do so,
    subject to the following conditions:

    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
    FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
    COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
    IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
    CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.