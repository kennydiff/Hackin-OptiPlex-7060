# Hackintosh-OptiPlex-7060-SFF(OpenCore)
**OpenCore Bootloader tested on Big Sur 11.6.2**

**2022-01-07**

- Upgrade macOS to Big Sur 11.6.2
- OpenCore Updated to 0.7.6
- Upgrade all the KEXT and Driver
- 深度休眠还是会重启，在BIOS里Power Management → Block Sleep: ***check*** ，可实现局部睡眠，唤醒。

**2021-01-07**

- 将OpenCore升级到0.6.5
- 删除OC的Tools文件夹的工具（被证实在正式系统中无用）
- 删除AMD显卡的驱动 WhateverGreen.kext
- 从windows 的SSDTTime 重新定制本机(OptiPlex-7060)的SSDT

**2020-12-31**

* 从webleon的OptiPlex7070SFF fork过来，安装Catalina 10.15.7后直接几乎完美，感谢webleon

**2020-11-15**

* Changed bootloader to Opencore 0.6.3
* Update MacOS to Big Sur 11.0.1
* Installed a dedicate GPU RX560, changed SMBIOS to iMac 19,1
* ALC255 Audio didn't work with default OC configuration caused by IRQ conflicts. These has been patched with [SSDTTime](https://github.com/corpnewt/SSDTTime) 

**2020-03-27**

* Update MacOS to Catalina 10.15.4

## Introdution
This is the Hackintosh EFI Folder for Dell OptiPlex 7070 Small Form Factor. The configuration settings support MacOS Catalina and Big Sur. 
Because deep sleep will cause a kernel panic, I blocked sleep in BIOS. 

I'm using a iMac 19,1 SMBIOS to improve performance with dedicate GPU. If you only using the intergrated iGPU, set SMBIOS to Macmini 8,1 will avoid most of the issues with video. 

You will have to [**generate a new SMIBIOS**](https://github.com/corpnewt/GenSMBIOS) before login to your iCloud account.

## Hardware Specs
* **Desktop Computer**: Dell OptiPlex 7070 Small Form Factor
* **CPU**: [Intel® Core™ i7-8700(Coffee Lake)](https://ark.intel.com/content/www/us/en/ark/products/126686/intel-core-i7-8700-processor-12m-cache-up-to-4-60-ghz.html)
* **iGPU**: Intel® UHD Graphics 630
* **RAM**: 32GB DDR4 2666 Daul Channel
* **HDD**: Crucial P5 1TB PCIe M.2 2280SS SSD
* **Wi-Fi & Bluetooth**: BCM94360CS2 with NGFF Adapter

## Working
* CPU Turbo Boost & Thermal Throttling
* Radeon™ RX 560 & iGPU acceleration
* ALC 255 audio
* All USB Ports
* LAN & Wireless Network
* Airdrop & Airplay
* Partly Sleep & Wakeup

## Not working
* 深度休眠后会内核出错重启

## BIOS Settings
* General → Advanced Boot Options: ***uncheck***
* System Configuration → SATA Operation: ***AHCI***
* Secure Boot → Secure Boot Enable: ***Disabled***
* Intel® Software Guard Extensions™ → Intel® SGX™ Enable: ***Disabled***
* Power Management → Block Sleep: ***check***
* Virtualization Support → VT for Direct I/O: ***uncheck***

## BIOS Settings via GRUB (Optional)
* Set Pre-Allocated DVMT to 64M: 
***setup_var 0x8DC 0x02***
* Disable CFG lock: 
***setup_var 0x5BE 0x00***
