---
title: "Remove-VBRProtectionGroup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrprotectiongroup.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRProtectionGroup


Short Description

Removes protection groups.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRProtectionGroup -ProtectionGroup <VBRProtectionGroup[]> [-UninstallEverything] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes selected protection groups from the Veeam Backup & Replication database. When you remove a protection group, Veeam Backup & Replication removes Veeam Agent and Veeam Plug-In from all computers of this group. You cannot undo this operation. Backups created for protected computers remain in backup repositories.

|  |
| --- |
| Note |
| Consider the following:   * You cannot remove a protection group if the entire protection group or a separate computer included in this protection group is added to a Veeam Agent backup job. * You cannot remove default protection groups, such as Manually Added, Unmanaged, and so on. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| ProtectionGroup | Specifies an array of protection groups. The cmdlet will remove these protection groups from Veeam Backup & Replication. | Accepts the [VBRProtectionGroup[]](vbrprotectiongroup.md) object. To get this object, run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| UninstallEverything | Defines that the cmdlet will remove an array of protection groups from the configuration database. Additionally, the cmdlet will uninstall the following entities from every computer in the deleted protection group:   * Veeam Agent * Veeam Installer Service * Veeam Plug-In | SwitchParameter | False | Named | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Protection Group

|  |  |
| --- | --- |
| This example shows how to remove a protection group from Veeam Backup & Replication.  |  | | --- | | $group = Get-VBRProtectionGroup -Name "Support\_East"  Remove-VBRProtectionGroup -ProtectionGroup $groups |  Perform the following steps:   1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 2. Run the Remove-VBRProtectionGroup cmdlet. Set the $group variable as the ProtectionGroup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing All Protection Groups by Name

|  |  |
| --- | --- |
| This example shows how to remove all protection groups with names containing Support.  |  | | --- | | $groups = Get-VBRProtectionGroup -Name \*Support\*  Remove-VBRProtectionGroup -ProtectionGroup $groups |  Perform the following steps:   1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $groups variable. 2. Run the Remove-VBRProtectionGroup cmdlet. Set the $groups variable as the ProtectionGroup parameter value. |

Related Commands

[Get-VBRProtectionGroup](get-vbrprotectiongroup.md)


