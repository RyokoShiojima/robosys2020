# robosys2020
 - ロボットシステム学で作成したデバイスドライバ

### 用意するもの
 - Raspberry Pi 4 Model B
 - ブレッドボード
 - LED × 2
 - 抵抗 390Ω × 2
 - ジャンパーワイヤ(オス ー メス) × 3

### ビルド

```sh
git clone https://github.com/RyokoShiojima/robosys2020.git
cd robosys2020/myled
make
sudo insmod myled.ko
sudo chmod 666 /dev/myled0
```

### 動作内容と実行

2つのLEDを"LED1","LED2"と定義して説明していきます。

 - 動作1
   - LED1が消灯
```sh
echo 0 > /dev/myled0
```

 - 動作2
   - LED1が点灯
```sh
echo 1 > /dev/myled0
```

 - 動作3
   - LED2が消灯
```sh
echo 2 > /dev/myled0
```

 - 動作4
   - LED2が点灯
```sh
echo 3 > /dev/myled0
```

 - 動作5
   - LED1が数秒点灯した後、点滅してLED2が点灯し、数秒点灯した後、消灯(歩行者信号のような動作)
```sh
echo 4 > /dev/myled0
```

 - 動作6
   - LED1が数回点滅
```sh
echo 5 > /dev/myled0
```

 - 動作7
   - LED2が数回点滅
```sh
echo 6 > /dev/myled0
```

 - 動作8
   - LED1とLED2が交互に点灯した後、消灯(踏切のような動作)
```sh
echo 7 > /dev/myled0
```

### 操作終了する際に打つコマンド
```sh
sudo rmmod myled
```

### 配線

 - 全体図

![iOS の画像 (2)](https://user-images.githubusercontent.com/40712113/101236979-8aa8e780-3718-11eb-97cc-e362ce28bb3a.jpg)

 - 配線の仕方
   - 左のケーブルはGPIO25(物理ピン番号22)と接続
   - 真ん中のケーブルはGND(物理ピン番号39)と接続
   - 右のケーブルはGPIO6(物理ピン番号31)と接続

![iOS の画像 (1)](https://user-images.githubusercontent.com/40712113/101236894-06eefb00-3718-11eb-8a85-de600cd2da4f.jpg)


### 動作様子
 - 動画は「動作2 動作1 動作4 動作3 動作5 動作6 動作7 動作8」の順で実行しています
[![IMAGE ALT TEXT HERE](http://img.youtube.com/vi/7Iw7LvhsB9o/0.jpg)](https://www.youtube.com/watch?v=7Iw7LvhsB9o)
