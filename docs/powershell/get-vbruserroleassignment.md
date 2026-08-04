---
title: "Get-VBRUserRoleAssignment"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbruserroleassignment.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRUserRoleAssignment


Prev1/2Next

Short Description

Returns a role that is assigned to a user or a user group.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get role assignments filtered by role entities.

|  |
| --- |
| Get-VBRUserRoleAssignment [-Name <String[]>] [-RoleEntity <VBRRoleEntity[]>] [-Type <VBRRoleType[]>] [<CommonParameters>] |

* Get role assignments filtered by role values.

|  |
| --- |
| Get-VBRUserRoleAssignment [-Name <String[]>] [-Role <VBRRole[]>] [-Type <VBRRoleType[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns a role that is assigned to a user or a user group.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Name | Specifies an array of names of users or user groups. The cmdlet will get roles that are assigned to these users or user groups.  Note: You must specify the name of a user or a user group in the DOMAIN\Username format. | String[] | False | Named | True (ByValue, ByProperty Name) |
| RoleEntity | Specifies a role that you want to get. The cmdlet will return the roles assigned to the user or a user group.. | Accepts the [VBRRoleEntity](vbrroleentity.md) object. To get this object, run the [Get-VBRRoleEntity](get-vbrroleentity.md) cmdlet. | False | Named | False |
| Role | Specifies a role that you want to get. You can get one of the following roles:   * BackupOperator * RestoreOperator * BackupAdmin * TapeOperator * BackupViewer * IncidentApiOperator * SecurityAdministrator * Custom | VBRRole[] | False | Named | False |
| Type | Specifies a type of the user which role you want to get. You can specify one of the following type of a user:   * User * Group | VBRRoleType[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUserRoleAssignment object that defines a role for a user or a user group

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Role of Specific User

|  |
| --- |
| This command returns a role that is assigned to the Tech\BackupAdmin user. The cmdlet output will contain the following details RoleEntity, Role, Type, Name and Id.  | Get-VBRUserRoleAssignment -Name Tech\BackupAdmin  RoleEntity : Backup Administrator  Role : BackupAdmin  Type : Group  Name : Administrators  Id : c5d266c7-8e2b-43f9-92c6-fffc4297074d  |  | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All Users and User Groups with Specific Role

|  |
| --- |
| This command returns all users and user groups that have the Backup Operator role. The cmdlet output will contain the following details RoleEntity, Role, Type, Name and Id.  | Get-VBRUserRoleAssignment -Role BackupOperator  RoleEntity : Backup Operator  Role : BackupOperator  |  | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Role Assigned Through a Custom Role Entity

|  |  |
| --- | --- |
| This command returns the role that is assigned through the Role\_01X custom role entity. The cmdlet output will contain the following details RoleEntity, Role, Type, Name and Id.  |  | | --- | | Get-VBRUserRoleAssignment -RoleEntity (Get-VBRRoleEntity -Name "Role\_01X")  RoleEntity : Role\_01X  Role : Custom  Type : User  Name : Tech\jsmith  Id : 3fa85f64-5717-4562-b3fc-2c963f66afa6 | |

Related Commands

[Get-VBRRoleEntity](get-vbrroleentity.md)

Page updated 2026-07-03

