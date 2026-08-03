---
title: "Set-VBRUserRoleAssignment"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbruserroleassignment.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Set-VBRUserRoleAssignment


Short Description

Modifies a role that is assigned to a user or a user group.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify a role assignment using a role entity object.

|  |
| --- |
| Set-VBRUserRoleAssignment -Assignment <VBRUserRoleAssignment> [-RoleEntity <VBRRoleEntity>] [<CommonParameters>] |

* Modify a role assignment using a role value.

|  |
| --- |
| Set-VBRUserRoleAssignment -Assignment <VBRUserRoleAssignment> [-Role <VBRRole>] [<CommonParameters>] |

Detailed Description

This cmdlet modifies a role that is assigned to a user or a user group.

|  |
| --- |
| Note |
| Consider the following:   * You cannot change the role of the last administrator. This is to prevent a situation where no administrator remains. * You cannot assign a custom role and a built-in role to the same user or user group. * To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Assignment | Specifies a user or a user group  assignment. The cmdlet will modify a role for this user or a user group. | Accepts the VBRUserRoleAssignment object. To get this object, run the [Get-VBRUserRoleAssignment](get-vbruserroleassignment.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| RoleEntity | Specifies a role. The cmdlet will modify the role defined in the custom roles to the user or user group. | Accepts the [VBRRoleEntity](vbrroleentity.md) object. To get this object, run the [Get-VBRRoleEntity](get-vbrroleentity.md) cmdlet. | False | Named | False |
| Role | Specifies a role that you want to assign to a user. The cmdlet will replace the current role with a new role. You can assign one of the following roles:   * BackupOperator * RestoreOperator * BackupAdmin * TapeOperator * BackupViewer * IncidentApiOperator * SecurityAdministrator * Custom | VBRRole | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUserRoleAssignment object that defines a role for a user or a user group.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Role to a Built-In Role

|  |  |
| --- | --- |
| This example shows how to modify a role that is assigned to the Tech\BackupAdmin user to a custom role.  |  | | --- | | $user = Get-VBRUserRoleAssignment -Name "Tech\BackupAdmin" -RoleEntity (Get-VBRRoleEntity -Name "r1")  Set-VBRUserRoleAssignment -Assignment $user -Role TapeOperator  RoleEntity : Tape Operator  Role : TapeOperator  Type : User  Name : KOS-TEST-0CF\k4  Id : 035c4f9d-9984-4890-8397-c19970e88829 |  Perform the following steps:   1. Run the [Get-VBRUserRoleAssignment](get-vbruserroleassignment.md) cmdlet. Specify the Name and RoleEntity parameter values. Save the result to the $user variable. 2. Run the Set-VBRUserRoleAssignment cmdlet. Set the $user variable as the Assignment parameter value. Set the TapeOperator value as the Role parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Role to a Custom Role

|  |  |
| --- | --- |
| This example shows how to modify a role that is assigned to the Tech\BackupAdmin user to a custom role.  |  | | --- | | $user = Get-VBRUserRoleAssignment -Name "Tech\BackupAdmin" -Role BackupOperator  Set-VBRUserRoleAssignment -Assignment $user -RoleEntity (Get-VBRRoleEntity -Name "r1")  RoleEntity : r1  Role : Custom  Type : User  Name : Tech\BackupAdmin  Id : 2985e2ba-b3e4-4fdf-99f7-b1f6fe7f7818 |  Perform the following steps:   1. Run the [Get-VBRUserRoleAssignment](get-vbruserroleassignment.md) cmdlet. Specify the Name and Role parameter values. Save the result to the $user variable. 2. Run the Set-VBRUserRoleAssignment cmdlet. Set the $user variable as the Assignment parameter value. Set the r1 custom role as the RoleEntity parameter value. |

Related Commands

* [Get-VBRRoleEntity](get-vbrroleentity.md)
* [Get-VBRUserRoleAssignment](get-vbruserroleassignment.md)

Page updated 2026-07-03

