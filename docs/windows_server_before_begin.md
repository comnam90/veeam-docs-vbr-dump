---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/windows_server_before_begin.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you add a Microsoft Windows server to the backup infrastructure, check network connection settings of this server.

* Check permissions required to add the server. For more information, see [Permissions](required_permissions.md#rphost).

* File and printer sharing must be enabled in network connection settings of the added Microsoft Windows server. On every connected Microsoft Windows server, Veeam Backup & Replication deploys two components:

+ Veeam Installer Service
+ Veeam Data Mover Service/Veeam Transport Service

If file and printer sharing is not enabled, Veeam Backup & Replication will fail to deploy these components.

* [For Microsoft Hyper-V] If you plan to use PowerShell Direct, Microsoft PowerShell 2.0 or later must be installed on the added server. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/virtualization/hyper-v-on-windows/user-guide/powershell-direct).

Page updated 8/26/2025

Page content applies to build 13.0.1.1071
