---
title: "New-VBRCloudTenantReplicationResources"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrcloudtenantreplicationresources.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# New-VBRCloudTenantReplicationResources

In this article

Short Description

Creates the [VBRCloudTenantReplicationResources](vbrcloudtenantreplicationresources.md) objects that contain replication resources.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRCloudTenantReplicationResources [-EnableNetworkFailoverResources] [-HardwarePlanOptions <VBRCloudTenantHwPlanOptions[]>] [-EnablePublicIp] [-NumberOfPublicIp <Int32>] [-EnablePublicIpV6] [-NumberOfPublicIpV6 <Int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new [VBRCloudTenantReplicationResources](vbrcloudtenantreplicationresources.md) object. This object contains the cloud tenant replication resources.

To provide network access to cloud replicas, you need to configure a network extension appliance. You have the following options:

* Default network extension appliance. If you enable the the failover resources in this cmdlet, the network extension appliance will be created automatically. The network appliance will have default settings.
* Customize the default network appliance. After the network appliance is created automatically, you can change its settings. For details, see the [Set-VBRCloudTenantNetworkAppliance](set-vbrcloudtenantnetworkappliance.md) cmdlet.
* Do not configure a network appliance. The tenant may deploy the network extension appliances manually on their side.

To allocate a number of public IP addresses, you need to pre-configure the public IP addresses pool. For details, see the [Add-VBRCloudPublicIP](add-vbrcloudpublicip.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| HardwarePlanOptions | Specifies the hardware plan options. | Accepts the [VBRCloudTenantHwPlanOptions[]](vbrcloudtenanthwplanoptions.md) object. To get this object, run the [New-VBRCloudTenantHwPlanOptions](new-vbrcloudtenanthwplanoptions.md) cmdlet. | False | Named | True (ByValue, |
| EnableNetworkFailoverResources | Enables the tenant to use the built-in failover networking management capabilities.  The cmdlet will create a network extension appliance with default settings. | SwitchParameter | False | Named | False |
| EnablePublicIp | Enables the tenant to use a range of public IP addresses.  Use the NumberOfPublicIp parameter to set the maximum number of IPs.  Default: 0. | SwitchParameter | False | Named | False |
| NumberOfPublicIp | Specifies the maximum number of public IPs for the tenant.  Permitted values: from 1 to 9999. | Int32 | False | Named | False |
| EnablePublicIpV6 | Enables the tenant to use a range of public IPv6 addresses.  Use the NumberOfPublicIpV6 parameter to set the maximum number of IPs.  Default: 0. | Int32 | False | Named | False |
| NumberOfPublicIpV6 | Specifies the maximum number of public IPv6 addresses for the tenant.  Permitted values: from 1 to 9999. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudTenantReplicationResources](vbrcloudtenantreplicationresources.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Replication Resources with Enabled Failover Capabilities

|  |  |
| --- | --- |
| This example shows how to create an object containing replication resources with enabled failover capabilities.  |  | | --- | | $HwPlan = Get-VBRCloudHardwarePlan -Name "VMware Silver"  $options = New-VBRCloudTenantHwPlanOptions -HardwarePlan $HwPlan  $resources = New-VBRCloudTenantReplicationResources -EnableNetworkFailoverResources -HardwarePlanOptions $options |  Perform the following steps:   1. Run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. Specify the Name parameter value. Save it to the $HwPlan variable. 2. Run the [New-VBRCloudTenantHwPlanOptions](new-vbrcloudtenanthwplanoptions.md). Set the $HwPlan variable as the HardwarePlan parameter value. Save the result to the $options variable. 3. Run the New-VBRCloudTenantReplicationResources cmdlet. Provide the EnableNetworkFailoverResources parameter. Set the $options variable as the HardwarePlanOptions parameter value. Save the result to the $resources variable for further use. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Replication Resources with Enabled Failover Capabilities and Allocated IP Addresses

|  |  |
| --- | --- |
| This example shows how to create an object containing replication resources with enabled failover capabilities and allocate 5 public IP addresses.  |  | | --- | | Add-VBRCloudPublicIP -FirstIpAddress 198.51.100.1 -LastIpAddress 198.51.100.15  $HwPlan = Get-VBRCloudHardwarePlan -Name "VMware Silver"  $options = New-VBRCloudTenantHwPlanOptions -HardwarePlan $HwPlan  $resources = New-VBRCloudTenantReplicationResources -EnableNetworkFailoverResources -HardwarePlanOptions $options -EnablePublicIp -NumberOfPublicIp 5 |  Perform the following steps:   1. Run the [Add-VBRCloudPublicIP](add-vbrcloudpublicip.md) cmdlet. Specify the FirstIpAddress and the LastIpAddress parameter values. 2. Run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. Specify the Name parameter value. Save it to the $HwPlan variable. 3. Run the [New-VBRCloudTenantHwPlanOptions](new-vbrcloudtenanthwplanoptions.md) cmdlet. Set the $HwPlan variable as the HardwarePlan parameter value. Save the result to the $options variable. 4. Run the New-VBRCloudTenantReplicationResources cmdlet. Specify the following settings:  * Provide the EnableNetworkFailoverResources parameter. * Set the $options variable as the HardwarePlanOptions parameter value. * Provide the EnablePublicIp parameter. * Specify the NumberOfPublicIp parameter value. * Save the result to the $resources variable for further use. |

Related Commands

[New-VBRCloudTenantHwPlanOptions](new-vbrcloudtenanthwplanoptions.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
