- 用len的镜像，卡在 error:6 table load failures 
***
- 黑果的镜像里有个Fix AsRock Z390 BIOS DSDT Device（RTC）bug的选项，以为自己用的是AUSU的主板不需要这个选项，结果取消了之后不能进系统了。

- 核显也没驱动起来，准备下个新的镜像[【Len's DMG】macOS Catalina 10.15.2 19C57 With Clover 5100 and OC 0.5.2镜像）](http://bbs.pcbeta.com/viewthread-1836586-1-1.html)。[下载地址](https://github.com/oceansong/heipingguo/blob/master/%E4%B8%8B%E8%BD%BD%E5%9C%B0%E5%9D%80.md)装一下试试，只不过这个镜像是clover和OpenCore（OC）双引导的，没有PE应该是比较不方便。

- 装新镜像之前把需要的软件备份到NAS。

- 要重装了。其实除了关机死机、不能用核显外也没什么毛病。2020-03-22

- 刚开始装就遇到麻烦了。多亏麻烦遇到的早，要是抹了盘再出问题就闹心了。

- 才发现编辑config.plist应该用xcode。用[ProperTree](https://blog.xjn819.com/wp-content/uploads/2019/10/ProperTree.zip)也不错

- 重装前，先烤一晚上机。(烤了一晚上，也没啥问题。）

- 加了xjn的qq群。都是用OC引导的。我也准备该用OC再重装一次了。
  - 加了群终于知道应该从哪个帖子开始学习了。
  > [精解OpenCore](https://blog.daliansky.net/OpenCore-BootLoader.html#附录1-opencore-支持的内核驱动-kext-及其用途)

- 新买的无线网卡装上了。京东买的[BCM94360CD](https://item.jd.com/18967921252.html)。WiFi和蓝牙倒是免驱能用了。可是随航和隔空投送还是不行。

- 启动台的残留问题还是用[launchpad Manager](http://launchpadmanager.com/)解决吧。只是清除的话也不用花钱。

[这可能是对“小白”最友好的黑苹果安装教程（Catalina 10.15.5 安装记录）](https://zhuanlan.zhihu.com/p/148284358)

机型的选择

- iMac18,1 这个机型是使用核显做显示器输出的，从AGPM的info.plist信息中能看到这种机型为iGPU做了很多的设置。
- iMac18,3/18,2 这个机型独显做显示输出，核显仅参与一些计算任务，这种机型的AGPM的info.plist信息中，iGPU的设置参数做了简化。
- iMacPro1,1 MacProX,X 独显输出，默认不开启核显，而且独显有各种机型的专用显卡硬件ID匹配，没有iGPU的设置参数。
- 其他机型类似，你需要到/System/Library/Extensions/AppleGraphicsPowerManagement.kext/Contents/info.plist里去核对

