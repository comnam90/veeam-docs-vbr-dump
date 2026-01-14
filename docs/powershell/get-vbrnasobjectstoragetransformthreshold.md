---
title: "Get-VBRNASObjectStorageTransformThreshold"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnasobjectstoragetransformthreshold.html"
last_updated: "10/4/2024"
product_version: "13.0.1.1071"
---

# Get-VBRNASObjectStorageTransformThreshold

In this article

Short Description

Returns the blob transformation threshold defined for an object storage repository that stores file backups.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRNASObjectStorageTransformThreshold -Repository <VBRObjectStorageRepository>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the value of the blob transformation threshold for an object storage repository that stores file backups. As soon as the amount of the outdated data in a separate blob reaches the threshold specified for this object storage repository, such a blob undergoes the transformation operation. The threshold is specified as the percentage of the blob size.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies an object storage. Veeam Backup & Replication will return the blob transformation threshold specified for this object storage repository. | Accepts the VBRObjectStorageRepository object. To get this object, run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRNASObjectStorageTransformThreshold object that contains the value of the blob transformation threshold for an object storage repository that stores file backups.

Examples

Getting Blob Transformation Threshold for Object Storage Repository with File Backups

This example shows how to get the blob transformation threshold defined for the S3 Storage 1 object storage repository.

|  |
| --- |
| $objectstorage = Get-VBRObjectStorageRepository -Name "S3 Storage 1"  Get-VBRNASObjectStorageTransformThreshold -Repository $objectstorage |

Perform the following steps:

1. Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. Specify the Name parameter value. Save the result to the $objectstorage variable.
2. Run the Get-VBRNASObjectStorageTransformThreshold cmdlet. Set the $objectstorage variable as the Repository parameter value.

Related Commands

* [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md)
* [Set-VBRNASObjectStorageTransformThreshold](set-vbrnasobjectstoragetransformthreshold.md)

Page updated 10/4/2024

Page content applies to build 13.0.1.1071
