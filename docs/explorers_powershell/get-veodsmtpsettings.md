---
title: "Get-VEODSmtpSettings"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veodsmtpsettings.html"
last_updated: "2/27/2025"
product_version: "13.0.1.1071"
---

# Get-VEODSmtpSettings


Short Description

Returns SMTP settings.

|  |
| --- |
| Note |
| In Veeam Backup for Microsoft 365 7a and Veeam Backup & Replication 12.1, this cmdlet became deprecated. Use the [Get-VEODMailSettings](get-veodmailsettings.md) cmdlet to get email settings. |

Applies to

Veeam Backup for Microsoft 365

Product Edition: Rental License, Subscription License

Syntax

|  |
| --- |
| Get-VEODSmtpSettings [<CommonParameters>] |

Detailed Description

This cmdlet returns SMTP settings configured for Veeam Explorer for Microsoft OneDrive for Business. These settings are required if you want to send restored OneDrive items as email attachments.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VBOOneDriveSmtpSettings](vboonedrivesmtpsettings.md) object that contains SMTP settings configured for Veeam Explorer for Microsoft OneDrive for Business.

Example

Getting SMTP Settings

This command returns SMTP settings configured for Veeam Explorer for Microsoft OneDrive for Business.

|  |
| --- |
| Get-VEODSmtpSettings |


