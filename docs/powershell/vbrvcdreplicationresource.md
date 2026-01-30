---
title: "VBRvCDReplicationResource"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrvcdreplicationresource.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# VBRvCDReplicationResource


Contains Cloud Director replication resources.

Properties

| Property | Type | Description |
| --- | --- | --- |
| NetworkFailoverResourcesEnabled | Boolean | Indicates if network resources are allocated to the Cloud Director tenant (TRUE) or not (FALSE). |
| TenantNetworkAppliance | [VBRCloudTenantNetworkAppliance](vbrcloudtenantnetworkappliance.md)[] | Tenant network helper appliances. |
| OrganizationvDCOptions | [VBROrganizationvDCOption](vbrorganizationvdcoption.md)[] | Replication resources. |


