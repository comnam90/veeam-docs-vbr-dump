---
title: "VBRCloudDatastoreQuota"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrclouddatastorequota.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRCloudDatastoreQuota

In this article

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

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
