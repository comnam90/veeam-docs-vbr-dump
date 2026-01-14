---
title: "Get-VBRvCDCloudVM"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvcdcloudvm.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRvCDCloudVM

In this article

Short Description

Returns cloud VMs from organization VDCs.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get a cloud VM by the name.

|  |
| --- |
| Get-VBRvCDCloudVM -OrganizationvDC <VBRvCDCloudOrganizationvDC> [-Name <string[]>]  [<CommonParameters>] |

* Get a cloud VM by ID.

|  |
| --- |
| Get-VBRvCDCloudVM -OrganizationvDC <VBRvCDCloudOrganizationvDC> [-Id <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns cloud VMs from organization VDCs. The tenant will use this VM to set up mapping.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| OrganizationvDC | Specifies an organization VDC. The cmdlet will return VMs from the specified organization VDC. | Accepts the VBRvCDCloudOrganizationvDC object. To get this object, run the [Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md) cmdlet. | True | Named | False |
| Name | Specifies an array of names. The cmdlet will return VMs with these names. | String[] | False | Named | False |
| Id | Specifies an array of IDs. The cmdlet will return VMs with these IDs. | Guid[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRvCDCloudVM

Examples

Getting All VMs from Selected Organization VDC

This example shows how to get all VMs from the specific organization VDC.

|  |
| --- |
| $vdc = Get-VBRvCDCloudOrganizationvDC -Name "Cloud Organization 01"  Get-VBRvCDCloudVM -OrganizationvDC $vdc |

Perform the following steps:

1. Run the [Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md) cmdlet. Specify the Name parameter value. Save the result to the $vdc variable.
2. Run the Get-VBRvCDCloudVM cmdlet. Set the $vdc parameter as the OrganizationvDC parameter value.

Related Commands

[Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
