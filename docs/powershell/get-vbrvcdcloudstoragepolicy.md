---
title: "Get-VBRvCDCloudStoragePolicy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvcdcloudstoragepolicy.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRvCDCloudStoragePolicy


Short Description

Returns Cloud Director storage policies.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get Cloud Director storage policies by name.

|  |
| --- |
| Get-VBRvCDCloudOrganizationvDC [-Name <string[]>]  [<CommonParameters>] |

* Get Cloud Director storage policies by ID.

|  |
| --- |
| Get-VBRvCDCloudOrganizationvDC [-Id <guid[]>]  [<CommonParameters>] |

* Get Cloud Director storage policies for the specified organization VDC.

|  |
| --- |
| Get-VBRvCDCloudOrganizationvDC [-OrganizationvDC <VBRvCDCloudOrganizationvDC>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Cloud Director storage policies. The service provider must configure a storage policy in VMware Cloud Director beforehand.

|  |
| --- |
| ![Get-VBRvCDCloudStoragePolicy](images/icon_important.webp) Important! |
| This cmdlet is available for tenants only. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name of a Cloud Director storage policy that you want to get. | String[] | False | Named | True (ByValue, |
| Id | Specifies an IDs of Organizations VDCs that you want to get. | Guid[] | False | Named | True (ByValue, |
| OrganizationvDC | Specifies an organization VDC. The cmdlet will return storage policies for the specified organization VDC. | Accepts the VBRvCDCloudOrganizationvDC object. To get this object, run the [Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md) cmdlet. | False | Named | True (ByValue,  ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRvCDCloudStoragePolicy

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Cloud Director Cloud Storage Policy

|  |  |
| --- | --- |
| This command gets a Cloud Director cloud storage policy.  |  | | --- | | Get-VBRvCDCloudStoragePolicy -Name "Silver policy" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cloud Director Cloud Storage Policy Assigned to Selected Organization VDC

|  |  |
| --- | --- |
| This example shows how to get the Cloud Director cloud storage policy that is assigned to the specific organization VDC.  |  | | --- | | $vdc = Get-VBRvCDCloudOrganizationvDC -Name "Organization VDC"  Get-VBRvCDCloudStoragePolicy -Name "Silver Policy" -OrganizationvDC $vdc |  Perform the following steps:   1. Run the [Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md) cmdlet. Specify the Name parameter value. Save the result to the $vdc variable. 2. Run the Get-VBRvCDCloudStoragePolicy cmdlet. Specify the Name parameter value. Set the $vdc variable as the OrganizationvDC parameter value. |

Related Commands

[Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md)


