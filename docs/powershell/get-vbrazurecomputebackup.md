---
title: "Get-VBRAzureComputeBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazurecomputebackup.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAzureComputeBackup


Short Description

Returns Azure backups.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAzureComputeBackup [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of Azure backups.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names for Azure backups. The cmdlet will return Azure backups with the specified names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAzureComputeBackup object that contains an array of Azure backups.

Examples

Getting Azure Backups

This command returns an array of Azure backups.

|  |
| --- |
| Get-VBRAzureComputeBackup |


