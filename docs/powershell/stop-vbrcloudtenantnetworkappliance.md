---
title: "Stop-VBRCloudTenantNetworkAppliance"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrcloudtenantnetworkappliance.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Stop-VBRCloudTenantNetworkAppliance

In this article

Short Description

Disables network extension appliances on the tenant side.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRCloudTenantNetworkAppliance -Appliance <VBRCloudTenantNetworkAppliance[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet allows the Service Provider to disable network extension appliances configured on the tenant side after a permanent failover.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Appliance | Specifies an array of network extension appliances that you want to disable. | Accepts the [VBRCloudTenantNetworkAppliance](vbrcloudtenantnetworkappliance.md) object. To get this object, run the [Get-VBRCloudTenantNetworkAppliance](get-vbrcloudtenantnetworkappliance.md) cmdlet. | True | Named | True (ByValue) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Disabling Network Extension Appliances of Selected Tenant

This example shows how to disable network extension appliances of the ABC Company tenant.

|  |
| --- |
| $tenant = Get-VBRCloudTenant -Name "ABC Company"  $appliance = Get-VBRCloudTenantNetworkAppliance -Tenant $tenant  Stop-VBRCloudTenantNetworkAppliance -Appliance $appliance |

Perform the following steps:

1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable.
2. Run the [Get-VBRCloudTenantNetworkAppliance](get-vbrcloudtenantnetworkappliance.md) cmdlet. Set the $tenant variable as the Tenant parameter value. Save the result to the $appliance variable.
3. Run the Stop-VBRCloudTenantNetworkAppliance cmdlet. Set the $appliance variable as the Appliance parameter value.

Related Commands

* [Get-VBRCloudTenantNetworkAppliance](get-vbrcloudprovider.md)
* [Get-VBRCloudTenant](get-vbrcloudtenant.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
