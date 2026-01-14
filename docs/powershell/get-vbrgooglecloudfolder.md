---
title: "Get-VBRGoogleCloudFolder"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrgooglecloudfolder.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Get-VBRGoogleCloudFolder

In this article

Short Description

Returns Google Cloud folders.

Applies to

Platform: VMware, Hyper-V

Syntax

|  |
| --- |
| Get-VBRGoogleCloudFolder -Connection <VBRGoogleCloudConnection> -Bucket <VBRGoogleCloudBucket[]> [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of Google Cloud folders.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Connection | Specifies an active session with Google Cloud object storage. The cmdlet will return an array of the folders added to this object storage. | Accepts the VBRGoogleCloudConnection object. To get this object, run the [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Bucket | Specifies an array of Google Cloud buckets. The cmdlet will return an array of the folders added to these buckets. | Accepts the VBRGoogleCloudBucket[] object. To get this object, run the [Get-VBRGoogleCloudBucket](get-vbrgooglecloudbucket.md) cmdlet. | True | Named | False |
| Name | Specifies an array of names for the Google Cloud folders. Veeam Backup & Replication will return the folders with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRGoogleCloudFolder object that contains an array of Google Cloud folders.

Examples

Getting Google Cloud Folders

This example shows how to get folders added to Google Cloud object storage.

|  |
| --- |
| $account = Get-VBRGoogleCloudAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c"  $connection = Connect-VBRGoogleCloudService -Account $account -ServiceType CapacityTier  $bucket = Get-VBRGoogleCloudBucket -Connection $connection -Region $region  Get-VBRGoogleCloudFolder -Connection $connection -Bucket $bucket |

Perform the following steps:

1. Run the [Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable.
2. Run the [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md) cmdlet. Specify the Account and ServiceType parameter values. Save the result to the $connection variable.
3. Run the [Get-VBRGoogleCloudBucket](get-vbrgooglecloudbucket.md) cmdlet. Specify the Connection and Region parameter values. Save the result to the $bucket variable.
4. Run the Get-VBRGoogleCloudFolder cmdlet. Set the $connection variable as the Connection parameter value. Set the $bucket variable as the Bucket parameter value.

Related Commands

* [Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md)
* [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md)
* [Get-VBRGoogleCloudBucket](get-vbrgooglecloudbucket.md)

Page updated 6/17/2024

Page content applies to build 13.0.1.1071
