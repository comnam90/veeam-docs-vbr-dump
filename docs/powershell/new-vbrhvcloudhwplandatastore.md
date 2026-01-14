---
title: "New-VBRHvCloudHWPlanDatastore"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrhvcloudhwplandatastore.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# New-VBRHvCloudHWPlanDatastore

In this article

Short Description

Creates Hyper-V cloud storage for tenants replication resources.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a VCP license.

Syntax

|  |
| --- |
| New-VBRHvCloudHWPlanDatastore -DatastorePath <String> -FriendlyName <String> -Quota <Int32>  [<CommonParameters>] |

Detailed Description

This cmdlet creates a [VBRHvCloudHardwarePlanDatastore](vbrhvcloudhardwareplandatastore.md) object. This object contains a quota of storage resources on the cloud provider disks and is used further in hardware plans. In the hardware plan, this quota will be presented as a cloud storage to a tenant. This object is used then in the [Add-VBRHvCloudHardwarePlan](add-vbrhvcloudhardwareplan.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| DatastorePath | Specifies the path to the folder on the cloud provider host that is used in the hardware plan. This folder will be used to provide the storage space to a tenant under a hardware plan. | String | True | Named | False |
| FriendlyName | Specifies the name of the storage that will be displayed to the tenant. | String | True | Named | False |
| Quota | Specifies the amount of disk space you want to provide to a tenant under a hardware plan (Gb). | Int32 | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRHvCloudHardwarePlanDatastore](vbrhvcloudhardwareplandatastore.md)

Examples

Creating Cloud Storage on Selected Datastore

This example shows how to create a cloud storage on the "Veeam Cloud Datastore" with the following parameters:

* Friendly name: Cloud Replicas.
* Quota: 500 Gb.
* The storage is saved to the $cloudreplicas variable.

|  |
| --- |
| $cloudreplicas = New-VBRHvCloudHWPlanDatastore -DatastorePath "D:\Replicas" -FriendlyName "Cloud Replicas" -Quota 500 |

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
