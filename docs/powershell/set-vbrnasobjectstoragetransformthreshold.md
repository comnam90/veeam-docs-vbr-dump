---
title: "Set-VBRNASObjectStorageTransformThreshold"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrnasobjectstoragetransformthreshold.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Set-VBRNASObjectStorageTransformThreshold

In this article

Short Description

Modifies the blob transformation threshold for an object storage repository that stores file backups.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify the blob transformation threshold for the object storage repository that stores file backups by setting the threshold to the default value.

|  |
| --- |
| Set-VBRNASObjectStorageTransformThreshold -Repository <VBRObjectStorageRepository> -Default  [<CommonParameters>] |

* Modify the blob transformation threshold for the object storage repository that stores file backups by setting the threshold to a custom value.

|  |
| --- |
| Set-VBRNASObjectStorageTransformThreshold -Repository <VBRObjectStorageRepository> -Threshold <Int32>  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the blob transformation threshold for an object storage repository that stores file backups. As soon as the amount of the outdated data in a separate blob reaches the threshold specified for this object storage repository, such a blob undergoes the transformation operation. The threshold is specified as the percentage of the blob size.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies an object storage. Veeam Backup & Replication will modify the blob transformation threshold for this object storage repository. | Accepts the VBRObjectStorageRepository object. To get this object, run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. | True | Named | True (ByValue) |
| Default | Defines that the cmdlet will set the blob transformation threshold for the object storage repository to its default value. | SwitchParameter | True | Named | False |
| Threshold | Specifies the threshold value that the cmdlet will set as the blob transformation threshold for the object storage repository. | Int32 | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRNASObjectStorageTransformThreshold object that contains the value of the blob transformation threshold for an object storage repository that stores file backups.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Setting Blob Transformation Threshold for Object Storage Repository to Default Value

|  |  |
| --- | --- |
| This example shows how to set the blob transformation threshold for the object storage repository to its default value.  |  | | --- | | $objectstorage = Get-VBRObjectStorageRepository -Name "S3 Storage 1"  Set-VBRNASObjectStorageTransformThreshold -Repository $objectstorage -Default |  Perform the following steps:   1. Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. Specify the Name parameter value. Save the result to the $objectstorage variable. 2. Run the Set-VBRNASObjectStorageTransformThreshold cmdlet. Set the $objectstorage variable as the Repository parameter value. Provide the Default parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Setting Blob Transformation Threshold for Object Storage Repository to Custom Value

|  |  |
| --- | --- |
| This example shows how to set the blob transformation threshold for the object storage repository to a custom value.  |  | | --- | | $objectstorage = Get-VBRObjectStorageRepository -Name "S3 Storage 1"  Set-VBRNASObjectStorageTransformThreshold -Repository $objectstorage -Threshold "50" |  Perform the following steps:   1. Run the [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md) cmdlet. Specify the Name parameter value. Save the result to the $objectstorage variable. 2. Run the Set-VBRNASObjectStorageTransformThreshold cmdlet. Set the $objectstorage variable as the Repository parameter value. Specify the Threshold parameter value. |

Related Commands

* [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md)
* [Get-VBRNASObjectStorageTransformThreshold](get-vbrnasobjectstoragetransformthreshold.md)

Page updated 1/6/2025

Page content applies to build 13.0.1.1071
