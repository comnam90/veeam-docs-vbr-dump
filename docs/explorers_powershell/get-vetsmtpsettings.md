---
title: "Get-VETSmtpSettings"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vetsmtpsettings.html"
last_updated: "2/28/2025"
product_version: "13.0.1.1071"
---

# Get-VETSmtpSettings


Short Description

Returns SMTP settings.

|  |
| --- |
| Note |
| In Veeam Backup for Microsoft 365 7a and Veeam Backup & Replication 12.1, this cmdlet became deprecated. Use the [Get-VETMailSettings](get-vetmailsettings.md) cmdlet to get email settings. |

Applies to

Veeam Backup for Microsoft 365

Product Edition: Community, Rental License, Subscription License

Syntax

|  |
| --- |
| Get-VETSmtpSettings [<CommonParameters>] |

Detailed Description

This cmdlet returns SMTP settings configured for Veeam Explorer for Microsoft Teams. You may want to get information on these settings before sending restored Microsoft Teams items as email attachments.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VETSmtpSettings](vetsmtpsettings.md) object that contains SMTP settings configured for Veeam Explorer for Microsoft Teams.

Example

Getting SMTP Settings

This command returns SMTP settings configured for Veeam Explorer for Microsoft Teams.

|  |
| --- |
| Get-VETSmtpSettings |


