---
title: "Get-VBRApplicationBackupSnapshot"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrapplicationbackupsnapshot.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRApplicationBackupSnapshot


Short Description

Returns application backup snapshots.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get snapshots by name.

|  |
| --- |
| Get-VBRApplicationBackupSnapshot [-Name <String[]>]  [<CommonParameters>] |

* Get snapshots by ID.

|  |
| --- |
| Get-VBRApplicationBackupSnapshot -Id <Guid[]>  [<CommonParameters>] |

* Get snapshots by application backup repository.

|  |
| --- |
| Get-VBRApplicationBackupSnapshot -Repository <VBRApplicationBackupRepository>  [<CommonParameters>] |

Detailed Description

This cmdlet returns application backup repository snapshots. You can get snapshots by name, ID, or application backup repository. If you run the cmdlet without parameters, it will return all application backup repository snapshots.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Id | Specifies an array of IDs for application backup snapshots. The cmdlet will return the snapshots with these IDs. | Guid[] | True | Named | False |
| Name | Specifies an array of names of application backup snapshots. The cmdlet will return snapshots with these names. | String[] | False | Named | False |
| Repository | Specifies the application backup repository. The cmdlet will return snapshots stored in this repository. | Accepts the [VBRApplicationBackupRepository](vbrapplicationbackuprepository.md) object. To get this object, run the [Get-VBRApplicationBackupRepository](get-vbrapplicationbackuprepository.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRApplicationBackupSnapshot](vbrapplicationbackupsnapshot.md) object that contains information about the application backup snapshot.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1: Getting Application Backup Snapshots by Name

|  |  |
| --- | --- |
| This command gets an application backup repository snapshot by its name.  |  | | --- | | Get-VBRApplicationBackupSnapshot -Name "Snapshot\_01" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2: Getting Application Backup Snapshots by ID

|  |  |
| --- | --- |
| This command gets an application backup repository snapshot by its ID.  |  | | --- | | Get-VBRApplicationBackupSnapshot -Id 3f2504e0-4f89-11d3-9a0c-0305e82c3301 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3: Getting Application Backup Snapshots by Repository

|  |  |
| --- | --- |
| This example shows how to get snapshots for the Oracle FRA Repository application backup repository.  |  | | --- | | $repository = Get-VBRApplicationBackupRepository -Name "Oracle FRA Repository"  Get-VBRApplicationBackupSnapshot -Repository $repository |  Perform the following steps:   1. Run the [Get-VBRApplicationBackupRepository](get-vbrapplicationbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the Get-VBRApplicationBackupSnapshot cmdlet. Set the $repository variable as the Repository parameter value. |

Related Commands

[Get-VBRApplicationBackupRepository](get-vbrapplicationbackuprepository.md)

Page updated 2026-06-04

