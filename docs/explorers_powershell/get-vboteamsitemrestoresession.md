---
title: "Get-VBOTeamsItemRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vboteamsitemrestoresession.html"
last_updated: "2/6/2025"
product_version: "13.0.1.1071"
---

# Get-VBOTeamsItemRestoreSession


Short Description

Returns active restore sessions started to perform operations with backed-up Microsoft Teams items.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Rental License, Subscription License

Syntax

|  |
| --- |
| Get-VBOTeamsItemRestoreSession [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of active restore sessions started to perform operations with backed-up Microsoft Teams objects.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VBOTeamsRestoreSession](vboteamsrestoresession.md)[] array that contains active restore sessions started to perform operations with backed-up Microsoft Teams objects.

Example

Getting Restore Sessions

This command returns all active restore sessions started to perform operations with backed-up Microsoft Teams objects.

|  |
| --- |
| Get-VBOTeamsItemRestoreSession |


