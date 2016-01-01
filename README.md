# THETA_GL
THETA WebGL Viewer with three.js

RICHO THETA S の映像をWebGL(three.js)とUVマッピングを用いて、全天球動画としてブラウザで表示します。

## 謝辞
* WebGLでの描画には、[three.js](http://threejs.org/)を利用しています
  * 全天球描画には[panorama / equirectangularサンプル](http://threejs.org/examples/#webgl_panorama_equirectangular)を参考にしています。
  * three.js はMITライセンスで提供されています
* UVマッピングの作成には、次のデータを利用させていただいています
  * 凹みtips [発売前に RICOH THETA S のライブビューを Unity でリアルタイムに全天球で見るやつ作ってみた](http://tips.hecomi.com/entry/2015/10/11/211456)
  * 上記のUnity用UVマッピングを元に、baba氏がthree.js用に変換、微調整したマッピングjsonデータ
* WebRTC配信サービス [WebRTC SFU as a Service Anzu](https://anzu.shiguredo.jp/) の利用サンプルには、[anzu-sdk.js](https://github.com/shiguredo/anzu-js-sdk)を利用しています
  * WebRTC SFU as a Service Anzuは株式会社時雨堂が提供しているサービスです
  * anzu-sdk.js は Apache License Version 2.0 で提供されています


皆様、どうもありがとうございます。


## サンプル
### USBカメラとして接続して利用
* navigator.getUserMedia()を利用してカメラ映像を取り込んだものを表示するサンプルです
* theta_360.html

### WebRTC SFU 配信映像を利用
* [WebRTC SFU as a Service Anzu](https://anzu.shiguredo.jp/) の配信映像を表示するサンプルです
* theta_anzu_360.html
* [Anzuダッシュボード](https://anzu.shiguredo.jp/dashboard.html)で配信を開始してから、サンプルでチャネルIDを指定して接続していください

## 使い方
### 準備
* HTMLでthree.js または trhee.min.js を読み込みます
  * [最新版をダウンロード](http://github.com/mrdoob/three.js/zipball/master)するか、[CDNのもの](http://cdnjs.com/libraries/three.js/)を利用します
* HTMLでtheta_gl.jsを読み込みます
  * 利用にあたっては、uvフォルダの下のjsonファイルも必要になります
* Anzuを利用する場合は、anzu.js または anzu.min.js も必要です
  * [最新版をgithub](https://github.com/shiguredo/anzu-js-sdk)から取得してください

### 初期化
* THETA_GL.init(divId, autoResuze, debugFlag)
  * string divId : WebGLを表示するCanvasのコンテナとなる、div要素のIDを指定
  * bool autoResize : Windowのリサイズに追従するかどうか(true/false)
  * bool debugFlag : デバッグ用に作業用のvideo要素、canvas要素を表示するか、ログ情報をconsoleに表示するか

### WebGLアニメーションの開始
* THETA_GL.startAnimate()

### 映像ソースURLの指定
* THETA_GL.setVideoSrc(url)
  * string url : 映像のURL。Web上のURLか、URL.createObjectURL()で生成したURLを指定

### 映像の停止
* THETA_GL.stopVideoSrc()

### デバイスの方向に追従
* THETA_GL.followOrientation(flag)
  * bool flag: スマートデバイスの方向に追従されるかどうかを指定

### コード例
```
var url = 'http://yourserver.com/video.mp4';
THETA_GL.init('container', true, false);
THETA_GL.setVideoSrc(url);
THETA_GL.startAnimate();
```


## ライセンス
THETA_GLはMITランセンスで提供されます

