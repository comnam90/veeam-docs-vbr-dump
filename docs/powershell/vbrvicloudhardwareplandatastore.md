---
title: "VBRViCloudHardwarePlanDatastore"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrvicloudhardwareplandatastore.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRViCloudHardwarePlanDatastore

In this article

Contains datastore used by VMware hardware plan.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Datastore ID. |
| Datastore | string | Datastore file path. |
| StoragePolicy | [VBRViStoragePolicy](vbrvistoragepolicy.md) | VMware storage policy profile applied to the datastore. |
| FriendlyName | string | Name of the storage resources exposed to the user. |
| Quota | int | Storage resources quota assigned to the user. |
| Platform | [VBRPlatform](veeam_powershell_types.md#vbrplatform) | Virtualization platform: VMware. |

Related Commands

[New-VBRViCloudHWPlanDatastore](new-vbrvicloudhwplandatastore.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
