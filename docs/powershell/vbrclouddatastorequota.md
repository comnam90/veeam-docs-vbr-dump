---
title: "VBRCloudDatastoreQuota"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrclouddatastorequota.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRCloudDatastoreQuota


Contains information about space used by a tenant.

Extends [VBRCloudTenantHwPlanOptions](vbrcloudtenanthwplanoptions.md).

Properties

| Property | Type | Description |
| --- | --- | --- |
| DatastoreId | GUID | ID of the datastore under a hardware plan. |
| FriendlyName | string | Datastore name. |
| Quota | int | Tenant quota (Gb). |
| UsedSpace | int64 | Used space (Gb). |
| CPUQuota | int | CPU quota. |
| MemoryQuota | int | Memory quota. |


