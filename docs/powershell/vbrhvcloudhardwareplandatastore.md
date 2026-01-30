---
title: "VBRHvCloudHardwarePlanDatastore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrhvcloudhardwareplandatastore.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRHvCloudHardwarePlanDatastore


Contains datastore used by Hyper-V hardware plan.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Datastore ID. |
| Datastore | string | Datastore file path. |
| FriendlyName | string | Name of storage resources exposed to the user. |
| Quota | int | Storage resources quota assigned to the user. |
| Platform | [VBRPlatform](veeam_powershell_types.md#vbrplatform) | Virtualization platform. |

Related Commands

* [New-VBRHvCloudHWPlanDatastore](new-vbrhvcloudhwplandatastore.md)
* [New-VBRViCloudHWPlanDatastore](new-vbrvicloudhwplandatastore.md)


