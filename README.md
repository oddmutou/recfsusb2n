# recfsusb2n ver. 0.9.2 (Linux版、狂気の改変版)
地デジTV TunerのFSUSB2N向け
http://tri.dw.land.to/fsusb2n/

責任は負いません。自己責任で行ってください。
当然、製品の保証外となり、修理・交換・サポートはされません。まず、Windows上で動作確認は行ってください。

## 使い方

Buildした後、
./recfsusb2n 録画するchannel 録画秒数 出力先ファイル名

録画秒数に - を指定するとSIGTERM, Ctrl+C等でinterruptされるまで録画を続けます。
出力先ファイル名に - を指定すると標準出力にTSを出力します。その場合、ログは標準エラー出力に出力されます。

## ビルド方法詳細

Makefileの記述
B25      = -DB25
まるも氏のARIB STD-B25 仕様確認テストプログラムがリンクされ、B25復号が可能になります。
オプション --b25 を指定すると、録画時にB25復号を経由して出力します。

/dev/bus/usb または /proc/bus/usb にある usbfs を使用してデバイスにアクセスします。
デバイスに対応するファイルの書き込み権限が必要です。

必要な物:
-  g++ コンパイル環境(cmake使用)
-  boostライブラリ

まるも氏のARIB STD-B25 仕様確認テストプログラムに、FSUSB2のチューナーをアクセスするように改変したものです。
元のプログラムについては
arib25/readme.txt を参照してください。

### for debian
```bash
sudo apt install make libboost-all-dev
cd src
make
```
