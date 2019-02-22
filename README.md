zram.shによって、4コアそれぞれ用にzram0, zram1, zram2, zram3の4つが作られる。

```
htop
swapon -s

sudo wget -O /usr/bin/zram.sh https://raw.githubusercontent.com/Naohiro2g/zram_rpi3/master/zram.sh
sudo chmod +x /usr/bin/zram.sh
```

起動設定：
`sudo nano /etc/rc.local`

exit 0の前に挿入：
`/usr/bin/zram.sh &`


zRAM onだと、実メモリ上に高速に圧縮してswapされる。
実際にマイクロSDカードへのswapが減った感じがする。
ファイルへのswapを遅らせることに成功している。

ファイルへのswapが起きると、今まで同じく、動作が急に遅くなる。
マイクロSDカードではなくUSB接続のSSDにswap領域を持てば、
その部分が改善できる。

--> ラズパイ高速化　https://github.com/Naohiro2g/Raspberry-Pi-Projects/wiki/高速化


# rpi_zram
script to enable zram for raspberry pi

Download the script and copy to /usr/bin/ folder
```
sudo wget -O /usr/bin/zram.sh https://raw.githubusercontent.com/Naohiro2g/zram_rpi3/master/zram.sh
```

make file executable
```
sudo chmod +x /usr/bin/zram.sh
```

edit /etc/rc.local file to run script on boot
```
sudo nano /etc/rc.local
```

add line before exit 0
```
/usr/bin/zram.sh &
```
