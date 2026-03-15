# heic-decode

HEIC画像をデコードして生の画素データを抽出するライブラリです。

## 使い方

HEIC画像のメインイメージをデコードする例:

```javascript
import { HEIC } from "https://code4fukui.github.io/heic-decode/HEIC.js";

const fn = "./temp/0003.heic";
const buffer = await Deno.readFile(fn);
const images = await HEIC.decode(buffer);
console.log(images);
```

画像がデコードされると、[`ImageData`](https://developer.mozilla.org/en-US/docs/Web/API/ImageData)形式のオブジェクトが返されます。このオブジェクトを使って他の画像処理ライブラリと連携することができます。

_デコーダは非同期のPromiseを返しますが、ほとんどの処理は同期的に行われます。高負荷な環境では、メインスレッドがブロックされないよう、ワーカースレッドの利用を検討してください。_

## 依存関係

* [libheif-js](https://github.com/code4fukui/libheif-js/)の`libheif-wasm`
* [libheif](https://github.com/strukturag/libheif)

## 関連プロジェクト

* [heic-cli](https://github.com/catdad-experiments/heic-cli) - コマンドラインからHEIC/HEIFの画像をJPEGやPNGに変換する
* [heic-convert](https://github.com/catdad-experiments/heic-convert) - HEIC/HEIF画像をJPEGやPNGに変換する
* [libheif-js](https://github.com/catdad-experiments/libheif-js) - JavaScriptのライブラリとしてのlibheif