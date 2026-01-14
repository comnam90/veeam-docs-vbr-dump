---
title: "Set-VBRUserRoleAssignment"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbruserroleassignment.html"
last_updated: "4/12/2024"
product_version: "13.0.1.1071"
---

# Set-VBRUserRoleAssignment

In this article

Short Description

Modifies a role that is assigned to a user or a user group.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRUserRoleAssignment -Assignment <VBRUserRoleAssignment> [-Role {BackupOperator | RestoreOperator | BackupAdmin | TapeOperator |BackupViewer}]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies a role that is assigned to a user or a user group.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Assignment | Specifies a user or a user group . The cmdlet will modify a role for this user or a user group. | Accepts the VBRUserRoleAssignment object. To create this object, run the [Get-VBRUserRoleAssignment](get-vbruserroleassignment.md) cmdlet. | True | Named | True (ByValue, |
| Role | Specifies a role that you want to assign to a user. The cmdlet will replace the current role with a new role. You can assign one of the following roles:   * BackupOperator * RestoreOperator * BackupAdmin * TapeOperator * BackupViewer | VBRRole | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUserRoleAssignment object that defines a role for a user or a user group.

Examples

Modifying User Role

This example shows how to modify a role that is assigned to the Tech\BackupAdmin user.

|  |
| --- |
| $user = Get-VBRUserRoleAssignment -Name Tech\BackupAdmin  Set-VBRUserRoleAssignment -Assignment $user -Role RestoreOperator            Role Type Name            Id            ---- ---- ----            --  RestoreOperator Group Administrators c5d266c7-8e2b-43f9-92c6-fffc4297074d |

Perform the following steps:

1. Run the [Get-VBRUserRoleAssignment](get-vbruserroleassignment.md) cmdlet. Specify the Name parameter value. Save the result to the $user variable.
2. Run the Set-VBRUserRoleAssignment cmdlet. Set the $user variable as the Assignment parameter value. Set the RestoreOperator value as the Role parameter value.

Related Commands

[Get-VBRUserRoleAssignment](get-vbruserroleassignment.md)

Page updated 4/12/2024

Page content applies to build 13.0.1.1071
