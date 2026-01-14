---
title: "Unmount-VBRObjectStorageRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/unmount-vbrobjectstoragerepository.html"
last_updated: "2/29/2024"
product_version: "13.0.1.1071"
---

# Unmount-VBRObjectStorageRepository

In this article

Short Description

Unmounts object storage and archive repositories.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Unmount object storage repositories.

|  |
| --- |
| Unmount-VBRObjectStorageRepository -Repository <VBRObjectStorageRepository> [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Unmount an archive repository.

|  |
| --- |
| Unmount-VBRObjectStorageRepository -ArchiveRepository <VBRArchiveObjectStorageRepository> [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet unmounts object storage and archive repositories.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies an object storage repository. The cmdlet will unmount this repository. | Accepts the VBRObjectStorageRepository object. To get this object, run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. | True | Named | True (ByValue) |
| ArchiveRepository | Specifies an archive repository. The cmdlet will mount this archive repository. | Accepts the VBRArchiveObjectStorageRepository object. To get this object, run the [Get-VBRArchiveObjectStorageRepository](get-vbrarchiveobjectstoragerepository.md) cmdlet. | True | Named | True (ByValue) |
| Force | Defines that the cmdlet will unmount an object storage repository and will not show up any warnings or notifications. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if the user is sure that he wants to continue. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Unmounting Object Storage Repository

This example shows how to unmount the Amazon OS object storage repository. The cmdlet will skip all notifications and warnings.

|  |
| --- |
| $repository = Get-VBRObjectStorageRepository -Name "Amazon OS"  Unmount-VBRObjectStorageRepository -Repository $repository -Force |

Perform the following steps:

1. Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.
2. Run the Unmount-VBRObjectStorageRepository cmdlet. Set the $repository variable as the Repository parameter value. Provide the Force parameter.

Related Commands

[Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md)

Page updated 2/29/2024

Page content applies to build 13.0.1.1071
