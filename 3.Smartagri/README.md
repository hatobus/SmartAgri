# SmartAgri

実際に農場に設置するセンサーを作っていく。

要件としては
- 温湿度、照度(照度、特定波長の強さ）、土壌湿度、Co2濃度のデータを取得して、データベースに上げる。
- 無線LANに接続し、HTTP通信でjsonファイルをPOST
- データを上げる頻度は約10秒ごとにデータを取得する

必要なもの

- 温湿度センサ ... SHT31
- 照度センサ(照度) ... TSL2561
- 照度センサ(波長) ... MIシリーズ
- 土壌湿度 ... M-07047
- Co2センサ ... MQ7

それぞれのサンプルコードをまとめたファイルを[SmartAgri.ino](./Smartagri.ino)にまとめています。

### サンプルコードの要点

それぞれのデバイスには固有の番号が必要になります。番号は決められたものを使ってください。

固有の番号はSmartAgri.inoの

```
const int deviceNum = YOUR-DEVICE-NUMBER;
```

の部分を変更してください。（二桁の数字）

また、WiFiを使用するので、SmartAgri.inoの

```
const char* ssid = "YOUR-SSID";
const char* password = "YOUR-PASSWORD";
```

の部分の、SSID, passworsを適宜変更してください。

また、センサーのピンはどこに接続しても、プロトコルが合えば動きます。

動かない OR きちんとした値が出力されない時は、ピンがきっちり刺さっているかなどを確認してください。

また、ESP32が立ち上がる際などに使用されるピンもあるため、それに繋いでしまうと、うまくプログラムが書き込めない場合などがあるため、その場合には他のピンを使用するなどをしてください。