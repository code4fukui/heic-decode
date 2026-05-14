# heic-decode

> HEIC画像をデコードして生のピクセルデータを抽出します。

## 使用方法

ファイル内のメイン画像をデコードするには:

```javascript
import { HEIC } from "https://code4fukui.github.io/heic-decode/HEIC.js";

const fn = "./temp/0003.heic";
const buffer = await Deno.readFile(fn);
const images = await HEIC.decode(buffer);
console.log(images);
```

画像がデコードされると、戻り値は [`ImageData`](https://developer.mozilla.org/en-US/docs/Web/API/ImageData) 形式のプレーンオブジェクトになります。このオブジェクトを使用して、他の画像処理ライブラリと連携させることができます。

_デコーダーは Promise を返しますが、処理の大部分は同期的に行われるため、並行処理が多い本番環境ではメインスレッドをブロックしないようにワーカースレッドの使用を検討してください。_

## 依存関係

* [libheif-js](https://github.com/code4fukui/libheif-js/) の libheif-wasm
* [libheif](https://github.com/strukturag/libheif)

## 関連プロジェクト

* [heic-cli](https://github.com/catdad-experiments/heic-cli) - コマンドラインからHEIC/HEIF画像をJPEGまたはPNGに変換
* [heic-convert](https://github.com/catdad-experiments/heic-convert) - HEIC/HEIF画像をJPEGおよびPNGに変換
* [libheif-js](https://github.com/catdad-experiments/libheif-js) - ピュアJavaScriptのnpmモジュールとしてのlibheif

## ライセンス

MIT License — 詳細は [LICENSE](LICENSE) を参照してください。
