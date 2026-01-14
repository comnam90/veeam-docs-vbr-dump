---
title: "get-vexmailsettings"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vexmailsettings.html"
last_updated: "2/28/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns Veeam Explorer for Microsoft Exchange email settings. Veeam Explorer for Microsoft Exchange uses these settings to send Exchange items that are located in a backup through email and deliver export reports.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEXMailSettings [<CommonParameters>] |

Detailed Description

This cmdlet returns email settings configured for Veeam Explorer for Microsoft Exchange.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEXMailSettings](vexmailsettings.md) object that contains mail settings configured for Veeam Explorer for Microsoft Exchange.

Example

Getting Email Settings

This command returns email settings.

|  |
| --- |
| Get-VEXMailSettings |

Page updated 2/28/2025

Page content applies to build 13.0.1.1071
