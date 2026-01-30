---
title: "Get-VBRCloudTenantNetworkAppliance"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudtenantnetworkappliance.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCloudTenantNetworkAppliance


Short Description

Returns network extension appliances.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a VCP license.

Syntax

This cmdlet provides parameter sets that allow you to:

* Getting all tenant network appliances or for network appliances by name.

|  |
| --- |
| Get-VBRCloudTenantNetworkAppliance [-Name <string[]>]  [<CommonParameters>] |

* Getting network appliances by name or by tenant.

|  |
| --- |
| Get-VBRCloudTenantNetworkAppliance [-Name <string[]>] [-Tenant <VBRCloudTenant[]>]  [<CommonParameters>] |

* Getting network appliances by name or by hosts.

|  |
| --- |
| Get-VBRCloudTenantNetworkAppliance [-Name <string[]>] [-Server <Object[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns network extension appliances. You can get the network extension appliance for the cloud tenants of the following types:

* Simple cloud tenant accounts
* Cloud Director tenant accounts

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of names of the appliance. The cmdlet will return appliances with these names. | String[] | False | Named | False |
| Tenant | Specifies the array of tenants. The cmdlet will return appliances assigned to these tenants. | Accepts the [VBRCloudTenant[]](vbrcloudtenant.md) object. To get this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | False | Named | True (ByValue, |
| Server | Specifies the array of hosts. The cmdlet will return appliances that use these hosts. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudTenantNetworkAppliance[]](vbrcloudtenantnetworkappliance.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Network Appliances

|  |  |
| --- | --- |
| This command returns all tenant network appliances.  |  | | --- | | Get-VBRCloudTenantNetworkAppliance | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Network Appliances for Selected Tenant

|  |  |
| --- | --- |
| This example shows how to return network appliances of a selected tenant.  |  | | --- | | $tenant = Get-VBRCloudTenant -Name "ABC Company"  Get-VBRCloudTenantNetworkAppliance -Tenant $tenant |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save it to the $tenant variable. 2. Run the Get-VBRCloudTenantNetworkAppliance cmdlet. Set the $tenant variable as the Tenant parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Network Appliances for Selected Host

|  |  |
| --- | --- |
| This example shows how to return network appliances deployed on a selected host.  |  | | --- | | $server = Get-VBRServer –Name "srv01.tech.local"  Get-VBRCloudTenantNetworkAppliance -Server $server |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the host to the $server variable. 2. Run the Get-VBRCloudTenantNetworkAppliance cmdlet. Set the $server variable as the Server parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRCloudTenant](get-vbrcloudtenant.md)


