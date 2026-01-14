---
title: "Get-VBRTapeMedium"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrtapemedium.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Get-VBRTapeMedium

In this article

Short Description

Returns tapes.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get tapes by names.

|  |
| --- |
| Get-VBRTapeMedium [-Name <String[]>]  [<CommonParameters>] |

* Get tapes in selected drives.

|  |
| --- |
| Get-VBRTapeMedium -Drive <VBRTapeDrive[]> [-Name <String[]>]  [<CommonParameters>] |

* Get tapes by IDs.

|  |
| --- |
| Get-VBRTapeMedium -Id <Guid[]> [-Name <String[]>]  [<CommonParameters>] |

* Get tapes in selected libraries.

|  |
| --- |
| Get-VBRTapeMedium [-Name <String[]>] -Library <VBRTapeLibrary[]>  [<CommonParameters>] |

* Get tapes in selected media pools.

|  |
| --- |
| Get-VBRTapeMedium [-Name <String[]>] -MediaPool <VBRTapeMediaPool[]>  [<CommonParameters>] |

* Get tapes in selected vaults.

|  |
| --- |
| Get-VBRTapeMedium [-Name <String[]>] -Vault <VBRTapeVault[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns tapes managed by Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of tape names. The cmdlet will return tapes with these names. | String[] | False | Named | True (ByValue, ByProperty Name) |
| Drive | Specifies the array of drives. The cmdlet will return tapes located in these drives. | Accepts the [VBRTapeDrive[]](vbrtapedrive.md) object, GUID or string. To get this object, run the [Get-VBRTapeDrive](get-vbrtapedrive.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Id | Specifies the array of tape IDs. The cmdlet will return tapes with these IDs. | Accepts GUID[] or string[]. | True | Named | True (ByValue, ByProperty Name) |
| Library | Specifies the array of tape libraries. The cmdlet will return tapes in these libraries. | Accepts the [VBRTapeLibrary[]](vbrtapelibrary.md) object, GUID or string. To get this object, run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| MediaPool | Specifies the array of media pools. The cmdlet will return tapes in these media pools. | Accepts the [VBRTapeMediaPool[]](vbrtapemediapool.md) object, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Vault | Specifies the array of vaults. The cmdlet will return tapes in these vaults. | Accepts the [VBRTapeVault[]](vbrtapevault.md) object, GUID or string. To get this object, run the [Get-VBRTapeVault](get-vbrtapevault.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRTapeMedium[]](vbrtapemedium.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Tape by Name

|  |  |
| --- | --- |
| This command gets a tape named 00110001.  |  | | --- | | Get-VBRTapeMedium -Name "00110001" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Tape by Barcode

|  |  |
| --- | --- |
| This example shows how to get a tape with the 00233400 barcode.  |  | | --- | | Get-VBRTapeMedium | Where-Object {$\_.Barcode -eq "00233400"} |  Perform the following steps:   1. Run the Get-VBRTapeMedium cmdlet to get all tapes. 2. Pipe the cmdlet output to the Where-Object cmdlet. Specify the Barcode value to equal 00233400. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Tapes in Media Pool

|  |  |
| --- | --- |
| This example shows how to get the list of tapes in the Incremental Backups media pool.  |  | | --- | | $IncrementalBackups = Get-VBRTapeMediaPool -Name "Incremental Backups"  Get-VBRTapeMedium -MediaPool $IncrementalBackups |  Perform the following steps:   1. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save the result to the $IncrementalBackups variable. 2. Run the Get-VBRTapeMedium cmdlet. Set the $IncrementalBackups variable as the MediaPool parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Expired Tapes in Vault

|  |  |
| --- | --- |
| This example shows how to look for the expired tapes within the Sydney vault.  |  | | --- | | $Sydney = Get-VBRTapeVault -Name "Sydney"  Get-VBRTapeMedium -Vault $Sydney | ?{$\_.IsExpired} |  Perform the following steps:   1. Run the [Get-VBRTapeVault](get-vbrtapevault.md) cmdlet. Specify the Name parameter value. Save the result to the $Sydney variable. 2. Run the Get-VBRTapeMedium cmdlet. Set the $Sydney variable as the Vault parameter value. 3. Pipe the cmdlet output to the query to find all expired tapes. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRTapeMediaPool](get-vbrtapemediapool.md)
* [Get-VBRTapeLibrary](get-vbrtapelibrary.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
