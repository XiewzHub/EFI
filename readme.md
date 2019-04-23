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

- 欢迎加入由大佬@[xiaoMGitHub](https://github.com/xiaoMGitHub)创建的Y7000系列笔记本黑苹果群：`285680890`

- 使用镜像

  镜像来源于黑果小兵，博客地址为<https://blog.daliansky.net/.   
  安装镜像：macOS Mojave 10.14.3(18D42) Installer with Clover 4859.dmg    [点击下载](https://blog.daliansky.net/macOS-Mojave-10.14.3-18D42-official-version-with-Clover-4859-original-image.html)

  更多下载[点击](https://mirrors.dtops.cc/iso/MacOS/daliansky_macos/)

- 推荐网址

  - [国外论坛tonymacx86](https://www.tonymacx86.com)
  - [安装系统参考网址](https://osx.cx/macos-high-sierra-10-13-xhackintosh-installation-tutorial.html)
  - [大神整理的各种机型的EFI](https://github.com/sqlsec/clover)
  - [关于Clover里的 .plist 文件配置说明](https://clover-wiki.zetam.org/zh-CN/Configuration#Config.plist-%E7%BB%93%E6%9E%84)
  - [黑果小兵博客](https://blog.daliansky.net)
  - [触摸板驱动大神penghubingzhou博客](<https://www.penghubingzhou.cn/#blog>)

## 更新

2019-04-24：在大佬[penghubingzhou](https://github.com/penghubingzhou)的努力下，终于驱动了`ELAN（硬件id：061B）`触摸板，对于这款触摸板的同学可以更新了，新思触摸板可以选择性更新。

2019-03-18：合并了@[xiaoMGitHub](https://github.com/xiaoMGitHub)的EFI，支持小键盘

2018-12-19：感谢@[arigatouzq](https://github.com/arigatouzq)提出的几个问题点，已经修复了找不到电池的问题。

## 感谢

- 感谢@[xiaoMGitHub](https://github.com/xiaoMGitHub)、@[penghubingzhou](https://github.com/penghubingzhou)和群友的不断努力～～

- 感谢@Mustard404 提供的`Mojave 10.14`的安装`clover`，此处提供[下载](https://github.com/hnie-xwz/EFI/files/2513551/EFI.zip)，或者在[issue](https://github.com/hnie-xwz/EFI/issues/7)中找到并下载。

- 感谢@daliansky制作出能驱动`macOS Mojave10.14 with Y7000`声卡驱动的EFI，支持原作者[地址链接](https://github.com/daliansky/Lenovo-Y7000-hackintosh)，声卡驱动注入`layout-id=3`

- 感谢**黑果小兵**制作的众多黑苹果安装教程，以及对于的镜像提供下载，博客地址为[黑果小兵博客](https://blog.daliansky.net/)

## 驱动情况

本人测试使用版本为：`macOS Mojave 10.14.3(18D42) ` ，目前**基本完美**，图片后续跟上。

- [x] 显卡(UHD630)正常，笔记本无法驱动独显

- [x] 网卡正常（只能驱动有线网卡`RealtekRTL8111`）

- [x] 无线网卡使用`BCM94352z`（DW1560），能正常使用蓝牙、WiFi

- [x] USB3.0正常

- [x] 亮度调节正常

- [x] 睡眠正常

- [x] 声卡alc236需要（ALC236驱动成功，id=18），耳机杂音可以在声音设置中调节声道，或者使用修复补丁

- [x] 键盘小键盘正常使用

- [x] ~~ELAN触摸板无法使用~~，新思触摸板可用，ELAN061B最新驱动，理论上都可以使用（目前ENAN的部分机器无法使用三指操作）

- [x] 外接显示器hdmi接口不可用，可通过usb转hdmi

## 设置

- 关于双系统下，macOS Mojave系统与Windows系统**时间不一致**的问题

  1. 打开时间设置

     ![mark](http://ww1.sinaimg.cn/large/e8450fe4gy1g2d1m55jxbj209803s74m.jpg)

  2. 打开鉴定设置，输入用户密码
     ![](http://ww1.sinaimg.cn/large/e8450fe4gy1g2d1qbzmt6j20ik0eojsf.jpg)
  3. 选择时区，设置为中国北京或天津
     ![](http://ww1.sinaimg.cn/large/e8450fe4gy1g2d1pzjx72j20ik0g53zr.jpg)


## 如何使用与安装

- 1 选择并切换到`macOs10.14`分支

  ![](http://ww1.sinaimg.cn/large/e8450fe4gy1g2d1re33oyj20u70b3dgl.jpg)

- 2 下载EFI

  ![](http://ww1.sinaimg.cn/large/e8450fe4gy1g2d1rwbkfkj20uh099dgp.jpg)

- 3 替换`clover`

  找到U盘或者硬盘的`clover`，右击点`强制删除`，然后把需要替换的`clover`拖入即可。

  ![](http://ww1.sinaimg.cn/large/e8450fe4gy1g2d1sgvpqej20xh0bxjse.jpg)

- 4 进入clover引导界面后，不要先急着安装，先进入显卡配置，把`ig-platform-id`设置为`0x12345678`，方便安装；以免安装时黑屏，安装过程会重启几次，记得每次都进去改一下。

## 说明

- 新思触摸板如果无法使用，则替换会原来的版本，或删除`CLOVER/ACPI/patched/SSDT-TPD0.aml`，修改`CLOVER/config_org.plist`为`config.plist`替换原来的`config.plist`即可。

## 实用软件

- mac下挂载EFI分区的实用软件，clover无法挂载的，也可以实用它挂载成功。`ESP Mounter Pro.app_v1.9.1.zip`链接：https://pan.baidu.com/s/1yR5KE4fhS5ddCpoIpq4AjQ  提取码：wyr4 
- 想为其他电脑定制驱动，可以使用该软件：黑苹果显卡，usb，声卡等驱动定制软件`Hackintool.zip`链接：https://pan.baidu.com/s/1VFJw2k2WMjD6WhSFWWblyQ  提取码：2n4s 
  



**未完待续。。。**
