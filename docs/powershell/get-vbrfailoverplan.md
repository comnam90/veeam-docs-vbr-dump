---
title: "Get-VBRFailoverPlan"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrfailoverplan.html"
last_updated: "4/18/2024"
product_version: "13.0.1.1071"
---

# Get-VBRFailoverPlan


Short Description

Returns existing failover plans or cloud failover plans.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Look for failover plans by name.

|  |
| --- |
| Get-VBRFailoverPlan [-Name <string[]>]  [<CommonParameters>] |

* Look for failover plans by type (Local/Tenant/Cloud).

|  |
| --- |
| Get-VBRFailoverPlan -Type <VBRFailoverPlanType> {Local | Tenant | Cloud} [-Name <string[]>]  [<CommonParameters>] |

* [Cloud] Look for failover plans by tenants.

|  |
| --- |
| Get-VBRFailoverPlan -Tenant <VBRCloudTenant> [-Name <string[]>]  [<CommonParameters>] |

* Look for failover plans by ID.

|  |
| --- |
| Get-VBRFailoverPlan [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns existing failover plans or cloud failover plans.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of names of the failover plans you want to get or search conditions. | String[] | False | Named | True (ByValue, |
| Tenant | Specifies the cloud tenant. The cmdlet will return failover plans created by this tenant. | Accepts the [VBRCloudTenant](vbrcloudtenant.md) object. To get this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Type | Specifies the type of the failover plan:   * Local: non-cloud failover plans. * Cloud: [for cloud user] cloud failover plans. * Tenant: [for cloud provider] cloud failover plans created by cloud user.   The cmdlet will return the failover plans of the selected type. | VBRFailoverPlanType | True | Named | False |
| Id | Specifies the array of IDs of the [VBRFailoverPlan](vbrfailoverplan.md) object you want to add to the failover plan. | Accepts GUID or string. | False | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

* [VBRFailoverPlan[]](vbrfailoverplan.md)
* [VBRCloudFailoverPlan[]](vbrcloudfailoverplan.md)
* [VBRTenantFailoverPlan[]](vbrtenantfailoverplan.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Existing Failover Plans

|  |  |
| --- | --- |
| This command looks for the list of all existing failover plans.  |  | | --- | | Get-VBRFailoverPlan | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Failover Plan by Name

|  |  |
| --- | --- |
| This command looks for the MS Exchange Group Failover failover plan.  |  | | --- | | Get-VBRFailoverPlan -Name "MS Exchange Group Failover" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting All Cloud Failover Plans

|  |  |
| --- | --- |
| [Cloud] This command gets all cloud failover plans.  |  | | --- | | Get-VBRFailoverPlan –Type Cloud | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting All Cloud Failover Plans

|  |  |
| --- | --- |
| [Cloud provider] This command gets MS Exchange Group Failover failover plan created by the ABC Company tenant.  |  | | --- | | $tenant = Get-VBRCloudTenant -Name "ABC Company"  Get-VBRFailoverPlan -Tenant $tenant -Name "MS Exchange Group Failover" |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable. 2. Run the Get-VBRFailoverPlan cmdlet. Set the $tenant variable as the Tenant parameter value. Specify the Name parameter value. |


