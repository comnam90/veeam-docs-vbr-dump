---
title: "Publishing Disks"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/integration_publish.html"
last_updated: "2/13/2026"
product_version: "13.0.1.1071"
---

# Publishing Disks


You can use the Veeam backup console to publish disks from Veeam Agent backups.

|  |
| --- |
| TIP |
| You can publish disks using the PowerShell console. To learn more, see the [Disk Publishing (Data Integration API)](https://helpcenter.veeam.com/docs/vbr/powershell/veeam_data_integration_api.html?ver=13) section in the Veeam PowerShell Reference. |

Disk publishing allows you to save time by getting backup content of one or multiple disks instead of all disks from a backup. This technology gives read-only access to data and helps if you want to analyze data of your backup. For example, look for specific documents or usage patterns, or perform antivirus scan of backed-up data.

You can publish disks from backups of Veeam Agent computers created with the following Veeam Agents:

* Veeam Agent for Microsoft Windows
* Veeam Agent for Linux
* Veeam Agent for Oracle Solaris
* Veeam Agent for IBM AIX
* Veeam Agent for Mac

To publish disks from a backup of a Veeam Agent computer to a target server, Veeam Backup & Replication uses one of the following storage network protocols depending on the target server OS:

* [For Windows-based target servers] iSCSI
* [For Linux and macOS-based target servers] FUSE
* [For Unix-based target servers] NFS

To learn more, see [Disk Publishing](data_integration_api.md).


