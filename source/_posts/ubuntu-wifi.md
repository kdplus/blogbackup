---
title: Ubuntu-Wifi
date: 2016-04-07 18:41:15
categories: linux
tags: [linux,wifi]
---
總之我這台華碩和ubuntu的相性的真的非常差，從裝14.04到現在使用的15.10都沒有一次是可以直接解決這個問題的。
接下來我提供幾個我廠試過的解決方案。
* 安裝wicd。這個是最方便的，通常也是最好解決的。第一次裝ubuntu14.04的時候遇到了wifi的問題，編譯實在麻煩啊...直接下載了就解決了一切問題誒，好評。然而，後來再遇到這個問題，卻沒能解決我的問題了...差評www  
```
sudo apt-get install wicd
```
* 解開軟鎖或者硬鎖
我的機子是通過這個方法解決的    
```
rfkill list #如果有yes的說明被鎖住了
rfkill unblock all #用這個命令解鎖
#很多機子，單單上面是解決不了的
sudo rmmod acer-wmi #可以打開wifi
vim /etc/modprobe.d/blacklist.conf
blacklist acer-wmi #將這句加在最後防止被鎖回來
```  
[參考來源](http://blog.csdn.net/ichsonx/article/details/40903005)
* System Setting  
有些網卡的驅動是可以在System Setting->Software&update->Additional Drivers裏面安裝的
* 自己下載驅動編譯安裝  
......
* 買一個內核支持的外接usb網卡  
這個也是解決的好方法，不用各種折騰2333。不過我比較倒霉有時候需要不斷的插拔網卡和enable開關才能搜到wifi
* 重裝系統  
有時候能奇跡般的解決我的wifi問題,裝的時候放一包乖乖可能有奇效
