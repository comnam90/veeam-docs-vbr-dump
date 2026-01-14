---
title: "New-VBRCloudSubUserResource"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrcloudsubuserresource.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# New-VBRCloudSubUserResource

In this article

Short Description

Creates quotas of cloud subuser resources.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create a quota with limited disk space.

|  |
| --- |
| New-VBRCloudSubUserResource -CloudRepository <CCloudRepository> -RepositoryFriendlyName <string> -Quota <Int64>  [<CommonParameters>] |

* Create a quota with unlimited disk space.

|  |
| --- |
| New-VBRCloudSubUserResource -CloudRepository <CCloudRepository> -RepositoryFriendlyName <string> -Unlimited  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new [VBRCloudSubUserResource](vbrcloudsubuserresource.md) object. This object contains a quota of the tenant backup resources.

The subtenant quota is a part of subuser account. To assign the quota to a subuser, run the [Add-VBRCloudSubUser](add-vbrcloudsubuser.md) cmdlet and use the created [VBRCloudSubUserResource](vbrcloudsubuserresource.md) object.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudRepository | Specifies the backup resources of the cloud tenant. The disk space available under the cloud user account will be used as parent resources for creating the subuser quota.  Use the Quota or the Unlimited parameter to indicate the amount of disk space you want to give to a subuser. | Accepts the CCloudRepository object, GUID or string. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | True (ByValue, |
| RepositoryFriendlyName | Specifies the name you want to give to the subuser quota.  This name will be displayed in the list of backup repositories at the subuser side. | String | True | Named | True (ByProperty Name) |
| Quota | Specifies the amount of space you want to give to the subuser on the selected backup repository.  Permitted value: 1 to 2097151  (GB). | Int64 | True | Named | True (ByProperty Name) |
| Unlimited | Defines that the quota of resources has unlimited disk space.  With unlimited quota, the subuser will be able to use all parent cloud repository. | SwitchParameter | True | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudSubUserResource](vbrcloudsubuserresource.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Resource Quota for Subuser with Limited Disk Space

|  |  |
| --- | --- |
| This example shows how to create a quota of resources for a subuser with a limited disk space.  |  | | --- | | $cloudrepository = Get-VBRBackupRepository | Where {$\_.Type -eq "Cloud"} | Select -First 1  New-VBRCloudSubUserResource -CloudRepository $cloudrepository -RepositoryFriendlyName "Cloud Repository 1" -Quota 10 |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Pipe the cmdlet output to the Where cmdlet to filter repositories where Type property equals Cloud. Pipe the cmdlet output to the Select cmdlet. Set the 1 number as the First parameter value. Save the result to the $cloudrepository variable. 2. Run the New-VBRCloudSubUserResource cmdlet. Set the $cloudrepository variable as the CloudRepository parameter value. Specify the RepositoryFriendlyName and the Quota parameter values. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Resource Quota for Subuser with Unlimited Disk Space

|  |  |
| --- | --- |
| This example shows how to create a quota of resources for a subuser with unlimited disk space.  |  | | --- | | $cloudrepository = Get-VBRBackupRepository | Where {$\_.Type -eq "Cloud"} | Select -First 1  New-VBRCloudSubUserResource -CloudRepository $cloudrepository -RepositoryFriendlyName "Cloud Repository 1" -Unlimited |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Pipe the cmdlet output to the Where cmdlet to filter repositories where Type property equals Cloud. Pipe the cmdlet output to the Select cmdlet. Set the 1 number as the First parameter value. Save the result to the $cloudrepository variable. 2. Run the New-VBRCloudSubUserResource cmdlet. Set the $cloudrepository variable as the CloudRepository parameter value. Specify the RepositoryFriendlyName parameter value. Provide the Unlimited parameter. |

Related Commands

[Get-VBRBackupRepository](get-vbrbackuprepository.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
