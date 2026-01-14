---
title: "New-VBRUniversalCDPvCDCloudDestination"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbruniversalcdpvcdclouddestination.html"
last_updated: "11/13/2025"
product_version: "13.0.1.1071"
---

# New-VBRUniversalCDPvCDCloudDestination

In this article

Short Description

Defines the target location settings for VDC universal CDP policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRUniversalCDPvCDCloudDestination -OrganizationvDC <VBRvCDCloudOrganizationvDC> [-StoragePolicy <VBRvCDCloudStoragePolicy>] [-vApp <VBRvCDCloudvApp>] [-Force] [-HighPriority]  [<CommonParameters>] |

Detailed Description

This cmdlet defines the VBRUniversalCDPvCDCloudDestination object. This object contains the target location settings for VDC universal CDP policies.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| OrganizationvDC | Specifies the organization VDC. The cmdlet will replicate workloads to this organization VDC. | Accepts the VBRvCDCloudOrganizationvDC object. To get this object, run the [Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md) cmdlet. | True | Named | False |
| StoragePolicy | Specifies the VMware Cloud Director storage policy for replication. | Accepts the VBRvCDCloudStoragePolicy object. To get this object, run the [Get-VBRvCDCloudStoragePolicy](get-vbrvcdcloudstoragepolicy.md) cmdlet. | False | Named | False |
| vApp | Specifies the target vApp. The cmdlet will replicate workloads to this vApp. | Accepts the VBRvCDCloudvApp object. To get this object, run the [Get-VBRvCDCloudvApp](get-vbrvcdcloudvapp.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will perform a failover without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUniversalCDPvCDCloudDestination object that defines the target location settings for VDC universal CDP policies.

Examples

Creating Target Location Settings for VDC Universal CDP Policy

This example shows how to create target location settings for the VDC universal CDP policy.

|  |
| --- |
| $vdc = Get-VBRvCDCloudOrganizationvDC -Name "Organization VDC"  $storage\_policy = Get-VBRvCDCloudStoragePolicy -Name "Silver Policy" -OrganizationvDC $vdc  $destination = New-VBRUniversalCDPvCDCloudDestination -OrganizationvDC $vdc -StoragePolicy $storage\_policy |

Perform the following steps:

1. Run the [Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md) cmdlet. Specify the Name parameter value. Save the result to the $vdc variable.
2. Run the [Get-VBRvCDCloudStoragePolicy](get-vbrvcdcloudstoragepolicy.md) cmdlet. Specify the Name parameter value. Set the $vdc variable as the OrganizationvDC parameter value. Save the result to the $storage\_policy variable.
3. Run the New-VBRUniversalCDPvCDCloudDestination cmdlet. Specify the following settings:

* Set the $vdc variable as the OrganizationvDC parameter value.
* Set the $storage\_policy variable as the StoragePolicy parameter value.
* Save the result to the $destination variable.

Related Commands

* [Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md)
* [Get-VBRvCDCloudStoragePolicy](get-vbrvcdcloudstoragepolicy.md)

Page updated 11/13/2025

Page content applies to build 13.0.1.1071
