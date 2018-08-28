# 联想Y7000装黑苹果问题

> 主板： 品牌 Lenovo ，型号 LNVNB161216 ， 序列号 PF16WKXB ， Bios版本 9VCN11WW
>
> CPU：Intel（R） Core(TM) i7-8750H CPU @ 2.2GHz
>
> 显卡： 
>     1 Intel(R) UHD Graphics 630 1G，
>     2 NVIDIA GeForce GTX 1060 6G
>
> 声卡：Realtek High Definition Audio
>
> 网卡：
>     1 品牌 Realtek Semiconductor Corp，名称 Realtek 8822BE Wireless LAN 802.11ac PCI-E NIC
>     2 品牌 Realtek ， 名称 Realtek PCIe GbE Family Controller
>
> 主硬盘：名称 RPFTJ128PDD2EWX ，接口类型 PCI-E ，119GB
>
> 电池：品牌 Celxpert，序列号 2094CelxpertL17C3PG2

- 使用镜像

  macOS High Sierra 10.13.6(17G2112) Installer with Clover 4606[点击下载](https://mirrors.dtops.cc/iso/MacOS/daliansky_macos/macOS%20High%20Sierra%2010.13.6%2817G2112%29%20Installer%20with%20Clover%204606.dmg)

  参考文章[链接地址](https://blog.daliansky.net/macOS-High-Sierra-10.13.6-17G2112-Release-Special-with-Clover-4606-original-mirror.html)

### 核显Uhd630没有识别

- 回答1

  那就是你还需要lilu.kext。另外我看到你使用i5-8400而不是i3。您甚至不应该按照这个来获得图形加速，虽然它是一个选项，只需在kexts / Other中使用FAKEPCIID.kext + FakePCIID_Intel_HD_Graphics.kext + IntelGraphicsFixup.kext + Lilu.kext 然后将ig-platform-id设置为0x59120000 ，FakeID-> IntelGFX 0x59128086，加-disablegfxfirmware bootflag允许Kaby湖iGPU的引导+取决于你的主板可能需要AptioMemoryFix.efi在drivers64UEFI文件夹中。  或者即使删除了FakePCIID kexts并且将ig-platform-id和IntelGFX留空，你仍然可以获得加速，因为（U）HD 630本机支持已经完成。  如果在此之后你仍然无法启动/加速你的问题是别的 

- 回答2

  嗨Hackintosher，谢谢你的回复。我在论坛的某个地方读到了核心i5 8400的iGPU UHD630由High Sierra本机支持。我已经使用unibeast准备了usb密钥，并且只在kext额外文件夹中保留了fakesmc并完成了安装。只有改变我必须在主板上禁用secureboot并启用AHCI。  我现在不在家。我将根据上述建议进行更改并与您分享结果。  请告诉我哪个SMBIOS设置14,2 18,1,18,2等适合我当前的配置。  让我尝试一下我身边的所有排列和组合，检查它是否有效。

### 引导黑屏问题

- 引导进入安装界面黑屏，需要用手电筒照着才能看到苹果图标

  + 回答1

    ```
    Name: com.apple.driver.AppleIntelKBLGraphicsFramebuffer
    Find: 00000800 02000000 98000000 02040A00 00080000 87010000 03060A00 00040000 87010000 FF000000 01000000 20000000
    Replace: 00000800 00040000 87010000 FF000000 01000000 20000000 FF000000 01000000 20000000 FF000000 01000000 20000000
    Comment: Modify 0x591B0000 video ports to match 15W (port 0 to eDP, ports1-3 non existents)
    ```

    [原文链接](https://www.tonymacx86.com/threads/help-black-screen-when-uhd630-run-with-internal-screen.250577/page-5#post-1762999)

  + 回答2

    软件设置如下：

    ```
    Comment	8750h黑屏补丁
    Find	00000800 02000000 98000000
    Name	com.apple.driver.AppleIntelKBLGraphicsFramebuffer
    Replace	00000800 02000000 87010000
    ```

    改文件：在`<key>KextsToPatch</key>  `标签下的`<array>  `中添加下面的配置

    ```
    <dict>
        <key>Comment</key>
        <string>8750h黑屏补丁</string>
        <key>Disabled</key>
        <false/>
        <key>Find</key>
        <data>
        AAAIAAIAAACYAAAA
        </data>
        <key>InfoPlistPatch</key>
        <false/>
        <key>Name</key>
        <string>com.apple.driver.AppleIntelKBLGraphicsFramebuffer</string>
        <key>Replace</key>
        <data>
        AAAIAAIAAACHAQAA
        </data>
    </dict>
    ```

    