---
title: "Remove-VBRExternalRepository"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrexternalrepository.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRExternalRepository

In this article

Short Description

Removes external repositories from the backup infrastructure.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRExternalRepository -ExternalRepository <VBRExternalRepository> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes external repositories from the backup infrastructure. You can remove the following types of external repositories:

* Amazon S3 object storage.
* Microsoft Azure object storage.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| ExternalRepository | Specifies the external repository that you want to remove. | Accepts the VBRExternalRepository object. To get this object, run the [Get-VBRExternalRepository](get-vbrexternalrepository.md) cmdlet. | True | Named | True (ByValue) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing External Repository

This example shows how to remove an external repository named External Repository from the backup infrastructure.

|  |
| --- |
| $repository = Get-VBRExternalRepository -Name "External repository"  Remove-VBRExternalRepository -ExternalRepository $repository |

Perform the following steps:

1. Run the [Get-VBRExternalRepository](get-vbrexternalrepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.
2. Run the Remove-VBRExternalRepository cmdlet. Set the $repository variable as the ExternalRepository parameter value.

Related Commands

[Get-VBRExternalRepository](get-vbrexternalrepository.md)

Page updated 5/7/2024

Page content applies to build 13.0.1.1071
