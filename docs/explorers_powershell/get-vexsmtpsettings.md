---
title: "Get-VEXSmtpSettings"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vexsmtpsettings.html"
last_updated: "2/27/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns SMTP settings.

|  |
| --- |
| Note |
| In Veeam Backup for Microsoft 365 7a and Veeam Backup & Replication 12.1, this cmdlet became deprecated. Use the [Get-VEXMailSettings](get-vexmailsettings.md) cmdlet to get email settings. |

Applies to

Veeam Backup & Replication, Veeam Backup for Microsoft 365

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEXSmtpSettings [<CommonParameters>] |

Detailed Description

This cmdlet returns SMTP settings configured for Veeam Explorer for Microsoft Exchange. You may want to get information on these settings before sending restored mailbox items as email attachments.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEXSmtpSettings](vexsmtpsettings.md) object that contains SMTP settings configured for Veeam Explorer for Microsoft Exchange.

Example

Getting SMTP Settings

This command returns SMTP settings configured for Veeam Explorer for Microsoft Exchange.

|  |
| --- |
| Get-VEXSmtpSettings |

Page updated 2/27/2025

Page content applies to build 13.0.1.1071
