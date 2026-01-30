---
title: "Get-VBRCloudTapeRestoreSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudtaperestoresession.html"
last_updated: "1/26/2024"
product_version: "13.0.1.1071"
---

# Get-VBRCloudTapeRestoreSession


Short Description

Returns active restore sessions of the tenant data from tape.

Applies to

Product Edition: Enterprise

Requires Cloud Connect license

Syntax

|  |
| --- |
| Get-VBRCloudTapeRestoreSession  [<CommonParameters>] |

Detailed Description

This cmdlet returns active restore sessions of the tenant data from tape.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

Getting All Active Restore Sessions of Tenant Data from Tape

This command shows how to get all active restore sessions of the tenant data from tape.

|  |
| --- |
| Get-VBRCloudTapeRestoreSession |


