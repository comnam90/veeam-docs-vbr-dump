---
title: "get-veodmailsettings"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veodmailsettings.html"
last_updated: "1/23/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns Veeam Explorer for Microsoft OneDrive for Business email settings. Veeam Explorer for Microsoft OneDrive for Business uses these settings to send Microsoft OneDrive items as attachments in email messages.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Rental License, Subscription License

Syntax

|  |
| --- |
| Get-VEODMailSettings [<CommonParameters>] |

Detailed Description

This cmdlet returns email settings configured for Veeam Explorer for Microsoft OneDrive for Business.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VBOOneDriveMailSettings](vboonedrivemailsettings.md) object that contains mail settings configured for Veeam Explorer for Microsoft OneDrive for Business.

Example

Getting Email Settings

This command returns email settings.

|  |
| --- |
| Get-VEODMailSettings |

Page updated 1/23/2025

Page content applies to build 13.0.1.1071
