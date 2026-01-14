---
title: "Add-VBRCloudSubUser"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrcloudsubuser.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRCloudSubUser

In this article

Short Description

Creates cloud subuser accounts.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRCloudSubUser -CloudProvider <VBRCloudProvider> -Name <string> -Password <string> -Resources <VBRCloudSubUserResource[]> [-Description <string>] [-Disabled]  [<CommonParameters>] |

Detailed Description

This cmdlet creates new cloud subuser accounts.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudProvider | Specifies the cloud provider. The resources of this provider will be parent for the subuser. | Accepts the [VBRCloudProvider](vbrcloudprovider.md) object. To get this object, run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies the name you want to assign to the subuser account.  The subuser name must meet the following requirements:   * The maximum length of the subuser name is 128 characters. It is recommended that you create short subuser names to avoid problems with long paths to backup files on the cloud repository. * The subuser name may contain space characters. * The subuser name must not contain the following characters: \/:\*?\"<>|=; as well as Unicode characters. * The subuser name must not end with the period character [.]. | String | True | Named | False |
| Password | Specifies the password you want to set to the subuser account. | String | True | Named | False |
| Resources | Specifies the quota of the subuser backup resources you want to give to the subuser. | Accepts the [VBRCloudSubUserResource[]](vbrcloudsubuserresource.md) object. To create this object, run the [New-VBRCloudSubUserResource](new-vbrcloudsubuserresource.md) cmdlet. | True | Named | False |
| Description | Specifies the description of the cloud subuser account. | String | False | Named | False |
| Disabled | Defines that the cloud subuser is disabled. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudSubUser](vbrcloudsubuser.md)

Examples

Creating Cloud Subuser Account

This example shows how to create a cloud subuser account.

|  |
| --- |
| $cloudrepository = Get-VBRBackupRepository | Where {$\_.Type -eq "Cloud"} | Select -First 1  $subuserquota = New-VBRCloudSubUserResource -CloudRepository $cloudrepository -RepositoryFriendlyName "Cloud Repository 1" -Quota 10  $cloudprovider = Get-VBRCloudProvider  Add-VBRCloudSubUser -CloudProvider $cloudprovider -Name "Subuser 1" -Password "Pass 123" -Resources $subuserquota |

Perform the following steps:

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Pipe the cmdlet output to the Where cmdlet to filter repositories where Type property equals Cloud. Pipe the cmdlet output to the Select cmdlet. Set the 1 number as the First parameter value. Save the result to the $cloudrepository variable.
2. Run the [New-VBRCloudSubUserResource](new-vbrcloudsubuserresource.md) cmdlet. Set the $cloudrepository variable as the CloudRepository parameter value. Specify the RepositoryFriendlyName and the Quota parameter values. Save the result to the $subuserquota variable.
3. Run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. Save the result to the $cloudprovider variable.
4. Run the Add-VBRCloudSubUser cmdlet. Specify the following settings:

* Set the $cloudprovider variable as the CloudProvider parameter value.
* Specify the Name parameter value.
* Specify the Password parameter value.
* Set the $subuserquota variable as the Resources parameter value.

Related Commands

* [Get-VBRCloudProvider](get-vbrcloudprovider.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBRCloudSubUserResource](new-vbrcloudsubuserresource.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
