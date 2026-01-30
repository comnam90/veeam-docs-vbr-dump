---
title: "Get-VBRCloudTenant"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudtenant.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCloudTenant


Short Description

Returns cloud tenant accounts.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all cloud tenant accounts.

|  |
| --- |
| Get-VBRCloudTenant  [<CommonParameters>] |

* Get cloud tenant accounts by the tenant account ID.

|  |
| --- |
| Get-VBRCloudTenant [-Id <guid[]>]  [<CommonParameters>] |

* Get cloud tenant accounts by the tenant account name.

|  |
| --- |
| Get-VBRCloudTenant [-Name <string[]>]  [<CommonParameters>] |

* Get cloud tenant accounts by a repository they use.

|  |
| --- |
| Get-VBRCloudTenant [-Repository <CBackupRepository[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns cloud tenant accounts of the following types:

* Simple cloud tenant accounts
* Cloud Director tenant accounts

|  |
| --- |
| Important! |
| The cmdlet gets only information on a number of licensed objects. To get information on backups stored in quota (non-licensed objects), see the [Tenant Machine Count](https://helpcenter.veeam.com/docs/backup/cloud/cloud_connect_machine_count.html?ver=120) section in Veeam Cloud Connect Guide. |

|  |
| --- |
| Note |
| The cmdlet returns information on a number of processed workloads that consume instances from the license scope. Instances are not consumed if a provider obtains a rental license and workloads have been processed for the first time during the current month. These workloads are counted separately and the cmdlet will display them under the following tenant settings:   * NewVMBackupCount * NewWorkstationBackupCount * NewServerBackupCount * NewReplicaCount   Workloads that start to consume instances on the first day of the following month are displayed under the following tenant settings:   * VMCount * WorkstationCount * ServerCount * ReplicaCount   If a tenant obtains a rental license, these workloads do not consume instances from the provider license scope and are displayed under the following tenant settings:   * RentalVMBackupCount * RentalWorkstationBackupCount * RentalServerBackupCount * RentalReplicaCount |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of cloud tenant IDs you want to get. | Accepts GUID or string. | False | Named | True (ByValue, |
| Name | Specifies an array of cloud tenant names. The cmdlet will return details on tenants with specified names. | String | False | Named | True (ByValue, ByProperty Name) |
| Repository | Specifies an array of backup repositories. The cmdlet will return the tenants that use these repositories.  You can specify simple or scale-out backup repositories.  You cannot specify cloud repositories. | Accepts the CBackupRepository[] object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Objects

* IVBRCloudTenant
* [VBRvCDCloudTenant](vbrvcdcloudtenant.md)
* [VBRAdCloudTenant](vbradcloudtenant.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Cloud Tenants

|  |  |
| --- | --- |
| This example shows how to look for all cloud tenants.  |  | | --- | | Get-VBRCloudTenant | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cloud Tenant by Tenant Account Name

|  |  |
| --- | --- |
| This example shows how to look for a cloud tenant by the tenant account name.  |  | | --- | | Get-VBRCloudTenant -Name "ABC Company" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Cloud Tenant by Tenant Account Backup Repository

|  |  |
| --- | --- |
| This example shows how to look for a cloud tenants by the tenant account backup repository.  |  | | --- | | $repository = Get-VBRBackupRepository -Name "Backups Vol2"  Get-VBRCloudTenant -Repository $repository |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the Get-VBRCloudTenant cmdlet. Set the $repository variable as Repository parameter value. |

Related Commands

[Get-VBRBackupRepository](get-vbrbackuprepository.md)


