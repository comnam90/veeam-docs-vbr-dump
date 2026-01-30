---
title: "Get-VBRGoogleCloudBucket"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrgooglecloudbucket.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Get-VBRGoogleCloudBucket


Short Description

Returns Google Cloud buckets.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRGoogleCloudBucket -Connection <VBRGoogleCloudConnection> -Region <VBRGoogleCloudRegion[]> [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of Google Cloud buckets.

|  |
| --- |
| Important |
| To be able to get a list of all buckets, you must configure the storage.buckets.list permission. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Connection | Specifies an active session with Google Cloud object storage. The cmdlet will return an array of Google Cloud buckets for this Google Cloud object storage. | Accepts the VBRGoogleCloudConnection object. To create this object, run the [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Region | Specifies an array of Google Cloud regions where Google Cloud buckets are located. The cmdlet will return an array of Google Cloud buckets from these Google Cloud regions. | Accepts the VBRGoogleCloudRegion[] object. To create this object, run the [Get-VBRGoogleCloudRegion](get-vbrgooglecloudregion.md) cmdlet. | True | Named | False |
| Name | Specifies a name of the Google Cloud bucket. The cmdlet will return the bucket with this name.  Note: If you do not have permissions to get all buckets, the cmdlet will not return the necessary bucket. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRGoogleCloudBucket object that contains an array of Google Cloud buckets.

Examples

Getting Array of Google Cloud Buckets within Region

This example shows how to get an array of all Google Cloud buckets from a particular Google Cloud region.

|  |
| --- |
| $account = Get-VBRGoogleCloudAccount -Id "936edf7c-7cf3-4ddc-9895-c7485ef4bb2c"  $connection = Connect-VBRGoogleCloudService -Account $account -ServiceType CapacityTier  $region = Get-VBRGoogleCloudRegion -Connection $connection  Get-VBRGoogleCloudBucket -Connection $connection -Region $region |

Perform the following steps:

1. Run the [Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable.
2. Run the [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md) cmdlet. Specify the Account and ServiceType parameter values. Save the result to the $connection variable.
3. Run the [Get-VBRGoogleCloudRegion](get-vbrgooglecloudregion.md) cmdlet. Specify the Connection parameter value. Save the result to the $region variable.
4. Run the Get-VBRGoogleCloudBucket cmdlet. Specify the following settings:

* Set the $connection variable as the Connection parameter value.
* Set the $region variable as the Region parameter value.

Related Commands

* [Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md)
* [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md)
* [Get-VBRGoogleCloudRegion](get-vbrgooglecloudregion.md)


