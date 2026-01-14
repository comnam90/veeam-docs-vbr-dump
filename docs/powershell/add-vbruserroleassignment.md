---
title: "Add-VBRUserRoleAssignment"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbruserroleassignment.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Add-VBRUserRoleAssignment

In this article

Short Description

Adds a role to a user or a user group.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRUserRoleAssignment -Name <string> -Role {BackupOperator | RestoreOperator | BackupAdmin | TapeOperator | BackupViewer}  [<CommonParameters>] |

Detailed Description

This cmdlet adds a role to a user or a user group. For more information on types of roles, see the [Roles and Users](https://helpcenter.veeam.com/docs/vbr/userguide/users_roles.html?ver=13) section of User Guide for VMware vSphere.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name of a user or a user group. The cmdlet will assign a role for this user or user group.  Note: You must specify the name of a user or a user group in the DOMAIN\Username format. | String | True | Named | True (ByValue, |
| Role | Specifies a role that you want to assign to a user. You can assign one of the following roles:   * BackupOperator * RestoreOperator * BackupAdmin * TapeOperator * BackupViewer | VBRRole[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUserRoleAssignment object that defines a role for a user or a user group

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Assigning Veeam Backup Operator Role to User

|  |  |
| --- | --- |
| This command assigns a Veeam Backup Operator role to the Tech\BackupAdmin user. The cmdlet output will contain the following details Role, Type, Name and Id.  |  | | --- | | Add-VBRUserRoleAssignment -Name Tech\BackupAdmin -Role "BackupOperator"        Role  Type Name           Id        ----  ---- ----           --  BackupAdmin Group Administrators c5d266c7-8e2b-43f9-92c6-fffc4297074d | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Assigning Veeam Tape Operator Role to User

|  |  |
| --- | --- |
| This command assigns a Veeam Tape Operator role to the Tech\TapeAdmin user. The cmdlet output will contain the following details Role, Type, Name and Id.  |  | | --- | | Add-VBRUserRoleAssignment -Name Tech\TapeAdmin -Role TapeOperator        Role  Type Name           Id        ----  ---- ----           --  BackupAdmin Group Administrators c5d266c7-8e2b-43f9-92c6-fffc4297074d | |

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
