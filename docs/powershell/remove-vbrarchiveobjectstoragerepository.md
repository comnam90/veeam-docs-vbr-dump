---
title: "Remove-VBRArchiveObjectStorageRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrarchiveobjectstoragerepository.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRArchiveObjectStorageRepository


Short Description

Removes archive repositories added to the backup infrastructure.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRArchiveObjectStorageRepository -Repository <VBRArchiveObjectStorageRepository[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes archive repositories added to the backup infrastructure. You can remove the following types of these backup repositories:

* Amazon S3 Glacier
* Azure Archive

* S3 compatible object storage with data archiving

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies an archive repository that you want to remove. | Accepts the VBRArchiveObjectStorageRepository object. To create this object, run the [Get-VBRArchiveObjectStorageRepository](get-vbrarchiveobjectstoragerepository.md) cmdlet. | True | Named | True (ByValue) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Example

Removing All Archive Repositories from Backup Infrastructure

This example shows how to remove all archive repositories from Veeam Backup & Replication.

|  |
| --- |
| $repository = Get-VBRArchiveObjectStorageRepository  Remove-VBRArchiveObjectStorageRepository -Repository $repository |

Perform the following steps:

1. Run the [Get-VBRArchiveObjectStorageRepository](get-vbrarchiveobjectstoragerepository.md) cmdlet. Save the result to the $repository variable.
2. Run the Remove-VBRArchiveObjectStorageRepository cmdlet. Set the $repository variable as the Repository parameter value.

Related Commands

[Get-VBRArchiveObjectStorageRepository](get-vbrarchiveobjectstoragerepository.md)


