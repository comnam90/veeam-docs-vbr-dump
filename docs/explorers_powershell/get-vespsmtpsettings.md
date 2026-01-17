---
title: "Get-VESPSmtpSettings"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vespsmtpsettings.html"
last_updated: "2/27/2025"
product_version: "13.0.1.1071"
---

# Get-VESPSmtpSettings


Short Description

Returns SMTP settings.

|  |
| --- |
| Note |
| In Veeam Backup & Replication 12.1 and Veeam Backup for Microsoft 365 7a, this cmdlet became deprecated. Use the [Get-VESPMailSettings](get-vespmailsettings.md) cmdlet to get email settings. |

Applies to

Veeam Backup for Microsoft 365, Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESPSmtpSettings [<CommonParameters>] |

Detailed Description

This cmdlet returns SMTP settings configured for Veeam Explorer for Microsoft SharePoint. These settings are needed if you want to send restored SharePoint items as email attachments.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESPSmtpSettings](vespsmtpsettings.md) object that contains SMTP settings configured for Veeam Explorer for Microsoft SharePoint.

Example

Getting SMTP Settings

This command returns SMTP settings configured for Veeam Explorer for Microsoft SharePoint.

|  |
| --- |
| Get-VESPSmtpSettings |


