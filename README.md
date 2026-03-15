# heic-decode

> Decode HEIC images to extract raw pixel data.

## Usage

Decode the main image in the file:

```javascript
import { HEIC } from "https://code4fukui.github.io/heic-decode/HEIC.js";

const fn = "./temp/0003.heic";
const buffer = await Deno.readFile(fn);
const images = await HEIC.decode(buffer);
console.log(images);
```

When the images are decoded, the return value is a plain object in the format of [`ImageData`](https://developer.mozilla.org/en-US/docs/Web/API/ImageData). You can use this object to integrate with other imaging libraries for processing.

_Note that while the decoder returns a Promise, it does the majority of the work synchronously, so you should consider using a worker thread in order to not block the main thread in highly concurrent production environments._

## Dependencies

* libheif-wasm of [libheif-js](https://github.com/code4fukui/libheif-js/)
* [libheif](https://github.com/strukturag/libheif)

## Related

* [heic-cli](https://github.com/catdad-experiments/heic-cli) - convert heic/heif images to jpeg or png from the command line
* [heic-convert](https://github.com/catdad-experiments/heic-convert) - convert heic/heif images to jpeg and png
* [libheif-js](https://github.com/catdad-experiments/libheif-js) - libheif as a pure-javascript npm module