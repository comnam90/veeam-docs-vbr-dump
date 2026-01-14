---
title: "Copy-VBRComputerBackupCopyJob (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/copy-vbrcomputerbackupcopyjob.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Copy-VBRComputerBackupCopyJob (obsolete)

In this article

Short Description

Clones Veeam Agent backup copy jobs.

|  |
| --- |
| Note |
| This cmdlet is obsolete and only works for cloning a simple mode backup copy job. It is recommended to clone a new backup job using the [Copy-VBRBackupCopyJob](copy-vbrbackupcopyjob.md) cmdlet. |

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Copy-VBRComputerBackupCopyJob -Job <VBRComputerBackupCopyJob[]> [-Name <String[]>] [-Description <String[]>] [-Repository <CBackupRepository>]  [<CommonParameters>] |

Detailed Description

This cmdlet clones Veeam Agent backup copy jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of Veeam Agent backup copy jobs that you want to clone. | Accepts the VBRComputerBackupCopyJob[] object. To create this object, run the [Get-VBRComputerBackupCopyJob](get-vbrcomputerbackupcopyjob.md) cmdlet. | True | 0 | True(ByValue, ByPropertyName) |
| Name | Specifies the name you want to assign to the Veeam Agent backup copy that you want to clone.  Default: the name of the primary job with the \_clone<clone sequence number> suffix. | String[] | False | Named | False |
| Description | Specifies the description you want to assign to the Veeam Agent backup copy job that you want to clone. | String[] | False | Named | False |
| Repository | Specifies the repository to which you want to copy to the Veeam Agent backup job that you want to clone.  Note: If you do not specify this parameter, the cmdlet will copy Veeam Agent backup jobs to the same repository, where the original job stores backups. | Accepts the CBackupRepository object. To create this object, run [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRComputerBackupCopyJob object that contains cloned Veeam Agent backup copy jobs.

Examples

Cloninig Veeam Agent Backup Copy Jobs

This example shows how to clone Veeam Agent backup copy jobs.

|  |
| --- |
| $copyjobs = Get-VBRComputerBackupCopyJob  Copy-VBRComputerBackupCopyJob -Job $copyjobs |

Perform the following steps:

1. Get the [Get-VBRComputerBackupCopyJob](get-vbrcomputerbackupcopyjob.md) cmdlet. Save the result to the $copyjobs variables.
2. Run the Copy-VBRComputerBackupCopyJob cmdlet. Set the $copyjobs variable as the Job parameter value.

Related Commands

[Get-VBRComputerBackupCopyJob](get-vbrcomputerbackupcopyjob.md)

Page updated 3/11/2024

Page content applies to build 13.0.1.1071
