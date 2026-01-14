---
title: "Sync-VBRBackupRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-vbrbackuprepository.html"
last_updated: "9/3/2025"
product_version: "13.0.1.1071"
---

# Sync-VBRBackupRepository

In this article

Short Description

Rescans a backup repository.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Sync-VBRBackupRepository -Repository <CBackupRepository[]>  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to rescan a backup repository and get details on backups stored on it.

You can perform the repository rescan, for example, in case you have imported or copied backups.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies the array of backup repositories you want to rescan. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

CBaseSession

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Rescanning Backup Repository [Using Variable]

|  |  |
| --- | --- |
| This example shows how to rescan the repository named Local Repository 01.  |  | | --- | | $repository = Get-VBRBackupRepository -Name "Local Repository 01"  Sync-VBRBackupRepository -Repository $repository |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the Sync-VBRBackupRepository cmdlet. Set the $repository variable as the Repository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Rescanning Backup Repository [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to rescan the repository named Local Repository 01.  |  | | --- | | Get-VBRBackupRepository -Name "Local Repository 01" | Sync-VBRBackupRepository |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Sync-VBRBackupRepository cmdlet. |

Related Commands

[Get-VBRBackupRepository](get-vbrbackuprepository.md)

Page updated 9/3/2025

Page content applies to build 13.0.1.1071
