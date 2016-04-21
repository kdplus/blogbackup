title: After installed ubuntu
tags:
---
---
title: 當我裝了Ubuntu我有哪些壞習慣  
date: 2016-04-07 19:30:03
categories: linux
tags: [tool,linux,美化]
---
### 記下
每次重裝總是忘記要撞些什麼尤其是美化的主題，ICON包什麼的名字總是記不住，於是還不如做個記錄吧。
### wicd wifi-manager

### sudo apt-get update && upgrade

### git && vim

### YouCompleteMe
ycm_client_support.[so|pyd|dll] and ycm_core.[so|pyd|dll] not detected; you need to compile YCM before using it. Read the docs!

似乎YCM是用了C++编写的模块对性能进行优化了，于是需要手工编译YCM的support库。步骤如下：

sudo apt-get install build-essential cmake python-dev
cd ~/.vim/bundle/YouCompleteMe
./install.sh

http://www.it165.net/os/html/201503/12190.html
記得sudo


### 自動掛載windows分區
http://piaoyun.cc/697.html
我是和windows雙系統，所以如果在windows上一次未正常關機的情況下啓動ubuntu將無法自動掛載並且無法正常boot的情況。所以這個時候需要去windows下關閉快速啓動的選項，且儘量避免上述情況的發生。如果發生了的話，請vim /etc/fstab 將windows分區的自動掛載註釋掉，reboot即可。


### wine
wine-HQ1.9.0
軟件中心winetricks

### smplay

### electoric wechat
git
