#OC0.8.4

不知道是我这块主板的问题还是其他什么原因，前段时间又突然不能引导了，显卡换回RX460，BIOS恢复出厂设置也不行。
之前好好的 EFI 不能用，更离谱的时候是甚至连 Windows 都不能安装。整个人差点给搞崩溃。
不得已拿掉主板电池，短接恢复出厂，黑苹果又神奇的起来了。

黑苹果在我这里感觉真的是一门玄学了。

几个注意事项，我现在还能记得的，列在下面，希望能帮忙碰到类似问题的朋友。

* 用主板自带的一键黑苹果选项后要单独检查安全启动是不是没有关闭
* 如果 Windows 能正常引导但是黑苹果不行，很大可能是安全启动没有关闭
* 还需要注意主板靠边的那个 PCI-E 槽如果插入非显卡设备可能会导致不能安装、引导系统的问题
* 如果碰到莫名其妙不能解决的问题可以考虑拔电池短接恢复出厂
* 如非必要，opencore 的版本不用跟随官方更新，稳定是王道

目前的OC 版本为 0.8.4，短时间内不准备升级。

# MSI-B460M-MORTAR-Hackintosh
微星B460M迫击炮黑苹果，个人自用长期更新维护。原始配置搜罗于网络，后自己做了些修改，如果正好能碰到相同或者类似配置的朋友帮到你了，那是我的荣幸。

我目前这块板子不准备升级 Ventura 了，在 Ventura 上感觉更容易出问题。

## 软件版本
* macOS： Monterey 12.4
* OpenCore： [0.8.4](https://github.com/acidanthera/OpenCorePkg/releases/tag/0.8.4)
* 机型：macpro7,1

![macOS](macOS.png)

## 硬件配置
* 主板：微星B460M迫击炮（无WiFi版） 
* CPU：英特尔 i5 10400
* GPU：核显 UHD 630 + RX460
* 网卡：板载网卡 Realtek® RTL8125B 2.5G LAN
* 声卡：板载声卡 Realtek® ALC1200
* 硬盘：M.2 256GB （系统盘）+ SATA固态1TB用于照片存储
* 内存：32G
* 机箱：德商德静界 SILENTBASE 801 （好大个）

## USB 端口定制

这是我发在 pcbeta 上的一个帖子，分享这个主板的USB端口：https://bbs.pcbeta.com/forum.php?mod=viewthread&tid=1933108

|类型	|名称	    |位置ID	    |接口	|连接器	    |备注|
|------|--------|----------|--------|-----------|--------------|
|XHC	|HS01	|0x14100000	|0x01	|USB2	    |后置面板网口旁USB-A口|
|XHC	|HS02	|0x14200000	|0x02	|USB2	    |后置面板网口旁USB-A口|
|XHC	|HS03	|0x14300000	|0x03	|USB2	    |后置面板USB-C口旁USB-A口|
|XHC	|HS04	|0x14400000	|0x04	|TypeC+Sw	|后置面板USB-C口|
|XHC	|HS05	|0x14500000	|0x05	|USB2	    |主板扩展口JUSB3|
|XHC	|HS06	|0x14600000	|0x06	|USB2	    |主板扩展口JUSB3|
|XHC	|HS09	|0x14700000	|0x09	|USB2	    |后置面板PS2口旁USB-A口|
|XHC	|HS10	|0x14800000	|0x0A	|USB2	    |后置面板PS2口旁USB-A口|
|XHC	|HS11	|0x14900000	|0x0B	|Internel	|内置USB2.0Hub,主板扩展口JUSB1和JUSB2|
|XHC	|SS01	|0x14A00000	|0x11	|USB3	    |后置面板网口旁USB-A口|
|XHC	|SS02	|0x14B00000	|0x12	|USB3	    |后置面板网口旁USB-A口|
|XHC	|SS03	|0x14C00001	|0x13	|USB3	    |后置面板USB-C口旁USB-A口|
|XHC	|SS04	|0x14D00001	|0x14	|TypeC+Sw	|后置面板USB-C口|
|XHC	|SS05	|0x14E00002	|0x15	|USB3	    |主板扩展口JUSB3|
|XHC	|SS06	|0x14F00002	|0x16	|USB3	    |主板扩展口JUSB3|
|XHC	|HS07	|N/A    	|N/A	|Type-C 2.0	|主板扩展口JUSB4|
|XHC	|SS07	|N/A    	|N/A	|Type-C 3.0 |主板扩展口JUSB4|
|XHC	|HS12	|N/A    	|N/A	|内置微星灯效控制|内置微星灯效控制|

![USBPorts](OC0.7.8USBPorts.png)

我用的机箱有一个前置的USB2.0，两个前置的3.0.
前置2.0接到了主板的JUSB1上，无线网卡的蓝牙线接到了主板的JUSB2上。
前置3.0接到了主板的JUSB3上。
没有前置USB C口所有刚好15个。

## 已知问题
* 部分驱动为debug版本
* 主板旁边的PCI如果插入固态转接卡会无法启动，暂未找到方案
* 最近发现长时间关机后第一次开机时会出现卡住不能正常进系统的情况，第二次重启就好了

## 感谢
* https://dortania.github.io/OpenCore-Install-Guide/
* https://github.com/ahuinee/OpenCore-EFI
* https://github.com/hurole/Hackintosh-MSI_B460M_MORTAR
* https://github.com/Spectrelai/Hackintosh-B460M-MORTAR-WIFI

## 工具
* ProperTree: https://github.com/corpnewt/ProperTree
* GenSMBIOS: https://github.com/corpnewt/GenSMBIOS
* gibMacOS：https://github.com/corpnewt/gibMacOS
* Hackintool：https://github.com/headkaze/Hackintool
* USBMap：https://github.com/corpnewt/USBMap