---
title: "Remove-VBRCloudSubUser"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrcloudsubuser.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRCloudSubUser

In this article

Short Description

Removes cloud subuser accounts.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRCloudSubUser -SubUser <IVBRCloudSubUser[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a selected cloud subuser account from Veeam Backup & Replication. You can remove the subuser accounts of the following types:

* Simple cloud tenant accounts
* Cloud Director tenant accounts

When you remove a subuser, all backups stored on the cloud repository on this subuser are removed permanently. The parent cloud user cannot undo this operation. The resources associated with this subuser account becomes available for use by the cloud user.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SubUser | Specifies the array of cloud subusers you want to remove. The subusers can have different parents. | Accepts the IVBRCloudSubUser[] object. To get this object, run the [Get-VBRCloudSubUser](get-vbrcloudsubuser.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Cloud Subuser

This example shows how to remove a cloud subuser.

|  |
| --- |
| $subuser = Get-VBRCloudSubUser -Name "Subuser 1"  Remove-VBRCloudSubUser -SubUser $subuser |

Perform the following steps:

1. Run the [Get-VBRCloudSubUser](get-vbrcloudsubuser.md) cmdlet. Specify the Name parameter value. Save the result to the $subuser variable.
2. Run the Remove-VBRCloudSubUser cmdlet. Set the $subuser variable as the SubUser parameter value.

Related Commands

[Get-VBRCloudSubUser](get-vbrcloudsubuser.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
