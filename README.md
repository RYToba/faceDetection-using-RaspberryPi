# faceDetection using RaspberryPi

目的：PiCameraを使用してストリーミングしている映像を自PC上で取得し顔認識にかける。

テスト環境（使用機材）：RaspberryPi 3 Model b+、Raspberry Pi カメラモジュール

ラズパイの初期設定を済ませている状況で以下を実行し、MJPEG-Streamerを用いて配信状態にする。

```
/usr/local/bin/mjpg_streamer -i "input_raspicam.so -x 640 -y 480 -fps 120 -rot 180 -q 80" -o "output_http.so -p 8080 -w /usr/local/share/mjpg-streamer/www" 
```

カメラオプションが必要な場合は適宜追加する。

後はdetect.ipynbをjupyterNotebook上でRunさせる。

### 諸仕様

ラズパイは映像配信用としてMJPEGStreamerで配信を行うだけ。

ローカルネットワークに接続されている自PCからアクセスし、取得した映像をOpenCVにかけて顔検出を行う。**(OpneCVインストール要)**

検出された顔情報を矩形切り取りし、同ディレクトリ上のimgフォルダに格納していく。

得られた画像は機械学習などで使用し、特定人物の顔識別などに使用。

![raspberrypi_and_camera](https://user-images.githubusercontent.com/39150905/61575720-4c525e80-ab0a-11e9-9ed4-a3db2e516552.png)
