---
title: "VBRCloudTenantNetworkAppliance"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcloudtenantnetworkappliance.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# VBRCloudTenantNetworkAppliance


Contains tenant side network appliance.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Host | CHost, CViClusterItem | Host or cluster where the appliance is created. |
| TenantId | GUID | ID of the tenant that uses the appliance. |
| HardwarePlanId | GUID | ID of the hardware plan that uses the appliance. |
| ProductionNetwork | IVBRServerNetworkInfo | Production network to which the appliance is connected. |
| ObtainIpAddressAutomatically | bool | Indicates if the IP address of the appliance is assigned automatically (TRUE) or user-defined (FALSE). |
| IpAddress | string | IP address of the appliance. |
| SubnetMask | string | Subnet mask assigned to the appliance. |
| DefaultGateway | string | Default gateway used by the appliance. |
| Platform | [VBRPlatform](veeam_powershell_types.md#vbrplatform) | Virtualization platform. |

Related Commands

* [Get-VBRCloudTenantNetworkAppliance](get-vbrcloudtenantnetworkappliance.md)
* [Set-VBRCloudTenantNetworkAppliance](set-vbrcloudtenantnetworkappliance.md)

The network appliance is created automatically by the [New-VBRCloudTenantReplicationResources](new-vbrcloudtenantreplicationresources.md) cmdlet when you enable network failover resources.


