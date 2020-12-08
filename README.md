# device_driver

# ロボットシステム学
## robsys2020 課題1 
## <共同製作者>
- CIT 高野翔伍 春山健太 高見俊介
## 課題1 <内容>
- <内容>
  - ledを4つ用意し, 点灯消灯を行う
- <アピールポイント>
  - 円周率を9桁まで2進数で表現する

## 回路
![kairo](https://user-images.githubusercontent.com/75356150/101359530-bfb36680-38df-11eb-93b7-e4adc06bda50.jpg)

LEDはRaspberry PiのGPIO[22, 23, 24, 25]及びGNDに接続  
GPIOに対応するLEDはブレッドボードの左から順にGPIO[22, 23, 24, 25]となっている  
ブレッドボードのLEDは左から8の位, 4の位, 2の位, 1の位の値と見なす
  
## <実行環境>
Raspberry Pi及びubuntu(desktop,serverとはない)が必要
次の環境では動作を確認
|||
|:---|---:|
|機種|Raspberry Pi Model 4|
|OS|ubuntu mate 20.04|

## <動作手順>
- ビルド
ソースコード(.c)が存在するフォルダへ移動
次のコマンドを使用し, ビルド
※一度した場合にはビルドした場合には後述するデバイスドライバの削除を実行
```bash:build
$make 
$sudo insmod myled.ko
$sudo chmod 666 /dev/myled0
```
- 動作
echo x > /dev/myled0でxの値の桁数の数値を2進数で表示する
なお、キャラクタで数値を取っているため,　0 <= x < 10の整数となっている  
例えば, 

```bash:move
$echo 1 > /dev/myled0
```
と入力すると, GPIO[25, 24]に接続されたLEDが点灯する  
このとき, ブレッドボードの2の位と1の位が点灯するため, このブレッドボードは3を表示していることがわかる

```bash:move
$echo 2 > /dev/myled0
```
と入力すると, GPIO[25]に接続されたLEDが点灯する  
このとき, ブレッドボードの1の位が点灯するため, このブレッドボードは1を表示していることがわかる

- デバイスドライバの削除
```bash:delate device driver
$sudo rmmod myled
```

## <共同作成者との共通点/相違点>
- 共通点  
LEDを点灯させる部分をfor文で回す

- 相違点  
LEDのON/OFFで2進数表現し, ON/OFFの書き込みの部分で円周率に対応させた

# 参考資料
https://github.com/ryuichiueda/robosys_device_drivers
