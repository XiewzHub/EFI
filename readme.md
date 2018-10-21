# 联想Y7000装黑苹果问题

> 主板： 品牌 Lenovo ，型号 LNVNB161216 ， 序列号 PF16WKXB ， Bios版本 9VCN11WW
>
> CPU：Intel（R） Core(TM) i7-8750H CPU @ 2.2GHz
>
> 显卡： 
> ​    1 Intel(R) UHD Graphics 630 1G，  
> ​    2 NVIDIA GeForce GTX 1060 6G
>
> 声卡：Realtek ALC236 @ Intel Cannon Lake PCH - cAVS (Audio, Voice, Speech)	 
>
> 网卡：
> ​    1 品牌 Realtek Semiconductor Corp，名称 Realtek RTL8822BE Wireless LAN 802.11ac PCI-E Network Adapter	PCI    
> ​    2 品牌 Realtek ， 名称 Realtek RTL8168/8111 PCI-E Gigabit Ethernet Adapter	PCI
>
> 主硬盘：名称 RPFTJ128PDD2EWX ，接口类型 PCI-E ，119GB
>
> 电池：品牌 Celxpert，序列号 2094CelxpertL17C3PG2

- 使用镜像

  macOS High Sierra 10.13.6(17G2112) Installer with Clover 4606[点击下载](https://mirrors.dtops.cc/iso/MacOS/daliansky_macos/macOS%20High%20Sierra%2010.13.6%2817G2112%29%20Installer%20with%20Clover%204606.dmg)

  参考文章[链接地址](https://blog.daliansky.net/macOS-High-Sierra-10.13.6-17G2112-Release-Special-with-Clover-4606-original-mirror.html)

- 推荐网址

  + [国外论坛tonymacx86](www.tonymacx86.com)
  + [安装系统参考网址](https://osx.cx/macos-high-sierra-10-13-xhackintosh-installation-tutorial.html)
  + [大神整理的各种机型的EFI](https://github.com/sqlsec/clover)
  + [关于Clover里的 .plist 文件配置说明](https://clover-wiki.zetam.org/zh-CN/Configuration#Config.plist-%E7%BB%93%E6%9E%84)

### 说明

 由于发现有部分人想采纳我的EFI，却出现各种问题，所以我在此对如何试用它做一下简略的说明，相信能找到这里的人，对于黑苹果的安装和配置，基本都不是小白了。所以我就不对如何配置它做详细说明，只做简单阐述了。

#### 1. 笔记本哪些功能可用？

**以下功能已经成功驱动**

- 显卡（核显UHD630）

  显卡驱动目前有点小问题，就是第一次开机会黑屏，需要启动两次到三次才能正常亮屏，目前还没有找到解决方法，如果有热心好友找到了，请分享一下，万分感谢~~

- 声卡（ALC236）

- 网卡（RealtekRTL8111）

- 电源管理

- usb3.0

#### 2. 如何使用本EFI？

- **这个EFI仅适用于联想拯救者Y7000的机型，如果机型不一样或者配置不同造成不好的后果，概不负责**
- 这个EFI目前分有四个分支：`master`，`driver`，`macOs10.14`，`lenovoY50-70`
  + `master`分支算是比较稳定的分支，不出意外，这个分支一般可以直接用于安装和使用（**适用于10.13.6(17G2112)**）。在安装时可以选择`config_install.plist`这个配置来进行，在安装好后就使用默认配置`config.plist`，您可能还看到很多奇怪的配置，如V1、V2这些，可以忽略不用管，都是本人配置时做备份留下的。
  + `drver`分支是驱动调试分支，稳定性可能没那么好，甚至使用它还可能无法启动，不建议使用，除非有人指导。
  + `macOs10.14`这个分支是用于安装启动`10.14`的mac系统，目前还不能使用，如果大家已经配置好了，希望能够分享给我，非常感谢~~~
  + `lenovoY50-70`是可以用于比较老的`联想Y50`的笔记本，如果您有这台机器，那就有福了。

#### 3. 如何切换分支？

- 需要本地环境安装了git版本控制，[下载地址](https://git-scm.com/downloads)。

- 先在对应的`EFI`文件目录下右击，找到`Git Bash Here`，进入Bash命令界面。

![](http://ww1.sinaimg.cn/large/e8450fe4gy1fwg8koct80j208v0e3dgc.jpg)

- 如下图，图中的蓝色字体`master`代表的是当前分支，如果想要切换另一个分支，则可以输入`git checkout driver`就可以切换到`driver`分支，想切回master分支，就用`git checkout master`，同理，其他分支也一样，如果想看一共有多少分支可以使用`git branch`，标了`*`符号的分支则是当前分支。

  ![](http://ww1.sinaimg.cn/large/e8450fe4gy1fwg8tzflqnj20fb07074k.jpg)