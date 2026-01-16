---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesp_ports.html"
last_updated: "1/15/2026"
product_version: "13.0.1.1071"
---

# Ports

In this article

The following table lists network ports that must be opened for managing traffic during recovery of Microsoft SharePoint data.

For more information on the ports used during backup, see the following sections:

* [Ports](used_ports.md) — for backups created with Veeam Backup & Replication
* [Ports](https://helpcenter.veeam.com/docs/vbo365/guide/vbo_used_ports.html?ver=8) section of the Veeam Backup for Microsoft 365 User Guide — for backups created with Veeam Backup for Microsoft 365.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup & Replication console | Backup server | TCP | 443 | Port used to communicate with the backup server. |
| Target SharePoint server | TCP | 80, 443 (according to SharePoint application settings) | Ports used to connect to the target Microsoft SharePoint machine.  For more information on recommended port numbers and protocols for SharePoint web application, see [this Microsoft article](https://learn.microsoft.com/en-us/sharepoint/security-for-sharepoint-server/security-hardening).  To discover ports currently used by your SharePoint web application, follow the steps described in [this Microsoft article](https://msdn.microsoft.com/en-us/library/hh167832%28v%3Dnav.70%29.aspx). |
| Staging server | TCP | 1433 or another port | Ports used to communicate with Microsoft SQL Server machines hosting content databases.  Exact port numbers depend on the configuration of Microsoft SQL Server.  For more information, see [this Microsoft article](http://msdn.microsoft.com/en-us/library/cc646023.aspx#BKMK_ssde). |
| 445 | Port used to connect to Microsoft Domain Services. |
| TCP, UDP, LDAP | 389 | Port used for validating the Microsoft SQL Server machine used as a staging server. |
| Mail server | TCP | 25, 587 or another port, 443 | Ports used for sending Microsoft SharePoint items.  Port 25 is used by default, but you can specify another port in the settings. To use SSL data encryption, specify port 587.  Port 443 is also used and cannot be changed. |
| Staging server | Mount server associated with the backup repository | TCP | 3260 to 3270 | Ports used by iSCSI initiator to connect to the iSCSI target. |
| Mount server associated with the backup repository | Backup repository | TCP | 6162 or 2500 to 3300 | Ports used to manage the mounting process.  Port 6162 is the default port used to connect to the Veeam Data Mover Service (for Windows-based backup servers) or Veeam Transport Service (for Linux-based backup servers). If port 6162 cannot be reached, the first available port in the 2500 to 3300 range is used instead. |

|  |
| --- |
| Note |
| To restore database items or lists to a server that is running in a DMZ, the SharePoint web application ports will be used. |

Page updated 1/15/2026

Page content applies to build 13.0.1.1071
