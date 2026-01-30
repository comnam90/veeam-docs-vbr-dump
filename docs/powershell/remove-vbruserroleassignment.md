---
title: "Remove-VBRUserRoleAssignment"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbruserroleassignment.html"
last_updated: "1/29/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRUserRoleAssignment


Short Description

Removes a role from a user or a user group.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRUserRoleAssignment -Assignment <VBRUserRoleAssignment>  [<CommonParameters>] |

Detailed Description

This cmdlet removes a role from a user or a user group.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Assignment | Specifies a user or a user group from which you want to remove a role. | Accepts the VBRUserRoleAssignment object. To create this object, run the [Get-VBRUserRoleAssignment](get-vbruserroleassignment.md) cmdlet. | True | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Role from User

This example shows how to remove a role that is assigned to the Tech\BackupAdmin user.

|  |
| --- |
| $role = Get-VBRUserRoleAssignment -Name Tech\BackupAdmin  Remove-VBRUserRoleAssignment -Assignment $role |

Perform the following steps:

1. Run the [Get-VBRUserRoleAssignment](get-vbruserroleassignment.md) cmdlet. Specify the Name parameter value. Save the result to the $role variable.
2. Run the Remove-VBRUserRoleAssignment cmdlet. Set the $role variable as the Assignment parameter value.

Related Commands

[Get-VBRUserRoleAssignment](get-vbruserroleassignment.md)


