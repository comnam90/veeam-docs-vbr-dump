---
title: "Remove-VBRObjectStorageRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrobjectstoragerepository.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRObjectStorageRepository

In this article

Short Description

Removes object storage added as backup repository to Veeam Backup & Replication.

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
| Remove-VBRObjectStorageRepository -Repository <VBRObjectStorageRepository[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes object storage added as backup repositories to Veeam Backup & Replication. You can remove types the following types of these backup repositories:

* Amazon S3
* S3 compatible
* Azure Blob

You will not be able to connect to object storage after removing them from Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies a backup repository that you want to remove. | Accepts the VBRObjectStorageRepository object. To get this object, run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. | True | Named | True (ByValue) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing All S3 Compatible Object Storage Added as Backup Repositories

This example shows how to remove all S3 compatible object storage added as backup repositories from Veeam Backup & Replication.

|  |
| --- |
| $repository = Get-VBRObjectStorageRepository -Type AmazonS3Compatible  Remove-VBRObjectStorageRepository -Repository $repository |

Perform the following steps:

1. Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. Set the AmazonS3Compatible option for the Type parameter. Save the result to the $repository variable.
2. Run the Remove-VBRObjectStorageRepository cmdlet. Set the $repository variable as the Repository parameter value.

Related Commands

[Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md)

Page updated 5/7/2024

Page content applies to build 13.0.1.1071
