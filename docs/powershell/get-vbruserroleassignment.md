---
title: "Get-VBRUserRoleAssignment"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbruserroleassignment.html"
last_updated: "1/29/2024"
product_version: "13.0.1.1071"
---

# Get-VBRUserRoleAssignment

In this article

Short Description

Returns a role that is assigned to a user or a user group.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRUserRoleAssignment [-Name <string[]>] [-Role {BackupOperator | RestoreOperator | BackupAdmin | TapeOperator | BackupViewer}] [-Type {User | Group}]  [<CommonParameters>] |

Detailed Description

This cmdlet returns a role that is assigned to a user or a user group.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names of users or user groups. The cmdlet will get roles that are assigned to these users or user groups.  Note: You must specify the name of a user or a user group in the DOMAIN\Username format. | String[] | False | Named | True (ByValue, |
| Role | Specifies a role that you want to get. You can assign one of the following roles:   * BackupOperator * RestoreOperator * BackupAdmin * TapeOperator * BackupViewer | VBRRole[] | False | Named | False |
| Type | Specifies a type of the user which role you want to get. You can specify one of the following type of a user:   * User * Group | VBRRoleType[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUserRoleAssignment object that defines a role for a user or a user group

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Role of Specific User

|  |  |
| --- | --- |
| This command returns a role that is assigned to the Tech\BackupAdmin user. The cmdlet output will contain the following details Role, Type, Name and Id.  |  | | --- | | Get-VBRUserRoleAssignment -Name Tech\BackupAdmin        Role  Type Name           Id        ----  ---- ----           --  BackupAdmin Group Administrators c5d266c7-8e2b-43f9-92c6-fffc4297074d | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All Users and User Groups with Specific Role

|  |  |
| --- | --- |
| This command returns all users and user groups that have the Veeam Restore Operator role. The cmdlet output will contain the following details Role, Type, Name and Id.  |  | | --- | | Get-VBRUserRoleAssignment -Role RestoreOperator        Role  Type Name           Id        ----  ---- ----           --  BackupAdmin Group Administrators c5d266c7-8e2b-43f9-92c6-fffc4297074d | |

Page updated 1/29/2024

Page content applies to build 13.0.1.1071
