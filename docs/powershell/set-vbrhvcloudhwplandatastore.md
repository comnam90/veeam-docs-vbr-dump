---
title: "Set-VBRHvCloudHWPlanDatastore"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrhvcloudhwplandatastore.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRHvCloudHWPlanDatastore

In this article

Short Description

Modifies Hyper-V cloud storage for tenants replication resources.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a VCP license.

Syntax

|  |
| --- |
| Set-VBRHvCloudHWPlanDatastore -CloudDatastore <VBRHvCloudHardwarePlanDatastore> [-DatastorePath <string>] [-FriendlyName <string>] [-Quota <int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the settings of a selected cloud storage in an existing hardware plan.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudDatastore | Specifies the cloud datastore you want to modify. | Accepts the [VBRHvCloudHardwarePlanDatastore](vbrhvcloudhardwareplandatastore.md) object. To get this object, use the datastore property of the object returned by the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. | True | Named | True (ByValue, |
| DatastorePath | Specifies the path to the folder on the cloud provider host that is used in the hardware plan. This folder will be used to provide the storage space to a tenant under a hardware plan. | String | False | Named | False |
| FriendlyName | Specifies the name of the storage that will be displayed to the tenant. | String | False | Named | False |
| Quota | Specifies the amount of disk space you want to provide to a tenant under a hardware plan (Gb). | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Modifying Cloud Storage Settings for Existing Hardware Plan

This example shows how to modify cloud storage settings of an existing hardware plan.

|  |
| --- |
| $plan = Get-VBRCloudHardwarePlan  $d1 = $plan.datastore | Where-Object {$\_.FriendlyName -eq "Cloud Replicas ABC"}  $d2 = $plan.datastore | Where-Object {$\_.FriendlyName -eq "Cloud Replicas North"}  $d1new = Set-VBRHvCloudHWPlanDatastore -CloudDatastore $d1 -FriendlyName "Cloud Replicas ABC Extended" -Quota 950  Set-VBRHvCloudHardwarePlan -HardwarePlan $plan -Datastore $d1new, $d2 |

Perform the following steps:

1. Run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. Save the result to the $plan variable.
2. Use the Datastore property of the [VBRHvCloudHardwarePlan](vbrhvcloudhardwareplan.md) object saved to the $plan variable. Pipe the output to the [Where-Object](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/where-object?view=powershell-7.3&viewFallbackFrom=powershell-7.1) cmdlet. Specify the following settings:

* Provide the $\_. automatic variable.
* Provide the FriendlyName property.
* Specify the eq comparison operator value.

Save each cloud storage to a separate variable: $d1, $d2, and so on.

1. Run the Set-VBRHvCloudHWPlanDatastore cmdlet. Set the $d1 variable as the CloudDatastore parameter value. Specify the FriendlyName and the Quota parameter values. Save the result to the $d1new variable.
2. Run the [Set-VBRHvCloudHardwarePlan](set-vbrhvcloudhardwareplan.md) cmdlet. Set the $plan variable as the HardwarePlan parameter value. Set the $d1new, $d2 variables as the Datastore parameter values.

Related Commands

* [Get-VBRCloudDatastore](get-vbrclouddatastore.md)
* [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md)
* [Set-VBRHvCloudHardwarePlan](set-vbrhvcloudhardwareplan.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
