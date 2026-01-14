---
title: "New-VBRvCDOrganizationvDCOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrvcdorganizationvdcoptions.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# New-VBRvCDOrganizationvDCOptions

In this article

Short Description

Creates organization vDCs settings.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRvCDOrganizationvDCOptions -OrganizationvDC <CVcdOrganizationVdcItem> [-EnableWanAccelerator] [-WanAccelerator <CWanAccelerator>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a VBRvCDOrganizationvDCOptions object that contains settings for organization vDCs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| OrganizationvDC | Specifies organization VDCs that you want to assign to the tenant. The specified organization VDCs will provide the resources for tenant VM replicas. | Accepts the CVcdOrganizationVdcItem object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet and provide the OrganizationVdc parameter. | True | Named | False |
| EnableWanAccelerator | Enables the WAN accelerator option. | SwitchParameter | False | Named | False |
| WanAccelerator | Specifies the target WAN accelerator that is configured at the SP side. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRvCDOrganizationvDCOptions

Examples

Defining Settings for Organization VDC

This example shows how to define settings for the organization VDC.

|  |
| --- |
| $orgvdc = Find-VBRvCloudEntity -OrganizationVdc -Name "VDC 01"  New-VBRvCDOrganizationvDCOptions -OrganizationvDC $orgvdc |

Perform the following steps:

1. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Provide the OrganizationVdc parameter. Specify the Name parameter value. Save the result to the $orgvdc variable.
2. Run the New-VBRvCDOrganizationvDCOptions cmdlet. Set the $orgvdc variable as the OrganizationvDC parameter value.

Related Commands

[Find-VBRvCloudEntity](find-vbrvcloudentity.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
