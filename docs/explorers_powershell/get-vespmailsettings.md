---
title: "Get-VESPMailSettings"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vespmailsettings.html"
last_updated: "2/6/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns Veeam Explorer for Microsoft SharePoint email settings. Veeam Explorer for Microsoft SharePoint uses these settings to send Microsoft SharePoint items as attachments in email messages and deliver export reports.

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESPMailSettings [<CommonParameters>] |

Detailed Description

This cmdlet returns email settings configured for Veeam Explorer for Microsoft SharePoint.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESPMailSettings](vespmailsettings.md) object that contains mail settings configured for Veeam Explorer for Microsoft SharePoint.

Example

Getting Email Settings

This command returns email settings.

|  |
| --- |
| Get-VESPMailSettings |

Page updated 2/6/2025

Page content applies to build 13.0.1.1071
