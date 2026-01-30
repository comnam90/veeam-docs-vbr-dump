---
title: "System Requirements for Microsoft Windows Computers"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_system_requirements_windows.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# System Requirements for Microsoft Windows Computers


A computer that you want to protect with Veeam Agent for Microsoft Windows must meet the following requirements:

| Specification | Requirement |
| --- | --- |
| Hardware | CPU: x64.  Memory: 2 GB RAM or more. Memory consumption varies depending on the number and size of processed disks.  Disk Space: 200–700 MB for product installation. Required disk space varies depending on the Veeam Agent usage scenario.  Network: 1 Mbps or faster. High latency and reasonably unstable WAN links are supported.  System firmware: BIOS or UEFI.  Drive encryption: Microsoft BitLocker (optional). BitLocker encrypted volumes must be unlocked at the moment when Veeam Agent for Microsoft Windows starts the backup or restore operation. Only Microsoft BitLocker is supported for drive encryption. Other drive encryption products are not supported. |
| OS | 64-bit versions of the following operating systems are supported:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows Server 2012 R2 — if you use Veeam Backup & Replication on Microsoft Windows * Microsoft Windows 11 (from version 22H2 to version 25H2) * Microsoft Windows 10 General Availability Channel 22H2 * Microsoft Windows 10 Long-Term Servicing Channel (versions 2015, 2016, 2019, 2021)   Each Veeam Agent computer that consumes a license installed in Veeam Backup & Replication must have a unique BIOS UUID.  Note:   * Running Veeam Agent on Insider versions of Microsoft Windows Client and Server OSes is not supported. * Microsoft Windows OSes installed on ReFS boot partitions are not supported.  * Server Core installations of Microsoft Windows Server OSes can be backed-up only by Veeam Agent backup jobs managed by the Veeam backup server. Note: to ensure proper work of Veeam Agent, do not uninstall the WoW64 feature.  * Windows Embedded / Windows IoT OSes are supported (except for custom builds by certain vendors that do not have components required for Veeam Agent operation). |
| File System | Microsoft Windows FAT, NTFS, ReFS file systems are supported.  The supported file system must reside on a volume that is 64 TB or smaller, because Veeam Agent uses the Microsoft Software Shadow Copy Provider to create a volume shadow copy during the backup. To learn more, see [Microsoft documentation](https://support.microsoft.com/en-us/help/2967756/usability-limit-for-volume-shadow-copy-service-vss-in-windows). |
| Database | SQLite database engine (installed with the product). |
| Software | The following required 3rd party software is included in the Veeam Agent for Microsoft Windows Redistributable. During the Veeam Agent deployment process, Veeam Backup & Replication checks whether all prerequisite software is available on the target computer. If some of the required software components are missing, Veeam Backup & Replication will install missing software automatically.   * Veeam OpenSSL3 FIPS Provider * ASP.NET Core Runtime 8.0.21 * .NET Desktop Runtime 8.0.21   Note: If you already have ASP.NET Core Runtime and NET Desktop Runtime version 8.0.17 or later on your computer, new packages will not be installed. However, make sure that both products have the same version; otherwise Veeam Agent operations will fail. |

Considerations and Limitations

Consider the following:

* Veeam Agent for Microsoft Windows works with only those hard drive types that are supported by the Microsoft Windows OS. Thus, Veeam Agent supports the 512 bytes and 4 KB sector hard drives only. Other hard drive types are not supported. To learn more, see [this Microsoft article](https://support.microsoft.com/en-us/help/2510009/microsoft-support-policy-for-4k-sector-hard-drives-in-windows).
* Devices managed by Veritas Volume Manager are not supported.
* Supported culture settings depend on the version of Microsoft Windows OS installed on your computer. To learn more, see [this Microsoft article](https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c).

* Do not use Veeam Agent managed by one Veeam Backup & Replication installation on a server that acts as a backup infrastructure component in another Veeam Backup & Replication installation. If this happens, both Veeam Backup & Replication installations can automatically update the Transport and Deployer components on the host server, which may lead to performance issues or errors in your backup infrastructure.


