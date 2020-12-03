# ロボットシステム学
##  目標
作成したデバイスドライバーをベースに、LEDでモールス信号を表現する。

##  使用した環境・道具
- Raspberry Pi4 MdelB
- Ubuntu20.04
- 5mm LED * 1
- 抵抗器　220Ω * 1
- ブレッドボード
- ジャンパー線 * 3

##  接続方法
<img src= "https://user-images.githubusercontent.com/72371336/100983243-66b89b00-358c-11eb-942b-5874da20c69c.jpeg" width="400" >
LEDのアノードをGPIO25をつなぎ、カソードをGRUNDにつなぐ。

##  実行方法
実行方法は以下のコマンドを順に実行する。
```
git clone https://github.com/Isamu-Nakajima/RobotSystem.git
cd RobotSystem/
make
sudo insmod myled.ko
sudo chmod 666 /dev/myled0
```
この状況で
```
echo 1 > /dev/myled0
```
でモールス信号を実行する。
```
echo 0 > /dev/myled0
```
でLEDを消す。  
モジュールをアンインストールする時は
```
sudo rmmodmyled
```
を実行する。

##  プログラム説明
今回はモールス信号で「ISAMU」と表示させるようにする。   
これをモールス信号で表すと「　**・・　・・・　・－　－－　・・－**　」　となる。    
またそれぞれにかかる時間を
- ・の時
   -  点灯　0.5秒
   -  消灯　0.5秒
- －の時
   -  点灯　1.5秒
   -  消灯　0.5秒
- （スペース）の時
   -  消灯　1.0秒

とした。

##  実演動画
<https://youtu.be/Vf8Q6rbLqN8>

##  参考文献
モールス符号の点と線の長さ<http://k-hiura.cocolog-nifty.com/blog/2019/03/post-579f.html>
