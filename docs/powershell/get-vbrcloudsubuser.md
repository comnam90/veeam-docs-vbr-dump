---
title: "Get-VBRCloudSubUser"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudsubuser.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCloudSubUser

In this article

Short Description

Returns cloud subuser accounts.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all cloud subusers.

|  |
| --- |
| Get-VBRCloudSubUser [-Mode <VBRCloudSubUserMode> {Common | AgentManagement}]  [<CommonParameters>] |

* Get cloud subusers by the subuser ID.

|  |
| --- |
| Get-VBRCloudSubUser [-Id <guid[]>] [-Mode <VBRCloudSubUserMode> {Common | AgentManagement}]  [<CommonParameters>] |

* Get cloud subusers by the subuser name.

|  |
| --- |
| Get-VBRCloudSubUser [-Name <string[]>] [-Mode <VBRCloudSubUserMode> {Common | AgentManagement}]  [<CommonParameters>] |

* Get cloud subusers by a cloud service provider.

|  |
| --- |
| Get-VBRCloudSubUser [-CloudProvider <VBRCloudProvider[]>] [-Mode <VBRCloudSubUserMode> {Common | AgentManagement}]  [<CommonParameters>] |

Detailed Description

This cmdlet returns cloud subuser accounts of the following types:

* Simple cloud subtenant accounts
* Cloud Director subtenant accounts

You can get the list of all existing subuser accounts, or narrow down the search results to name, ID or cloud provider. Use an appropriate parameter set for each case.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of subuser ID. The cmdlet will return subusers with these IDs. | Guid[] | False | Named | True (ByValue, |
| Name | Specifies an array of names for subuser accounts. The cmdlet will return subusers with names. | String[] | False | Named | True (ByValue, ByProperty Name) |
| Mode | Specifies the cloud subtenant mode. You can select either of the following modes:   * Common * AgentManagement   The cmdlet will return subusers of the specified mode. | VBRCloudSubUserMode | False | Named | False |
| CloudProvider | Specifies a cloud provider. The cmdlet will return subusers associated with this cloud provider. | Accepts the [VBRCloudProvider[]](vbrcloudprovider.md) object. To get this object, run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

IVBRCloudSubUser

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Cloud Subusers

|  |  |
| --- | --- |
| This command returns all cloud subusers.  |  | | --- | | Get-VBRCloudSubUser | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cloud Subuser by Name

|  |  |
| --- | --- |
| This command looks for a subuser by the subuser name.  |  | | --- | | Get-VBRCloudSubUser -Name "Subuser 1" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Cloud Subuser by Cloud Service Provider

|  |  |
| --- | --- |
| This example shows how to get a subuser by a cloud service provider.  |  | | --- | | $cloudProvider = Get-VBRCloudProvider  Get-VBRCloudSubUser -CloudProvider $cloudprovider |  Perform the following steps:   1. Run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. Save the result to the $cloudprovider variable. 2. Run the Get-VBRCloudSubUser cmdlet. Set the $cloudprovider variable as the CloudProvider parameter value. |

Related Commands

[Get-VBRCloudProvider](get-vbrcloudprovider.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
