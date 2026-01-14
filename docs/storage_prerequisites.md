---
title: "Universal Storage API Integrated Systems"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/storage_prerequisites.html"
last_updated: "1/6/2026"
product_version: "13.0.1.1071"
---

# Universal Storage API Integrated Systems

In this article

[For VMware, Veeam Agent integration] Before you add storage systems to Veeam Backup & Replication, check the following requirements:

* You must install the storage system plug-in. For more information, see [Installing Storage System Plug-Ins (Linux Server)](storage_install_plugin_linux.md).

* Check requirements the following requirements:

* [DataCore SANsymphony](https://www.veeam.com/kb4128)
* [Dell PowerMax](https://www.veeam.com/kb4200)
* [Dell PowerStore](https://www.veeam.com/kb4243)
* [Dell SC Series](https://www.veeam.com/kb4798)
* [Fujitsu ETERNUS AF/DX Series](https://www.veeam.com/kb4043)
* [Hitachi VSP/VSP One Block](https://www.veeam.com/kb4191)
* [IBM FlashSystem](https://www.veeam.com/kb4650)
* [INFINIDAT InfiniBox F Series](https://www.veeam.com/kb4009)
* [NEC Storage M Series](https://www.veeam.com/kb4274)
* [NetApp SolidFire/HCI](https://www.veeam.com/kb4044)
* [Pure Storage FlashArray](https://www.veeam.com/kb4129)
* [Tintri IntelliFlash/Western Digital/Tegile](https://www.veeam.com/kb3226)

* [For Dell SC] Make sure that multiple proxy servers are not part of a single Server object.
* Some storage system vendors provide the capability to configure additional integration options — such as limiting the scope of storage systems involved in the integration, specifying the primary node in active-active replication scenarios or others. After you add the storage system to the backup infrastructure, edit the configuration file and specify the options provided by the vendor. For the Linux-based backup server, edit the /etc/veeam/plugins/storages/<plugin-name> configuration file as described in [Performing Maintenance Tasks](hmc_perform_maintenance_tasks.md#config). For the Microsoft Windows-based backup server, edit the C:\ProgramData\Veeam\Storage\<Plugin Name> configuration file. For the information on the file format and the list of available options, see the vendor documentation of the plug-in.

Page updated 1/6/2026

Page content applies to build 13.0.1.1071
