---
title: "Copy-VBRBackupCopyJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/copy-vbrbackupcopyjob.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Copy-VBRBackupCopyJob


Short Description

Clones a backup copy job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Copy-VBRBackupCopyJob -Job <VBRBackupCopyJob[]> [-Name <string[]>] [-Description <string[]>] [-Repository <CBackupRepository>]  [<CommonParameters>] |

Detailed Description

This cmdlet clones a backup copy job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of backup copy jobs that you want to clone. | Accepts the VBRBackupCopyJob[] object. To create this object, run the [Get-VBRBackupCopyJob](get-vbrbackupcopyjob.md) cmdlet. | True | 0 | True(ByValue, ByPropertyName) |
| Name | Specifies the name you want to assign to the backup copy that you want to clone.  Default: the name of the primary job with the \_clone<clone sequence number> suffix. | String[] | False | Named | False |
| Description | Specifies the description you want to assign to the backup copy job that you want to clone. | String[] | False | Named | False |
| Repository | Specifies the repository to which you want to copy the backup job that you want to clone.  Note: If you do not specify this parameter, the cmdlet will copy the backup job to the same repository, where the original job stores backups. | Accepts the CBackupRepository object. To create this object, run [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRBackupCopyJob object that contains settings of backup copy jobs.

Examples

Cloning Backup Copy Jobs

This example shows how to clone backup copy jobs.

|  |
| --- |
| $copyjobs = Get-VBRBackupCopyJob  Copy-VBRBackupCopyJob -Job $copyjobs |

Perform the following steps:

1. Run the [Get-VBRBackupCopyJob](get-vbrbackupcopyjob.md) cmdlet. Save the result to the $copyjobs variable.
2. Run the Copy-VBRBackupCopyJob cmdlet. Set the $copyjobs variable as the Job parameter value.

Related Commands

[Get-VBRBackupCopyJob](get-vbrbackupcopyjob.md)


