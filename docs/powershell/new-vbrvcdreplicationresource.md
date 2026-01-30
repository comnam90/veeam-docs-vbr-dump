---
title: "New-VBRvCDReplicationResource"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrvcdreplicationresource.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# New-VBRvCDReplicationResource


Short Description

Defines Cloud Director replication resource settings.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRvCDReplicationResource -OrganizationvDCOptions <VBROrganizationvDCOption[]> [-EnableNetworkFailoverResources]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRvCDReplicationResource](vbrvcdreplicationresource.md) object that contains settings for the replication resources.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| OrganizationvDCOptions | Specifies organization VDCs that you want to assign to the tenant. The specified organization VDCs will provide the resources for tenant VM replicas. | Accepts the VBRvCDOrganizationvDCOptions[] object. To get this object, run the [New-VBRvCDOrganizationvDCOptions](new-vbrvcdorganizationvdcoptions.md) cmdlet. | True | Named | True (ByValue, |
| EnableNetworkFailoverResources | Enables the tenant to use the network resources to perform failover task.  The cmdlet will create a network extension appliance with default settings. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRvCDReplicationResource](vbrvcdreplicationresource.md)

Examples

Defining Cloud Director Replication Resource Settings

This example shows how to set the Organization 05 organization VDC to provide the resources for tenant VM replicas.

|  |
| --- |
| $orgvdc = Find-VBRvCloudEntity -OrganizationVdc -Name "Organization 05"  $dcoptions = New-VBRvCDOrganizationvDCOptions -OrganizationvDC $orgvdc  New-VBRvCDReplicationResource -OrganizationvDCOptions $dcoptions |

Perform the following steps:

1. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Provide the OrganizationVdc parameter. Specify the Name parameter value. Save the result to the $orgvdc variable.
2. Run the [New-VBRvCDOrganizationvDCOptions](new-vbrvcdorganizationvdcoptions.md) cmdlet. Set the $orgvdc variable as the OrganizationvDC parameter value. Save the result to the $dcoptions variable.
3. Run the New-VBRvCDReplicationResource cmdlet. Set the $dcoptions variable as the OrganizationvDCOptions parameter value.

Related Commands

* [Find-VBRvCloudEntity](find-vbrvcloudentity.md)
* [New-VBRvCDOrganizationvDCOptions](new-vbrvcdorganizationvdcoptions.md)


