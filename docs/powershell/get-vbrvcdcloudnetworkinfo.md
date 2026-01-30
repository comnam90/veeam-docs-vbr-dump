---
title: "Get-VBRvCDCloudNetworkInfo"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvcdcloudnetworkinfo.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRvCDCloudNetworkInfo


Short Description

Returns target VDC networks for replica mapping.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get target Cloud Director networks by name.

|  |
| --- |
| Get-VBRvCDCloudNetworkInfo [-Name <string[]>]  [<CommonParameters>] |

* Get target Cloud Director networks by ID.

|  |
| --- |
| Get-VBRvCDCloudNetworkInfo [-Id <guid[]>]  [<CommonParameters>] |

* Get target Cloud Director networks by organization VDC.

|  |
| --- |
| Get-VBRvCDCloudNetworkInfo [-OrganizationvDC <VBRvCDCloudOrganizationvDC>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns target VDC networks for replica mapping.

|  |
| --- |
| ![Get-VBRvCDCloudNetworkInfo](images/icon_important.webp) Important! |
| This cmdlet is available for tenants only. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name of VDC network that you want to get. | String[] | False | Named | True (ByValue, |
| Id | Specifies the IDs of Organizations VDCs that you want to get. | Guid[] | False | Named | True (ByValue, |
| OrganizationvDC | Specifies an organization VDC. The cmdlet will return target VDC networks for the specified organization VDC. | Accepts the VBRvCDCloudOrganizationvDC object. To get this object, run the [Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md) cmdlet. | False | Named | True (ByValue,  ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRvCDCloudNetworkInfo

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Cloud Director Target Networks

|  |  |
| --- | --- |
| This command gets all VDC target networks.  |  | | --- | | Get-VBRvCDCloudNetworkInfo | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cloud Director Target Network for Selected Organization VDC

|  |  |
| --- | --- |
| This example shows how to get a VDC target network for the particular organization VDC.  |  | | --- | | $vdc = Get-VBRvCDCloudOrganizationvDC -Name "vCDorg"  Get-VBRvCDCloudNetworkInfo -OrganizationvDC $vdc |  Perform the following steps:   1. Run the [Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md) cmdlet. Specify the Name parameter value. Save the result to the $vdc variable. 2. Run the Get-VBRvCDCloudNetworkInfo cmdlet. Set the $vdc variable as the OrganizationvDC parameter value. |

Related Commands

[Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md)


