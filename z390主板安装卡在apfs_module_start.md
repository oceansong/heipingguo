## 使用的是黑果小兵的镜像
- 就是Ec0转EC的问题
- 安装的时候在clover的option里的APCI patching里把Ec0 to EC选上。等于remane Ec0 to EC
- 也可以用Clover Configurator 或者Hackintool修改config.plist文件。
- 有帖子说用rename的方法不安全。推荐使用打SSDT补丁的方法。
- 按照[tonymacx86里介绍的方法](https://www.tonymacx86.com/threads/guide-usb-power-property-injection-for-sierra-and-later.222266/post-1728645)打了SSDT-EC.aml、SSDT-USBX.aml两个补丁成功解决。
- 打了里面的两个补丁同时也解决的USB的问题。

```
Thank you for the findings and for writing this guide RehabMan, I could make it work on my build! :clap:

I wrote a shorter guide for beginners not familiar with Hackintosh topics and the common inspector tools we use:
1.) You can read "ioreg" several places but I cannot find a link or description at post #1 what ioreg actually is... So if you're wondering how you can view ioreg, there is an application called IORegistryExplorer (version 2.1 !), which you can download from here: https://www.tonymacx86.com/threads/guide-how-to-make-a-copy-of-ioreg.58368/ If you open it up it will show you a list in alphabetical order.. Look for the name "EC" (Embedded Controller), it will be before the FAN labels... If you can find the element called "EC" in there, continue with step 5.)
2.) If the "EC" element is not there in the IORegistryExplorer, you need to check if you have EC0 or the H_EC name (or neither) under the hood in so called ACPI. There is another application to check that: MaciASL. It's also not mentioned in post #1, you can download it from here: RehabMan / OS-X-MaciASL-patchmatic / Downloads — Bitbucket. Open it up, press Command + F, and search for these terms: "Device (H_EC)" and "Device (EC0)". You will hopefully find the H_EC or the EC0 code block (not both). Don't bother with the meaning of the code you see, you don't have to understand it. There will be a code block in a few lines down, starting with "Method (_STA, ....". If you see a "Return (Zero)" in this {} block, then it means it's ignored as per post #1.
So what we done in this step: You have to check if you have EC0 or H_EC device or neither in MaciASL. If you find EC0 or H_EC you need to check if it's ignored: "Return (Zero)" or not. Remember your findings...
3.) Now you know what you have under the hood...
If you didn't have EC0 or H_EC device or it's returning Zero in method _STA, then you need to copy the file SSDT-EC.aml (attached to this post) to your main macOS drive's EFI partition, under EFI/CLOVER/ACPI/patched.
If you have found the EC0 or H_EC device in IORegistryExplorer and it's not returning Zero in method _STA, then you need to add a Clover config patch in EFI/CLOVER/config.plist to rename "EC0 to EC" or "H_EC to EC". Choose which one you have. The patch can be seen in post #1, under the title: "Insuring AppleBusPowerControllerUSB loads". In the picture, the config.plist file was opened in an application called Xcode, available free from the Mac App Store.
4.) Restart you PC. Once macOS is loaded, open IORegistryExplorer again and check weather you see EC in the list. If "EC" shows up, everything is fine, continue with step 5.) If the name "EC" is still not there in IORegistryExplorer, start it over from 1.), more carefully.
5.) Check your system definition in a built in macOS app called "System Information". Under the "Hardware Overview" section, you can find your system definition at "Model identifier", for example: iMac 18,3
If you have newer system definition than Macbook8,1 or MacBookAir7,2 or MacBookPro12,1 or MacPro6,1 or MacMini7,1 or iMac15,2 THEN copy the file SSDT-USBX.aml (attached to this post) to your main macOS drive's EFI partition, under EFI/CLOVER/ACPI/patched.
If you use one of the system def listed above or older, then you have nothing to do, continue with step 6.)
6.) Restart your PC. Once macOS is loaded, plug in an iPhone or iPad to your Hackintosh with a USB cable. Open System Information app and choose the "USB" section from the left sidebar. Click on the iPhone or iPad in the list. If you can see all 4 lines you're won! ;)
Current Available (mA):
Current Required (mA):
Extra Operating Current (mA):
Sleep current (mA):
If all 4 lines are there, it's the obvious indicator of working USB power under macOS.
​
Hope this post will help others to understand the process described in post #1.
```
