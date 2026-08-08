---
title: "Remove-VBRUserRoleAssignment"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbruserroleassignment.html"
last_updated: "2026"
product_version: "13.1.0.411"
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
| Remove-VBRUserRoleAssignment -Assignment <VBRUserRoleAssignment> [<CommonParameters>] |

Detailed Description

This cmdlet removes a role from a user or a user group.

|  |
| --- |
| Note |
| You cannot remove the role of the last administrator. This is to prevent a situation where no administrator remains. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Assignment | Specifies a role assignment that you want to remove | Accepts the VBRUserRoleAssignment object. To get this object, run the [Get-VBRUserRoleAssignment](get-vbruserroleassignment.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing All Role Assignments from User

|  |  |
| --- | --- |
| This example shows how to remove all roles that are assigned to the User\Administrator user if it has more than one role assigned.  |  | | --- | | Get-VBRUserRoleAssignment -Name "User\Administrator" | Remove-VBRUserRoleAssignment | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Custom Role from User

|  |  |
| --- | --- |
| This example shows how to remove a custom role that is assigned to the User\Administrator user.  |  | | --- | | $role = Get-VBRUserRoleAssignment -Name "User\Administrator" -RoleEntity (Get-VBRRoleEntity -Name "r1")  Remove-VBRUserRoleAssignment -Assignment $role |  Perform the following steps:   1. Run the [Get-VBRUserRoleAssignment](get-vbruserroleassignment.md) cmdlet. Specify the Name and RoleEntity parameter values. Save the result to the $role variable. 2. Run the Remove-VBRUserRoleAssignment cmdlet. Set the $role variable as the Assignment parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Removing Built-In Role from User

|  |  |
| --- | --- |
| This example shows how to remove a built-in role that is assigned to the User\Administrator user.  |  | | --- | | $role = Get-VBRUserRoleAssignment -Name "User\Administrator" -Role BackupOperator  Remove-VBRUserRoleAssignment -Assignment $role |  Perform the following steps:   1. Run the [Get-VBRUserRoleAssignment](get-vbruserroleassignment.md) cmdlet. Specify the Name and Role parameter values. Save the result to the $role variable. 2. Run the Remove-VBRUserRoleAssignment cmdlet. Set the $role variable as the Assignment parameter value. |

Related Commands

[Get-VBRUserRoleAssignment](get-vbruserroleassignment.md)

Page updated 2026-07-03

