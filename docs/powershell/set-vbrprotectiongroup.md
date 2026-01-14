---
title: "Set-VBRProtectionGroup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrprotectiongroup.html"
last_updated: "1/17/2025"
product_version: "13.0.1.1071"
---

# Set-VBRProtectionGroup

In this article

Short Description

Modifies protection groups.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRProtectionGroup -ProtectionGroup <VBRProtectionGroup> [-Name <string>] [-Description <string>] [-Container <VBRProtectionGroupContainer>] [-ScheduleOptions <VBRProtectionGroupScheduleOptions>] [-DeploymentOptions <VBRProtectionGroupDeploymentOptions>] [-AdvancedOptions <VBRProtectionGroupAdvancedWindowsOptions>] [-NotificationOptions <VBRProtectionGroupNotificationOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of a protection group.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| ProtectionGroup | Specifies the protection group you want to modify. | Accepts the [VBRProtectionGroup](vbrprotectiongroup.md) object. To get this object, run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Container | Specifies the protection scope. The protection scope can contain the following objects:   * Active Directory objects. * Individual computers. * Cloud machines. * Computers imported from a CSV file. * Computers with pre-installed backup agents. * MongoDB Replica sets.   The cmdlet will modify the protection group with this protection scope. | Accepts the following objects:   * [VBRADContainer](vbradcontainer.md)  * [VBRIndividualComputerContainer](vbrindividualcomputercontainer.md)  * [VBRAmazonEC2Container](vbramazonec2container.md) * [VBRAzureContainer](vbrazurecontainer.md)  * [VBRCSVContainer](vbrcsvcontainer.md) * [VBRManuallyDeployedContainer](vbrmanuallydeployedcontainer.md) * [VBRMongoDBContainer](vbrmongodbcontainer.md)   To get this object, run one of the following cmdlets:   * [New-VBRADContainer](new-vbradcontainer.md) * [New-VBRIndividualComputerContainer](new-vbrindividualcomputercontainer.md)  * [New-VBRAmazonEC2Container](new-vbramazonec2container.md) * [New-VBRAzureContainer](new-vbrazurecontainer.md)  * [New-VBRCSVContainer](new-vbrcsvcontainer.md)  * [New-VBRManuallyDeployedContainer](new-vbrmanuallydeployedcontainer.md) * [New-VBRMongoDBContainer](new-vbrmongodbcontainer.md) | False | Named | True (ByProperty Name) |
| Name | Specifies the name you want to assign to the protection group. | String | False | Named | True (ByProperty Name) |
| Description | Specifies the description of the protection group. | String | False | Named | True (ByProperty Name) |
| ScheduleOptions | Specifies the discovery schedule. The cmdlet will use this schedule to perform discovery operations for computers in the protection group. | Accepts the [VBRProtectionGroupScheduleOptions](vbrprotectiongroupscheduleoptions.md) object. To get this object, run the [New-VBRProtectionGroupScheduleOptions](new-vbrprotectiongroupscheduleoptions.md) cmdlet. | False | Named | True (ByProperty Name) |
| DeploymentOptions | Specifies Veeam Agent deployment settings. The cmdlet will use these settings to install Veeam Agent on the discovered computers in the protection group. | Accepts the [VBRProtectionGroupDeploymentOptions](vbrprotectiongroupdeploymentoptions.md) object. To get this object, run the [New-VBRProtectionGroupDeploymentOptions](new-vbrprotectiongroupdeploymentoptions.md) cmdlet. | False | Named | True (ByProperty Name) |
| AdvancedOptions | Specifies settings for Veeam Agent for Windows deployed on computers in the protection group. You can specify the following settings:   * Network usage settings * Throttling settings * Security settings | Accepts the [VBRProtectionGroupAdvancedWindowsOptions](vbrprotectiongroupadvancedwindowsoptions.md) object. To get this object, run the [New-VBRProtectionGroupAdvancedWindowsOptions](new-vbrprotectiongroupadvancedwindowsoptions.md) cmdlet. | False | Named | True (ByProperty Name) |
| NotificationOptions | Specifies notification settings for the protection group. | Accepts the [VBRProtectionGroupNotificationOptions](vbrprotectiongroupnotificationoptions.md) object. To get this object, run the [New-VBRProtectionGroupNotificationOptions](new-vbrprotectiongroupnotificationoptions.md) cmdlet. | False | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRProtectionGroup](vbrprotectiongroup.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Computer to Protection Group

|  |  |
| --- | --- |
| This example shows how to add a computer to an existing protection group.  |  | | --- | | $group = Get-VBRProtectionGroup -Name Computers  $comp = $group.Container.CustomCredentials  $supervisor = New-VBRIndividualComputerCustomCredentials -HostName support.east.local -Credentials support\jsmith  $comp += $supervisor  $newcomp = Set-VBRIndividualComputerContainer -Container $group.Container -CustomCredentials $comp  Set-VBRProtectionGroup -ProtectionGroup $group -Container $newcomp |  Perform the following steps:   1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 2. Use the Container.CustomCredentials property of the $group variable. Save the result to the $comp variable. 3. Run the [New-VBRIndividualComputerCustomCredentials](new-vbrindividualcomputercustomcredentials.md) cmdlet. Specify the HostName and the Credentials parameter values. Save the result to the $supervisor variable. 4. Add the computer to the group of computers in the $comp variable. Use the += operator. 5. Run the [Set-VBRIndividualComputerContainer](set-vbrindividualcomputercontainer.md) cmdlet. Set the Container property of the $group variable as the Container parameter value. Set the $comp variable as the CustomCredentials parameter value. Save the result to the $newcomp variable. 6. Run the Set-VBRProtectionGroup cmdlet. Set the $group variable as the ProtectionGroup parameter value. Set the $newcomp variable as the Container parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Exclusions from Protection Group

|  |  |
| --- | --- |
| This example shows how to remove exclusions from a protection group for Microsoft Active Directory Objects.  |  | | --- | | $group = Get-VBRProtectionGroup -Name "AD PG"  $ADcontainer = $group.Container  $newcontaineroptions = @{     Entity = $ADcontainer.Entity     Domain = $ADcontainer.Domain     ExcludeVMs = $ADcontainer.ExcludeVMs     ExcludeOfflineComputers = $ADcontainer.ExcludeOfflineComputers     ExcludeComputers = $False     MasterCredentials = $ADcontainer.MasterCredentials     UseCustomCredentials = $ADcontainer.UseCustomCredentials     CustomCredentials = $ADcontainer.CustomCredentials  }  $newADcontainer = New-VBRADContainer @newcontaineroptions  Set-VBRProtectionGroup -ProtectionGroup $group -Container $newADcontainer |  Perform the following steps:   1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 2. Use the Container property of the $group variable. Save the result to the $ADcontainer variable. 3. Define the scope and settings of AD objects for the new container by creating a hashtable:  * Use the Entity property of the $ADcontainer variable. Save the result as the Entity key value. * Use the Domain property of the $ADcontainer variable. Save the result as the Domain key value. * Use the ExcludeVMs property of the $ADcontainer variable. Save the result as the ExcludeVMs key value. * Use the ExcludeOfflineComputers property of the $ADcontainer variable. Save the result as the ExcludeOfflineComputers key value. * Set $False as the ExcludeComputers property value. * Use the MasterCredentials property of the $ADcontainer variable. Save the result as the MasterCredentials key value. * Use the UseCustomCredentials property of the $ADcontainer variable. Save the result as the UseCustomCredentials key value. * Use the CustomCredentials property of the $ADcontainer variable. Save the result as the CustomCredentials key value.   Save the result to the $newcontaineroptions variable.   1. Run the [New-VBRADContainer](new-vbradcontainer.md) cmdlet. Use the $newcontaineroptions variable with splatting to define the scope and settings of AD objects for the new container. Save the result to the $newADcontainer variable. 2. Run the Set-VBRProtectionGroup cmdlet. Set the $group variable as the ProtectionGroup parameter value. Set the $newADcontainer variable as the Container parameter value. |

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [New-VBRIndividualComputerCustomCredentials](new-vbrindividualcomputercustomcredentials.md)
* [Set-VBRIndividualComputerContainer](set-vbrindividualcomputercontainer.md)

Page updated 1/17/2025

Page content applies to build 13.0.1.1071
