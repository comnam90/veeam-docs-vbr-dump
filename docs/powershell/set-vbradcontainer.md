---
title: "Set-VBRADContainer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbradcontainer.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# Set-VBRADContainer

In this article

Short Description

Modifies a scope of Active Directory objects.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRADContainer -Container <VBRADContainer> [-Domain <VBRADDomain>] [-Entity <VBRADEntity[]>] [-ExcludeVMs] [-ExcludeOfflineComputers] [-ExcludeComputers] [-ExcludedEntity <VBRADEntity[]>] [-MasterCredentials <CCredentials>] [-UseCustomCredentials] [-CustomCredentials <VBRADCustomCredentials[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the [VBRADContainer](vbradcontainer.md) object. This object contains a scope of Active Directory objects you want to add to a protection group.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Container | Specifies the scope of Active Directory objects you want to add to a protection group. | Accepts the [VBRADContainer](vbradcontainer.md) object. To get this object, use the Container parameter of the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Domain | Specifies the Active Directory domain connection object. | Accepts the [VBRADDomain](vbraddomain.md) object. To get this object, run the [Get-VBRADDomain](get-vbraddomain.md) cmdlet. | False | Named | True (ByProperty Name) |
| Entity | Specifies the array of the Active Directory objects from the same domain. The cmdlet will add these objects to the protection scope.  You can add the following types of Active Directory objects:   * Domain * Cluster * Organization unit * Global group * Folder * Computer   Note: You cannot add Domain Local or Universal groups. | Accepts the [VBRADEntity](vbradentity.md)[] object. To get this object, run the [Find-VBRADEntity](find-vbradentity.md) cmdlet. | False | Named | True (ByProperty Name) |
| ExcludeVMs | Defines that the cmdlet will exclude all VMs from the protection scope. | SwitchParameter | False | Named | True (ByProperty Name) |
| ExcludeOfflineComputers | Defines that the cmdlet will exclude computers that have been offline for over 30 days. | SwitchParameter | False | Named | True (ByProperty Name) |
| ExcludeComputers | Defines that you want to exclude some Active Directory objects from the protection scope.  Use the ExcludeEntity parameter to specify objects you want to exclude from the protection scope. | SwitchParameter | False | Named | True (ByProperty Name) |
| ExcludedEntity | Specifies Active Directory objects you want to exclude from the protection scope.  Note: You cannot exclude Domain Local or Universal groups. | Accepts the [VBRADEntity](vbradentity.md)[] object. To get this object, run the [Find-VBRADEntity](find-vbradentity.md) cmdlet. | False | Named | True (ByProperty Name) |
| MasterCredentials | Specifies Master account credentials for authenticating with all Active Directory objects in a protection scope.  For authenticating with Active Directory objects that require different credentials, Veeam Backup & Replication uses custom credentials. If you want to use custom credentials for some Active Directory objects, set the UseCustomCredentials parameter. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | True (ByProperty Name) |
| UseCustomCredentials | Defines that you want to use custom credentials for authenticating with some Active Directory objects.  To specify custom credentials, use the CustomCredentials parameter. | SwitchParameter | False | Named | True (ByProperty Name) |
| CustomCredentials | Specifies custom credentials for authenticating with associated Active Directory objects. | Accepts the [VBRADCustomCredentials](vbradcustomcredentials.md)[] object. To create this object, run the [New-VBRADCustomCredentials](new-vbradcustomcredentials.md) cmdlet. | False | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRADContainer](vbradcontainer.md)

Examples

Excluding VMS from Protection Group

This example shows how to exclude VMs from the existing protection group.

|  |
| --- |
| $group = Get-VBRProtectionGroup -Name "Support PG"  $ad = $group.Container  $newad = Set-VBRADContainer -Container $ad -ExcludeVMs  Set-VBRProtectionGroup -ProtectionGroup $group -Container $newad |

Perform the following steps:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable.
2. Get the scope of Active Directory objects. Use the Container property of the $group variable. Save the result to the $ad variable.
3. Run the Set-VBRADContainer cmdlet. Set the $ad variable as the Container parameter value. Provide the ExcludeVMs parameter. Save the result to the $newad variable.
4. Run the [Set-VBRProtectionGroup](set-vbrprotectiongroup.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Set the $newad variable as the Container parameter value.

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Set-VBRProtectionGroup](set-vbrprotectiongroup.md)

Page updated 3/6/2024

Page content applies to build 13.0.1.1071
