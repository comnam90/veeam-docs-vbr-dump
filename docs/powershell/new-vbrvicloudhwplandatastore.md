---
title: "New-VBRViCloudHWPlanDatastore"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrvicloudhwplandatastore.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# New-VBRViCloudHWPlanDatastore

In this article

Short Description

Creates VMware cloud storage for tenants replication resources.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a VCP license.

Syntax

|  |
| --- |
| New-VBRViCloudHWPlanDatastore -Datastore <VBRViDatastore> [-StoragePolicy <VBRViStoragePolicy>] -FriendlyName <String> -Quota <Int32>   [<CommonParameters>] |

Detailed Description

This cmdlet creates a [VBRViCloudHardwarePlanDatastore](vbrvicloudhardwareplandatastore.md) object. This object contains a quota of storage resources on the cloud provider datastores and is used further in hardware plans. In the hardware plan, this quota will be presented as a cloud storage to a tenant. This object is used then in the [Add-VBRViCloudHardwarePlan](add-vbrvicloudhardwareplan.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Datastore | Specifies the cloud provider datastore. This datastore will be used to provide the storage space to a tenant under a hardware plan. | Accepts the VBRViDatastoreBase object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | True | Named | False |
| StoragePolicy | Specifies the VMware storage policy profile. The cmdlet will use datastores with this policy profile.  Note: If you do not specify this parameter, the cmdlet will apply the default VMware storage policy profile. | Accepts the [VBRViStoragePolicy](vbrvistoragepolicy.md) object. To get this object, run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) cmdlet. | False | Named | False |
| FriendlyName | Specifies the name of the storage that will be displayed to the tenant. | String | True | Named | False |
| Quota | Specifies the amount of disk space you want to provide to a tenant under a hardware plan (Gb). | Int32 | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRViCloudHardwarePlanDatastore](vbrvicloudhardwareplandatastore.md)

Examples

Creating Cloud Storage for Selected Datastore

This example shows how to create a cloud storage on Veeam Cloud Datastore with the following parameters:

* Friendly name: Cloud Replicas
* Quota: 500 Gb

|  |
| --- |
| $datastore = Get-VBRServer -Name "ESXiHost" | Find-VBRViDatastore -Name "Veeam Cloud Datastore"  $cloudreplicas = New-VBRViCloudHWPlanDatastore -Datastore $datastore -FriendlyName "Cloud Replicas" -Quota 500 |

Perform the following steps:

1. To get the Veeam Cloud Datastore:

* Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value.
* Pipe the cmdlet output to the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Specify the Name parameter value.
* Save the result to the $datastore variable.

1. Run the New-VBRViCloudHWPlanDatastore cmdlet. Specify the following settings:

* Set the $datastore variable as the Datastore parameter value.
* Specify the FriendlyName parameter value.
* Specify the Quota parameter value.
* Save the result to the $cloudreplicas variable.

Related Commands

* [Find-VBRViDatastore](find-vbrvidatastore.md)
* [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
