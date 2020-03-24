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
