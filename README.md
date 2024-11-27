#OC0.7.8

# MSI-B460M-MORTAR-Hackintosh
微星B460M迫击炮黑苹果，这块板子目前个人没再使用，换成了Windows系统。

升级降级过几次BIOS，这板子在我手里总有种很奇怪的感觉。升级是因为PCI-E*8 的插槽查PCI-E硬盘的时候出现了一次无法引导系统的情况，以为升级BIOS能解决。但是升级后感觉BIOS有的项目默认值变了，后来又看到说如果用黑苹果不要升级BIOS，升级后会有问题，就给降级回来了。从那之后就出现了之前好用的EFI再次安装系统的时候就死活不能引导的情况。全短时间心血来潮又安装黑苹果的时候误打误撞的用 [H370M](https://github.com/beta4better/GIGABYTE_H370M-DS3H_Hackintosh) 的板子的EFI竟然引导起来了。所以说总感觉这块主板很奇怪，但是往上有很多人都在用这块主板，而且说是黑苹果能接近完美的状态，我是一头雾水。目前1.0.2的两个配置都是基于另一块 [H370M](https://github.com/beta4better/GIGABYTE_H370M-DS3H_Hackintosh) 的板子来的。

## 软件版本
* macOS： Monterey 12.4
* OpenCore：https://github.com/acidanthera/OpenCorePkg
* 机型：iMac20,1

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

![USBPorts](OC0.7.8USBPorts.png)

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