---
title: "Add-VBRProtectionGroup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrprotectiongroup.html"
last_updated: "8/16/2024"
product_version: "13.0.1.1071"
---

# Add-VBRProtectionGroup

In this article

Short Description

Creates protection groups in Veeam Backup & Replication.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRProtectionGroup -Name <string> -Container <VBRProtectionGroupContainer>[-Description <string>] [-ScheduleOptions <VBRProtectionGroupScheduleOptions>] [-DeploymentOptions <VBRProtectionGroupDeploymentOptions>] [-AdvancedOptions <VBRProtectionGroupAdvancedWindowsOptions>] [-NotificationOptions <VBRProtectionGroupNotificationOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates protection groups.

Before creating a protection group, you must create a protection scope for this group. Protection groups can include the following objects:

* Active Directory objects.
* Individual computers.
* Cloud machines.
* Computers imported from a CSV file.
* Computers with pre-installed backup agents.
* MongoDB Replica sets.

For more information about the protection scope, see the following cmdlets:

* [New-VBRADContainer](new-vbradcontainer.md)
* [New-VBRIndividualComputerContainer](new-vbrindividualcomputercontainer.md)
* [New-VBRAmazonEC2Container](new-vbramazonec2container.md)
* [New-VBRAzureContainer](new-vbrazurecontainer.md)
* [New-VBRCSVContainer](new-vbrcsvcontainer.md)
* [New-VBRManuallyDeployedContainer](new-vbrmanuallydeployedcontainer.md)
* [New-VBRMongoDBContainer](new-vbrmongodbcontainer.md)

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Container | Specifies the protection scope. The protection scope can contain the following objects:   * Active Directory objects. * Individual computers. * Cloud machines. * Computers imported from a CSV file. * Computers with pre-installed backup agents. * MongoDB Replica sets.   The cmdlet will create the protection group with this protection scope. | Accepts the following objects:   * [VBRADContainer](vbradcontainer.md)  * [VBRIndividualComputerContainer](vbrindividualcomputercontainer.md)  * [VBRAmazonEC2Container](vbramazonec2container.md) * [VBRAzureContainer](vbrazurecontainer.md)  * [VBRCSVContainer](vbrcsvcontainer.md) * [VBRManuallyDeployedContainer](vbrmanuallydeployedcontainer.md) * [VBRMongoDBContainer](vbrmongodbcontainer.md)   To get this objects, run one of the following cmdlets:   * [New-VBRADContainer](new-vbradcontainer.md) * [New-VBRIndividualComputerContainer](new-vbrindividualcomputercontainer.md)  * [New-VBRAmazonEC2Container](new-vbramazonec2container.md) * [New-VBRAzureContainer](new-vbrazurecontainer.md)  * [New-VBRCSVContainer](new-vbrcsvcontainer.md)  * [New-VBRManuallyDeployedContainer](new-vbrmanuallydeployedcontainer.md) * [New-VBRMongoDBContainer](new-vbrmongodbcontainer.md) | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the name you want to assign to the protection group. | String | True | Named | True (ByProperty Name) |
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

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Protection Group for Individual Computers

|  |  |
| --- | --- |
| This example shows how to create a protection group with the following settings:   * The created protection group will include individual computers. * Veeam Backup & Replication will discover computers in the protection group every 12 hours. * Veeam Backup & Replication will automatically install Veeam Agent on all discovered computers of this protection group.   |  | | --- | | $computers = @("support.east.local", "qa.east.local", "adm-v8931") | ForEach { New-VBRIndividualComputerCustomCredentials -HostName $\_ -Credentials "support\jsmith"}  $scope = New-VBRIndividualComputerContainer -CustomCredentials $computers  $periodically = New-VBRPeriodicallyOptions -FullPeriod 12 -PeriodicallyKind Hours  $schedule = New-VBRProtectionGroupScheduleOptions -PolicyType Periodically -PeriodicallyOptions $periodically  $deployment = New-VBRProtectionGroupDeploymentOptions -InstallAgent  Add-VBRProtectionGroup -Name "Support\_East" -Container $scope -ScheduleOptions $schedule -DeploymentOptions $deployment |  Perform the following steps:   1. Run the [New-VBRIndividualComputerCustomCredentials](new-vbrindividualcomputercustomcredentials.md) cmdlet. Use the ForEach statement to apply the same credentials to multiple computers. Save the result to the $computers variable. 2. Run the [New-VBRIndividualComputerContainer](new-vbrindividualcomputercontainer.md) cmdlet. Set the $computers variable as the CustomCredentials parameter value. Save the result to the $scope variable. 3. Run the [New-VBRPeriodicallyOptions](new-vbrperiodicallyoptions.md) cmdlet. Specify the FullPeriod and the PeriodicallyKind parameter values. Save the result to the $periodically variable. 4. Run the [New-VBRProtectionGroupScheduleOptions](new-vbrprotectiongroupscheduleoptions.md) cmdlet. Set the Periodically value as the PolicyType parameter value. Set the $periodically variable as the PeriodicallyOptions parameter value. Save the result to the $schedule variable. 5. Run the [New-VBRProtectionGroupDeploymentOptions](new-vbrprotectiongroupdeploymentoptions.md) cmdlet. Provide the InstallAgent parameter. Save the result to the $deployment variable. 6. Run the Add-VBRProtectionGroup cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $scope variable as the Container parameter value. * Set the $schedule variable as the ScheduleOptions parameter value. * Set the $deployment variable as the DeploymentOptions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Protection Group for Pre-Installed Veeam Agents

|  |  |
| --- | --- |
| This example shows how to create a protection group that will include Linux and Unix computers with pre-installed Veeam Agents.  |  | | --- | | $linuxdistr = Get-VBRProtectionGroupLinuxPackage -LinuxDistributionName "debian", "ubuntu" -LinuxPackageBitness X64  $unixdistr = Get-VBRProtectionGroupUnixPackage -Name "Solaris Intel"  $preinstalledcontainer = New-VBRManuallyDeployedContainer -Path \\srv001\VeeamBackups -LinuxPackage $linuxdistr -UnixPackage $unixdistr  Add-VBRProtectionGroup -Name PreinstalledPG -Container $preinstalledcontainer |  Perform the following steps:   1. Run the Get-VBRProtectionGroupLinuxPackage cmdlet. Specify the LinuxDistributionName and LinuxPackageBitness parameter values. Save the result to the $linuxdistr variable. 2. Run the Get-VBRProtectionGroupUnixPackage cmdlet. Specify the Name parameter value. Save the result to the $unixdistr variable. 3. Run the New-VBRManuallyDeployedContainer cmdlet. Specify the Path parameter value. Set the $linuxdistr variable as the LinuxPackage parameter value. Set the $unixdistr variable as the UnixPackage parameter value. Save the result to the $preinstalledcontainer variable. 4. Run the Add-VBRProtectionGroup cmdlet. Specify the Name parameter value. Set the $preinstalledcontainer variable as the Container parameter value. |

Related Commands

* [New-VBRIndividualComputerCustomCredentials](new-vbrindividualcomputercustomcredentials.md)
* [New-VBRIndividualComputerContainer](new-vbrindividualcomputercontainer.md)
* [New-VBRPeriodicallyOptions](new-vbrperiodicallyoptions.md)
* [New-VBRProtectionGroupScheduleOptions](new-vbrprotectiongroupscheduleoptions.md)
* [New-VBRProtectionGroupDeploymentOptions](new-vbrprotectiongroupdeploymentoptions.md)

Page updated 8/16/2024

Page content applies to build 13.0.1.1071
