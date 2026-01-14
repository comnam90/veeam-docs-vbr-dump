---
title: "Get-VBRvCDCloudOrganizationvDC"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvcdcloudorganizationvdc.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRvCDCloudOrganizationvDC

In this article

Short Description

Returns organization VDCs.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get organization VDCs by name.

|  |
| --- |
| Get-VBRvCDCloudOrganizationvDC [-Name <string>]  [<CommonParameters>] |

* Get organization VDCs by ID.

|  |
| --- |
| Get-VBRvCDCloudOrganizationvDC [-Id <guid>]  [<CommonParameters>] |

* Get organization VDCs by cloud service provider.

|  |
| --- |
| Get-VBRvCDCloudOrganizationvDC [-CloudProvider <VBRCloudProvider[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns organization VDCs.

|  |
| --- |
| ![Get-VBRvCDCloudOrganizationvDC](images/icon_important.webp) Important! |
| This cmdlet is available for tenants only. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name of organization VDCs that you want to get. | String[] | False | Named | True (ByValue, |
| Id | Specifies an ID of organization VDCs that you want to get. | Guid[] | False | Named | True (ByValue, |
| CloudProvider | Specifies a cloud service provider. Veeam Backup & Replication will return the organization VDCs, managed by this cloud service provider. | Accepts the [VBRCloudProvider[]](vbrcloudprovider.md) object. To get this object, run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. | False | Named | True (ByValue,  ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRvCDCloudOrganizationvDC

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Organization VCDs

|  |  |
| --- | --- |
| This command gets all organization VDCs.  |  | | --- | | Get-VBRvCDCloudOrganizationvDC | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Organization VCD by Name

|  |  |
| --- | --- |
| This command gets an organization VDC by the organization VDC name.  |  | | --- | | Get-VBRvCDCloudOrganizationvDC -Name "Organization VDC" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Organization VCD by Name and Cloud Service Provider

|  |  |
| --- | --- |
| This example shows how to get an organization VDCs by specifying the name and the cloud service provider.  |  | | --- | | $provider = Get-VBRCloudProvider -Name "Organization VDC"  Get-VBRvCDCloudOrganizationvDC -Name "Organization vDC" -CloudProvider $provider |  Perform the following steps:   1. Run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. Specify the Name parameter value. Save the result to the $provider variable. 2. Run the Get-VBRvCDCloudOrganizationvDC cmdlet. Specify the Name parameter value. Set the $provider variable as the CloudProvider parameter value. |

Related Commands

[Get-VBRCloudProvider](get-vbrcloudprovider.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
