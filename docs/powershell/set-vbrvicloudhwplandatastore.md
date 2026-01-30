---
title: "Set-VBRViCloudHWPlanDatastore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvicloudhwplandatastore.html"
last_updated: "11/20/2024"
product_version: "13.0.1.1071"
---

# Set-VBRViCloudHWPlanDatastore


Short Description

Modifies VMware cloud storage for tenants replication resources.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a VCP license.

Syntax

|  |
| --- |
| Set-VBRViCloudHWPlanDatastore -CloudDatastore <VBRViCloudHardwarePlanDatastore> [-Datastore <VBRViDatastoreBase>] [-StoragePolicy <VBRViStoragePolicy>] [-FriendlyName <string>] [-Quota <int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the settings of a selected cloud storage in an existing hardware plan.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| CloudDatastore | Specifies the cloud storage you want to modify. | Accepts the [VBRViCloudHardwarePlanDatastore](vbrvicloudhardwareplandatastore.md) object. To get this object, run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet and use the Datastore property. | True | Named | True (ByValue, ByProperty Name) |
| Datastore | Specifies the cloud provider datastore or datastore cluster. This datastore will be used to provide the storage space to a tenant under a hardware plan. | Accepts the VBRViDatastore or [VBRViDatastoreCluster](vbrvidatastorecluster.md) objects. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) or the [Find-VBRViDatastoreCluster](find-vbrvidatastorecluster.md) cmdlets. | False | Named | False |
| StoragePolicy | Specifies the VMware storage policy profile. The cmdlet will use datastores with this policy profile.  Note: If you specify the parameter value as $null, the storage policy profile is reset to the default one. | Accepts the [VBRViStoragePolicy](vbrvistoragepolicy.md) object. To get this object, run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) cmdlet. | False | Named | False |
| FriendlyName | Specifies the name of the storage that will be displayed to the tenant. | String | False | Named | False |
| Quota | Specifies the amount of disk space you want to provide to a tenant under a hardware plan (Gb).  Permitted value: 1 to 2097151 (GB). | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRViCloudHardwarePlanDatastore](vbrvicloudhardwareplandatastore.md)

Examples

Modifying Cloud Storage Settings for Existing Hardware Plan

This example shows how to modify cloud storage settings of an existing hardware plan.

|  |
| --- |
| $plan = Get-VBRCloudHardwarePlan  $d1 = $plan.datastore | Where-Object {$\_.FriendlyName -eq "Cloud Replicas ABC"}  $d2 = $plan.datastore | Where-Object {$\_.FriendlyName -eq "Cloud Replicas North"}  $d1new = Set-VBRViCloudHWPlanDatastore -CloudDatastore $d1 -FriendlyName "Cloud Replicas ABC Extended" -Quota 950  Set-VBRViCloudHardwarePlan -HardwarePlan $plan -Datastore $d1new, $d2 |

Perform the following steps:

1. Run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. Save the result to the $plan variable.
2. Use the Datastore property of the [VBRViCloudHardwarePlan](vbrvicloudhardwareplan.md) object saved to the $plan variable. Pipe the output to the [Where-Object](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/where-object?view=powershell-7.3&viewFallbackFrom=powershell-7.1) cmdlet. Specify the following settings:

* Provide the $\_. automatic variable.
* Provide the FriendlyName property.
* Specify the eq comparison operator value.

Save each cloud storage to a separate variable: $d1, $d2, and so on.

1. Run the Set-VBRViCloudHWPlanDatastore cmdlet. Set the $d1 variable as the CloudDatastore parameter value. Specify the FriendlyName and the Quota parameter values. Save the result to the $d1new variable.
2. Run the [Set-VBRViCloudHardwarePlan](set-vbrvicloudhardwareplan.md) cmdlet. Set the $plan variable as the HardwarePlan parameter value. Set the $d1new and $d2 variables as the Datastore parameter value.

Related Commands

* [Get-VBRCloudDatastore](get-vbrclouddatastore.md)
* [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md)
* [Set-VBRViCloudHardwarePlan](set-vbrvicloudhardwareplan.md)
* [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md)


