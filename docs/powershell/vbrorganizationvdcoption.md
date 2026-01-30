---
title: "VBROrganizationvDCOption"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrorganizationvdcoption.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# VBROrganizationvDCOption


Contains replication resources.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Enabled | Boolean | Indicates that replication resources are enabled (TRUE) or disabled (FALSE). |
| OrganizationvDCID | Guid | ID of an organization VDC |
| OrganizationvDCName | String | Name of an organization VDC. |
| WANAccelarationEnabled | Boolean | Indicates that the WAN accelerator is enabled (TRUE) or disabled (FALSE). |
| WANAccelerator | [CWanAccelerator](cwanaccelerator.md) | Target WAN accelerator. |
| AllocationModel | [VBROrganizationvDCAllocationModel](enums.md#VBROrganizationvDCAllocationModel) | Allocation model of the organization VDC. |
| UsedCPU | Int64 | Amount of CPU resources allocated to the tenant. |
| UsedMemory | Int64 | Amount of storage allocated to the tenant. |
| StoragePolicyQuotas | [VBRCloudvCDStoragePolicyQuota](vbrcloudvcdstoragepolicyquota.md)[] | Datastore quota allocated to the tenant. |


