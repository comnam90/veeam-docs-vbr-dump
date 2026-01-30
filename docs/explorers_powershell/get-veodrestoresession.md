---
title: "Get-VEODRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veodrestoresession.html"
last_updated: "1/30/2025"
product_version: "13.0.1.1071"
---

# Get-VEODRestoreSession


Short Description

Returns active restore sessions started to perform operations with backed-up OneDrive items.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Community, Rental License, Subscription License

Syntax

|  |
| --- |
| Get-VEODRestoreSession [<CommonParameters>] |

Detailed Description

This cmdlet returns active Veeam Explorer for Microsoft OneDrive for Business restore sessions.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VBOOneDriveItemRestoreSession](vboonedriveitemrestoresession.md)[] array that contains restore sessions started to perform operations with backed-up OneDrive items.

Example

Getting Restore Sessions

This command returns all active restore sessions started to perform operations with backed-up OneDrive items.

|  |
| --- |
| Get-VEODRestoreSession |


