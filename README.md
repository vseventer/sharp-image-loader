# sharp-image-loader
> Sharp image loader module for webpack.

There is also [sharp-loader](https://www.npmjs.com/package/sharp-loader), but I needed a loader which allows access to the entire [Sharp API](http://sharp.dimens.io/en/stable/), and would return a (one) image instead of a (responsive) set. This also allows subsequent loaders (e.g. [image-webpack-loader](https://www.npmjs.com/package/image-webpack-loader)) to execute succesfully.

## Install
`$ npm install sharp-image-loader`

## Options
```js
  sequentialRead: false,
  limitInputPixels: 268402689,
  topOffsetPre: -1,
  leftOffsetPre: -1,
  widthPre: -1,
  heightPre: -1,
  topOffsetPost: -1,
  leftOffsetPost: -1,
  widthPost: -1,
  heightPost: -1,
  width: -1,
  height: -1,
  canvas: 'crop',
  crop: 0,
  angle: 0,
  rotateBeforePreExtract: false,
  flip: false,
  flop: false,
  extendTop: 0,
  extendBottom: 0,
  extendLeft: 0,
  extendRight: 0,
  withoutEnlargement: false,
  kernel: 'lanczos3',
  interpolator: 'bicubic',
  centreSampling: false,
  background: [0, 0, 0, 255],
  flatten: false,
  negate: false,
  blurSigma: 0,
  sharpenSigma: 0,
  sharpenFlat: 1,
  sharpenJagged: 2,
  threshold: 0,
  thresholdGrayscale: true,
  trimTolerance: 0,
  gamma: 0,
  greyscale: false,
  normalise: 0,
  booleanBufferIn: null,
  booleanFileIn: '',
  joinChannelIn: [],
  extractChannel: -1,
  colourspace: 'srgb',
  overlayGravity: 0,
  overlayXOffset: -1,
  overlayYOffset: -1,
  overlayTile: false,
  overlayCutout: false,
  fileOut: '',
  formatOut: 'input',
  streamOut: false,
  withMetadata: false,
  withMetadataOrientation: -1,
  jpegQuality: 80,
  jpegProgressive: false,
  jpegChromaSubsampling: '4:2:0',
  jpegTrellisQuantisation: false,
  jpegOvershootDeringing: false,
  jpegOptimiseScans: false,
  pngProgressive: false,
  pngCompressionLevel: 6,
  pngAdaptiveFiltering: true,
  webpQuality: 80,
  webpAlphaQuality: 100,
  webpLossless: false,
  webpNearLossless: false,
  tiffQuality: 80,
  tileSize: 256,
  tileOverlap: 0
}
```

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