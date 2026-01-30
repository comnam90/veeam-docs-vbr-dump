---
title: "Get-VBRvCDCloudvApp"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvcdcloudvapp.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRvCDCloudvApp


Short Description

Returns VDC vApps.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRvCDCloudvApp -OrganizationvDC <VBRvCDCloudOrganizationvDC> [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns vApps that are added to Organization DCs.

|  |
| --- |
| ![Get-VBRvCDCloudvApp](images/icon_important.webp) Important! |
| This cmdlet is available for tenants only. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| OrganizationvDC | Specifies an organization VDC. The cmdlet will return vApps for the specified organization VDC. | Accepts the VBRvCDCloudOrganizationvDC object. To get this object, run the [Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies the name of the cloud App that you want to get. | String[] | False | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRvCDCloudvApp

Examples

Getting vApp Container

This example shows how to get a vApp container.

|  |
| --- |
| $vdc = Get-VBRvCDCloudOrganizationvDC -Name "Organization VDC"  $vApp = Get-VBRvCDCloudvApp -OrganizationvDC $vdc |

Perform the following steps:

1. Run the [Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md) cmdlet. Specify the Name parameter value. Save the result to the $vdc variable.
2. Run the Get-VBRvCDCloudvApp cmdlet. Set the $vdc variable as OrganizationvDC parameter value.

Related Commands

[Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md)


