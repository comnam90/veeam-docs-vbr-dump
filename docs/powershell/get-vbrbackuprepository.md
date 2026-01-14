---
title: "Get-VBRBackupRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrbackuprepository.html"
last_updated: "4/3/2024"
product_version: "13.0.1.1071"
---

# Get-VBRBackupRepository

In this article

Short Description

Returns a list of backup repositories.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRBackupRepository [-Name <string[]>] [-ScaleOut]  [<CommonParameters>] |

Detailed Description

This cmdlet returns a list of backup repositories added to the backup infrastructure.

You can get a list of all backup repositories, get scale-out backup repositories or look for repositories directly by name.

|  |
| --- |
| Important |
| To get information on object storage repositories, run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept | Accept Wildcard Characters |
| --- | --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of backup repositories names. The cmdlet will return repositories with these names. | String | False | Named | False | True |
| ScaleOut | Defines that the cmdlet will return only scale-out backup repositories.  Note: You must provide this parameter to get scale-out backup repositories.  Default: False. | SwitchParameter | False | Named | False | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CBackupRepository object that contains settings of backup repositories added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Standalone Backup Repositories

|  |  |
| --- | --- |
| This command gets all standalone backup repositories added to the backup infrastructure.  |  | | --- | | Get-VBRBackupRepository | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Scale-Out Backup Repositories

|  |  |
| --- | --- |
| This command gets scale-out backup repositories added to the backup infrastructure.  |  | | --- | | Get-VBRBackupRepository -ScaleOut | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Standalone Backup Repositories by Name

|  |  |
| --- | --- |
| This command gets the Backups Vol12 and Local standalone backup repositories.  |  | | --- | | Get-VBRBackupRepository -Name "Backups Vol2", "Local\*" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Scale-Out Backup Repository by Name

|  |  |
| --- | --- |
| This command gets scale-out backup repository named  Veeam Performance Scale-Out Repository.  |  | | --- | | Get-VBRBackupRepository -ScaleOut -Name "Veeam Performance Scale-Out Repository" | |

Page updated 4/3/2024

Page content applies to build 13.0.1.1071
