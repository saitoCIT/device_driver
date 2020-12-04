# device_driver

# ロボットシステム学
## robsys2020 課題1 
## <共同製作者>
- ソースコード内のMODULE_AUTHORを参照
## 課題1 <内容>
- <内容>
  - ledを4つ用意し, 点灯消灯を行う
- <アピールポイント>
  - 学籍番号が個人情報のため, 円周率を9桁まで2進数で表現する
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
```bash:move
$echo 1 > /dev/myled0
$echo 2 > /dev/myled0
$echo 3 > /dev/myled0
$echo 4 > /dev/myled0
```
- デバイスドライバの削除
```bash:delate device driver
$sudo rmmod myled
```
# 参考資料
https://github.com/ryuichiueda/robosys_device_drivers
