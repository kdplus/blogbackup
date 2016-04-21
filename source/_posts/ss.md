---
title: Shadowsocks-ubuntu-科學上網
date: 2016-03-23 16:58:37
categories: linux
tags: [ss,ubuntu,linux]
---
### 羅嗦
* 由於之前的ubuntu的網卡驅動沒有得到結局在加上各種以來問題，導致我拋棄了14.04打算用據說一倍茶的時間來重新安裝ubuntu。
* 這次安裝的ubuntu是15.10，因爲只需要覆蓋上次的ubuntu所以各種簡單，也再也懶得美化grub了上次實在吃足了苦頭
* 15.10比我想象的要好（拜託你根本說不出好在哪裏...總之一上來各種必須安裝的軟件都不能少，關於自己的美化的記錄到時候會再寫一篇記錄，防止我以後重裝了又一臉懵逼
* 這裏主要記錄一下Shadowsocks在ubuntu上如何運作吧~（這種東西你也寫？？？

### 正文
* 關於各種代理原理的介紹看這裏->[點我學習姿勢](https://hengyunabc.github.io/something-about-science-surf-the-internet/)
* 我使用過pptp轉發->[點我看教程](http://blog.fens.me/ubuntu-vpn-pptp/)，以及當然本文的shadowsocks（下文簡稱ss）[點我看官網](https://shadowsocks.com/)

#### SS下載
1. GUI版本  
ubuntu14.04以上
```
sudo add-apt-repository ppa:hzwhuang/ss-qt5
sudo apt-get update
sudo apt-get install shadowsocks-qt5
```
2. Command Version  
```
# 如果你沒有安裝pip
sudo apt-get install python-pip
sudo pip install shadowsocks
```
<!--more-->
#### 配置
GUI版本add一個之後按照要求填寫即可。  
下面是命令版本的配置
1. 首先你需要創建一個config來存連接ss的信息  
```
sudo vim config.json
```
裏面有這些如下字段
```
{
        "server":"服務器地址",
        "server_port":端口號,
        "local_port":1080,
        "password":"密碼",
        "timeout":600,
        "method" : "aes-256-cfb"
}                                                                                                                                                                ```
關於更多的字段和介紹可以看官網->[這裏
](https://shadowsocks.com/download.html)

2. 接下來執行下面這句話，就可以連接上ss了
```
sslocal -c config.json
```
你也可以將這句話寫到sh，以方便開機啓動注意path，確保執行正確

3. 開機啓動ss服務
像上面說的，把命令寫到sh中
```
sudo vim ss_start.sh
sslocal -c /YOUR_PATH/config.json
```
然後加入到開機自動啓動
```
sudo vim /etc/rc.local
```
把下面這句話寫在exit 0之前。
```
sudo sh /YOUR_PATH/ss_start.sh
```

#### 瀏覽器插件配合
1. Firefox  
安裝[Pan插件](https://addons.mozilla.org/zh-CN/firefox/addon/pan/?src=api)  
選擇默認代理爲ss即可
* Chrome
安裝[switchyomega插件](https://chrome.google.com/webstore/detail/proxy-switchyomega/padekgcemlokbadohgkifijomclgjgif?utm_source=chrome-app-launcher-info-dialog)  
具體操作請看此文->[點我](https://ii-i.org/archives/289)

#### 大功告成啦參考
[ubuntu运行ss客户端](http://www.jianshu.com/p/4f6ea97427e9)  
文中已經列出&&谷歌&&百度
