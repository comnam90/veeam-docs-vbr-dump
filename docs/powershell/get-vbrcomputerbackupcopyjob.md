---
title: "Get-VBRComputerBackupCopyJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcomputerbackupcopyjob.html"
last_updated: "1/8/2024"
product_version: "13.0.1.1071"
---

# Get-VBRComputerBackupCopyJob


Short Description

Returns Veeam Agent backup copy jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all Veeam Agent backup copy jobs.

|  |
| --- |
| Get-VBRComputerBackupCopyJob  [<CommonParameters>] |

* Get Veeam Agent backup copy job by its name.

|  |
| --- |
| Get-VBRComputerBackupCopyJob [-Name <string[]>]  [<CommonParameters>] |

* Get Veeam Agent backup copy job by its ID.

|  |
| --- |
| Get-VBRComputerBackupCopyJob [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Veeam Agent backup copy jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names for Veeam Agent backup copy jobs. The cmdlet will return jobs with these names. | String[] | False | Named | False |
| Id | Specifies an array of IDs for Veeam Agent backup copy jobs. The cmdlet will return jobs with these IDs. | Guid[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRComputerBackupCopyJob object that contains settings of Veeam Agent backup copy jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Veeam Agent Backup Copy Jobs

|  |  |
| --- | --- |
| This command returns all Veeam Agent backup copy jobs.  |  | | --- | | Get-VBRComputerBackupCopyJob | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Veeam Agent Backup Copy Job by Name

|  |  |
| --- | --- |
| This command returns the Windows Copy Job05 Veeam Agent backup copy job.  |  | | --- | | Get-VBRComputerBackupCopyJob -Name "Windows Copy Job05" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Veeam Agent Backup Copy Job by ID

|  |  |
| --- | --- |
| This command returns the c4bb4625-7158-43d7-ab63-beaee75d2cff Veeam Agent backup copy job.  |  | | --- | | Get-VBRComputerBackupCopyJob -Id "c4bb4625-7158-43d7-ab63-beaee75d2cff" | |


