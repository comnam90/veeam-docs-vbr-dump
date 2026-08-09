---
title: "Get-VBRRoleEntity"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrroleentity.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRRoleEntity


Short Description

Returns roles configured in Veeam Backup & Replication.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRRoleEntity [-Name <String[]>] [-BuiltIn] [<CommonParameters>] |

Detailed Description

This cmdlet returns roles configured in Veeam Backup & Replication. You can filter the results by name or return only built-in custom roles.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Name | Specifies an array of roles names. The cmdlet will return custom roles with these names. | String[] | False | Named | True (ByValue, ByProperty Name) |
| BuiltIn | Defines that the cmdlet will return only built-in roles. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRRoleEntity](vbrroleentity.md) object that contains the custom roles settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Built-In Roles

|  |  |
| --- | --- |
| This command returns built-in roles.  |  | | --- | | Get-VBRRoleEntity -BuiltIn | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Assigning Role to User

|  |  |
| --- | --- |
| This example shows how to get a role and assign it to a user.  |  | | --- | | $roleEntity = Get-VBRRoleEntity -Name "BackupOperator"  Add-VBRUserRoleAssignment -Name "Tech\jsmith" -RoleEntity $roleEntity |  Perform the following steps:   1. Run the Get-VBRRoleEntity cmdlet. Specify the Name parameter value. Save the result to the $roleEntity variable. 2. Run the [Add-VBRUserRoleAssignment](add-vbruserroleassignment.md) cmdlet. Specify the Name parameter value. Set the $roleEntity variable as the RoleEntity parameter value. |

Related Commands

[Add-VBRUserRoleAssignment](add-vbruserroleassignment.md)

Page updated 2026-07-03

