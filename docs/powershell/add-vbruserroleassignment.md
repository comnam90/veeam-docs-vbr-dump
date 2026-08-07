---
title: "Add-VBRUserRoleAssignment"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbruserroleassignment.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Add-VBRUserRoleAssignment


Prev1/6Next

Short Description

Adds a role to a user or a user group.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Assign a role to a user or user group using a role entity object.

|  |
| --- |
| Add-VBRUserRoleAssignment -Name <String> -RoleEntity <VBRRoleEntity> [<CommonParameters>] |

* Assign a role to a user or user group using a role value.

|  |
| --- |
| Add-VBRUserRoleAssignment -Name <String> -Role <VBRRole> [<CommonParameters>] |

Detailed Description

This cmdlet adds a role to a user or a user group. For more information on types of roles, see the [Roles and Users](https://helpcenter.veeam.com/docs/vbr/userguide/users_roles.html?ver=13) section of User Guide for VMware vSphere.

|  |
| --- |
| Note |
| You cannot assign a custom role and a built-in role to the same user or user group. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Name | Specifies a name of a user or a user group. The cmdlet will assign a role for this user or user group.  Note: You must specify the name of a user or a user group in the DOMAIN\Username format. | String | True | Named | True (ByValue, ByProperty Name) |
| RoleEntity | Specifies roles. The cmdlet will assign these roles to the user or user group. | Accepts the [VBRRoleEntity](vbrroleentity.md) object. To get this object, run the [Get-VBRRoleEntity](get-vbrroleentity.md) cmdlet. | True | Named | False |
| Role | Specifies a role that you want to assign to a user. You can assign one of the following roles:   * BackupOperator * RestoreOperator * BackupAdmin * TapeOperator * BackupViewer * IncidentApiOperator * SecurityAdministrator * Custom | VBRRole | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUserRoleAssignment object that defines a role for a user or a user group

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Assigning Backup Operator Role to User

|  |  |
| --- | --- |
| This command assigns the Backup Operator role to the Tech\BackupAdmin user. The cmdlet output will contain the following details: RoleEntity, Role, Type, Name and Id.  |  | | --- | | Add-VBRUserRoleAssignment -Name Tech\BackupAdmin -Role "BackupOperator"  RoleEntity : Backup Operator  Role : BackupOperator  Type : User  Name : Tech\BackupAdmin  Id : efd17c66-104a-4ef8-8b76-365ece476cef | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Assigning Tape Operator Role to User

|  |  |
| --- | --- |
| This command assigns the Tape Operator role to the Tech\TapeAdmin user. The cmdlet output will contain the following details: RoleEntity, Role, Type, Name and Id.  |  | | --- | | Add-VBRUserRoleAssignment -Name Tech\TapeAdmin -Role TapeOperator  RoleEntity : Tape Operator  Role : TapeOperator  Type : User  Name : Tech\TapeAdmin  Id : b2c6a3d4-8f91-4e5a-9c3b-1a7d5e8f2b60 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Assigning Custom Role to User

|  |  |
| --- | --- |
| This command assigns the r1 custom role to the k4 user. The cmdlet output will contain the following details: RoleEntity, Role, Type, Name and Id.  |  | | --- | | Add-VBRUserRoleAssignment -Name "k4" -RoleEntity (Get-VBRRoleEntity -Name "r1")  RoleEntity : r1  Role : Custom  Type : User  Name : Tech\BackupAdmin  Id : a1a5898b-5377-4c04-89e6-70abf0d5395b | |

Related Commands

* [Get-VBRRoleEntity](get-vbrroleentity.md)

Page updated 2026-07-14

