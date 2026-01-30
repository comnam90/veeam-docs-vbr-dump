---
title: "Get-VBRCloudSubTenant"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudsubtenant.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCloudSubTenant


Short Description

Returns cloud subtenant accounts.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all cloud subtenant accounts.

|  |
| --- |
| Get-VBRCloudSubTenant [-Mode <VBRCloudSubTenantMode> {Common | AgentManagement}]  [<CommonParameters>] |

* Get cloud subtenants by ID.

|  |
| --- |
| Get-VBRCloudSubTenant [-Id <guid[]>] [-Mode <VBRCloudSubTenantMode> {Common | AgentManagement}]  [<CommonParameters>] |

* Get cloud subtenants by name.

|  |
| --- |
| Get-VBRCloudSubTenant [-Name <string[]>] [-Mode <VBRCloudSubTenantMode> {Common | AgentManagement}]  [<CommonParameters>] |

* Get cloud subtenants by tenant.

|  |
| --- |
| Get-VBRCloudSubTenant [-Tenant <IVBRCloudTenant[]>] [-Mode <VBRCloudSubTenantMode> {Common | AgentManagement}]  [<CommonParameters>] |

Detailed Description

This cmdlet returns cloud subtenant accounts of the following types:

* Simple cloud subtenant accounts.
* Cloud Director subtenant accounts.

|  |
| --- |
| ![Get-VBRCloudSubTenant](images/icon_tip.webp) Tip: |
| You can get the cloud subtenant accounts from the specified cloud tenant. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet to get the cloud tenant. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies the array of subtenant IDs. The cmdlet will return the subtenants with these IDs. | Accepts GUID[] or string[]. | False | Named | True (ByValue, |
| Mode | Specifies the cloud subtenant mode. You can select either of the following modes:   * Common * AgentManagement   The cmdlet will return subusers of the specified mode. | VBRCloudSubTenantMode | False | Named | False |
| Name | Specifies the array of names for the subtenant account you want to get or search conditions. | String[] | False | Named | True (ByValue, ByProperty Name) |
| Tenant | Specifies the tenant. The cmdlet will return the subtenants associated with this tenant. | Accepts the IVBRCloudSubTenant[] and [VBRvCDCloudTenant[]](vbrvcdcloudtenant.md) objects. To get one of the objects, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

IVBRCloudSubTenant

VBRvCDCloudSubTenant

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Cloud Subtenant by Name

|  |  |
| --- | --- |
| This command shows how to get a simple cloud subtenant by name.  |  | | --- | | Get-VBRCloudSubTenant -Name "Alpha" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cloud Subtenant by Tenant

|  |  |
| --- | --- |
| This example shows how to get a cloud subtenant by tenant.  |  | | --- | | $Alpha = Get-VBRCloudTenant -Name "Alpha"  Get-VBRCloudSubTenant -Tenant $Alpha |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $Alpha variable. 2. Run the Get-VBRCloudSubTenant cmdlet. Set the $Alpha variable as the Tenant parameter value. |

Related Commands

[Get-VBRCloudTenant](get-vbrcloudtenant.md)


