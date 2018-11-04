# 联想Y7000装黑苹果10.14系统

> 主板： 品牌 Lenovo 属于300系列 ，型号 LNVNB161216 ， 序列号 PF16WKXB ， Bios版本 9VCN11WW
>
> CPU：Intel（R） Core(TM) i7-8750H CPU @ 2.2GHz
>
> 显卡： 1 Intel(R) UHD Graphics 630 1G，
> 2 NVIDIA GeForce GTX 1060 6G
>
> 声卡：Realtek ALC236 @ Intel Cannon Lake PCH - cAVS (Audio, Voice, Speech)
>
> 网卡： 1 品牌 Realtek Semiconductor Corp，名称 Realtek RTL8822BE Wireless LAN 802.11ac PCI-E Network Adapter	PCI
> 2 品牌 Realtek ， 名称 Realtek RTL8168/8111 PCI-E Gigabit Ethernet Adapter	PCI
>
> 主硬盘：名称 RPFTJ128PDD2EWX ，接口类型 PCI-E ，119GB
>
> 电池：品牌 Celxpert，序列号 2094CelxpertL17C3PG2

- 使用镜像


  macOS Mojave 10.14(18A391) Installer with Clover 4674.dmg    [点击下载](https://mirrors.dtops.cc/iso/MacOS/daliansky_macos/macOS%20Mojave%2010.14%2818A391%29%20Installer%20with%20Clover%204674.dmg)

  更多下载[点击](https://mirrors.dtops.cc/iso/MacOS/daliansky_macos/)

  参考文章 黑果小兵关于10.14系统安装教程[链接地址](https://blog.daliansky.net/macOS-Mojave-10.14-18A391-official-version-with-Clover-4674-original-image.html)

- 推荐网址

  - [国外论坛tonymacx86](https://github.com/hnie-xwz/EFI/blob/master/www.tonymacx86.com)
  - [安装系统参考网址](https://osx.cx/macos-high-sierra-10-13-xhackintosh-installation-tutorial.html)
  - [大神整理的各种机型的EFI](https://github.com/sqlsec/clover)
  - [关于Clover里的 .plist 文件配置说明](https://clover-wiki.zetam.org/zh-CN/Configuration#Config.plist-%E7%BB%93%E6%9E%84)

## 感谢

- 感谢@Mustard404 提供的`Mojave 10.14`的安装`clover`，此处提供[下载](https://github.com/hnie-xwz/EFI/files/2513551/EFI.zip)，或者在[issue](https://github.com/hnie-xwz/EFI/issues/7)中找到并下载。

- 感谢@daliansky制作出能驱动`macOS Mojave10.14 with Y7000`声卡驱动的EFI，支持原作者[地址链接](https://github.com/daliansky/Lenovo-Y7000-hackintosh)，声卡驱动注入`layout-id=3`



## 驱动情况

本人测试使用版本为：`macOS Mojave 10.14(18A391)` ，图片后续跟上。

- [x] 显卡(UHD630)正常，笔记本无法驱动独显
- [x] 网卡正常（只能驱动有线网卡`8111`，无线网卡不能驱动）
- [x] USB3.0正常
- [x] 亮度调节正常
- [x] 睡眠正常
- [x] 声卡alc236需要~~重新仿冒~~（ALC236驱动成功，id=3）
- [ ] 键盘小键盘无法使用，只能当功能键用，如`音乐播放`，其他正常
- [ ] 触摸板无法使用，没反应，暂时没有去管他
- [ ] 外接显示器，**未测试**，希望大家帮忙试试

## 如何使用与安装

- 1 选择并切换到`macOs10.14`分支

  ![mark](http://ph31ipolx.bkt.clouddn.com/blog/181029/B8eHHI4JhH.png)

- 2 下载EFI

  ![mark](http://ph31ipolx.bkt.clouddn.com/blog/181029/4im272ED4j.png)

- 3 替换`clover`

  找到U盘或者硬盘的`clover`，右击点`强制删除`，然后把需要替换的`clover`拖入即可。

  ![mark](http://ph31ipolx.bkt.clouddn.com/blog/181029/K0FLjjFa8J.png)

- 4 进入clover引导界面后，不要先急着安装，先进入显卡配置，把`ig-platform-id`设置为`0x12345678`，方便安装；以免安装时黑屏，安装过程会重启几次，记得每次都进去改一下。

## 说明

~~由于此次升级后，原版声卡删除了很多`layout-id`，很不幸，联想Y7000的可用id也被删除了，导致原来的仿冒驱动无法正常使用，因此需要重新仿冒声卡`AppleALC`，我预计本周末会对声卡进行仿冒，因为最近没多少时间去弄，大家见谅。大家也可以暂时使用`万能声卡`暂时应急。~~

- 1 不要随便替换`Lilu.kext`和`WhateverGreen.kext`

  因为显卡驱动使用的不是官方建议的版本，但是这个显卡可以调亮度，需要在启动参数中加入`igxfcflbklt=force`，对于8代CPU的支持很好。

- 2 声卡已经成功驱动，可以使用快捷键`FN`+`F1~3`调节，此外，**睡眠后声卡无声，暂时未解决**

- 3 亮度调节不能使用快捷键，只能手动进入显示器设置中调节





**未完待续。。。**