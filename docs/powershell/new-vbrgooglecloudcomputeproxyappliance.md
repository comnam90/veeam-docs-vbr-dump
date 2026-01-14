---
title: "New-VBRGoogleCloudComputeProxyAppliance"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrgooglecloudcomputeproxyappliance.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# New-VBRGoogleCloudComputeProxyAppliance

In this article

Short Description

Creates proxy appliances for restoring VMs to Google Cloud.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRGoogleCloudComputeProxyAppliance -InstanceType <VBRGoogleCloudComputeInstanceType> -Subnet <VBRGoogleCloudComputeSubnet> |

Detailed Description

This cmdlet creates proxy appliances for restoring VMs to Google Cloud.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| InstanceType | Specifies a Google Cloud instance type. The cmdlet will create a new proxy appliance with the settings based on this VM instance type. | Accepts the VBRGoogleCloudComputeInstanceType object. To get this object, run the [Get-VBRGoogleCloudComputeInstanceType](get-vbrgooglecloudcomputeinstancetype.md) cmdlet. | True | Named | False |
| Subnet | Specifies a Google Cloud subnet. The cmdlet will create a new proxy appliance that will use the specified subnet. | Accepts the VBRGoogleCloudComputeSubnet object. To get this object, run the [Get-VBRGoogleCloudComputeSubnet](get-vbrgooglecloudcomputesubnet.md) cmdlet. | True | Named | False |
| RedirectorPort | Specifies a port. Veeam Backup & Replication will use this port to route requests between the proxy appliance that the cmdlet will create and backup infrastructure components. | Int | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGoogleCloudComputeProxyAppliance](vbrgooglecloudcomputeproxyappliance.md)

Examples

Creating Google Cloud Proxy Appliance

This example shows how to create a new Google Cloud proxy appliance.

|  |
| --- |
| $computeregion = Get-VBRGoogleCloudComputeRegion -Name "Europe-west1"  $computezone = Get-VBRGoogleCloudComputeZone -Region $computeregion  $instancetype = Get-VBRGoogleCloudComputeInstanceType -Zone $computezone  $account = Get-VBRGoogleCloudComputeAccount -Name "GCP service account 1"  $vpc = Get-VBRGoogleCloudComputeVPC -Account $account  $subnet = Get-VBRGoogleCloudComputeSubnet -Region $computeregion -VPC $vpc  New-VBRGoogleCloudComputeProxyAppliance -InstanceType $instancetype -Subnet $subnet -RedirectorPort "443" |

Perform the following steps:

1. Run the [Get-VBRGoogleCloudComputeRegion](get-vbrgooglecloudcomputeregion.md) cmdlet. Specify the Name parameter value. Save the result to the $computeregion variable.
2. Run the [Get-VBRGoogleCloudComputeZone](get-vbrgooglecloudcomputezone.md) cmdlet. Set the $computeregion variable as the Region parameter. Save the result to the $computezone parameter value.
3. Run the [Get-VBRGoogleCloudComputeInstanceType](get-vbrgooglecloudcomputeinstancetype.md) cmdlet. Set the $computezone variable as the Zone parameter. Save the result to the $instancetype parameter value.
4. Run the [Get-VBRGoogleCloudComputeAccount](get-vbrgooglecloudcomputeaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable.
5. Run the [Get-VBRGoogleCloudComputeVPC](get-vbrgooglecloudcomputevpc.md) cmdlet. Set the $account variable as the Account parameter. Save the result to the $vpc variable.
6. Run the [Get-VBRGoogleCloudComputeSubnet](get-vbrgooglecloudcomputesubnet.md) cmdlet. Set the $computeregion variable as the Region parameter. Set the $vpc variable as the VPC parameter. Save the result to the $subnet parameter value.
7. Run the New-VBRGoogleCloudComputeProxyAppliance cmdlet. Specify the following settings:

* Set the $instancetype variable as the InstanceType parameter.
* Set the $subnet variable as the Subnet parameter.
* Provide the RedirictorPort parameter value.

Related Commands

* [Get-VBRGoogleCloudComputeRegion](get-vbrgooglecloudcomputeregion.md)
* [Get-VBRGoogleCloudComputeZone](get-vbrgooglecloudcomputezone.md)
* [Get-VBRGoogleCloudComputeInstanceType](get-vbrgooglecloudcomputeinstancetype.md)

* [Get-VBRGoogleCloudComputeAccount](get-vbrgooglecloudcomputeaccount.md)
* [Get-VBRGoogleCloudComputeVPC](get-vbrgooglecloudcomputevpc.md)

* [Get-VBRGoogleCloudComputeSubnet](get-vbrgooglecloudcomputesubnet.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
