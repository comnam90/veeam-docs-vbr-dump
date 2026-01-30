---
title: "New-VBRGoogleCloudFolder"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrgooglecloudfolder.html"
last_updated: "2/29/2024"
product_version: "13.0.1.1071"
---

# New-VBRGoogleCloudFolder


Short Description

Creates Google Cloud folders.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRGoogleCloudFolder -Connection <VBRGoogleCloudConnection> -Bucket <VBRGoogleCloudBucket> [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates Google Cloud folders in the selected bucket. Veeam Backup & Replication will use these folders to keep backup files there.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Connection | Specifies an active session with Google Cloud object storage. The cmdlet will create a new folder in this Google Cloud object storage. | Accepts the VBRGoogleCloudConnection object. To create this object, run the [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Bucket | Specifies a Google Cloud bucket. The cmdlet will add a new Google Cloud folder to this bucket. | Accepts the VBRGoogleCloudBucket object. To create this object, run the [Get-VBRGoogleCloudBucket](get-vbrgooglecloudbucket.md) cmdlet. | True | Named | False |
| Name | Specifies an array of names for the Google Cloud folder. The cmdlet will create the Google Cloud folder with this name. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRGoogleCloudFolder object that contains Google Cloud folders added to the selected bucket.

Examples

Creating Google Cloud Folder

This example shows how to create a new Google Cloud folder.

|  |
| --- |
| $account = Get-VBRGoogleCloudAccount -Id "0x0x0xxx-000x-0x0x-000-000x00000x0x"  $connection = Connect-VBRGoogleCloudService -Account $account -RegionType Global -ServiceType CapacityTier  $bucket = Get-VBRGoogleCloudBucket -Connection $connection -Region $region  New-VBRGoogleCloudFolder -Connection $connection -Bucket $bucket -Name "NewFolder" |

Perform the following steps:

1. Run the [Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable.
2. Run the [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md) cmdlet. Specify the Account, RegionType, and ServiceType parameter values. Save the result to the $connection variable.
3. Run the [Get-VBRGoogleCloudBucket](get-vbrgooglecloudbucket.md) cmdlet. Specify the Connection and Region parameter values. Save the result to the $bucket variable.
4. Run the New-VBRGoogleCloudFolder cmdlet. Specify the following settings:

* Set the $connection variable as the Connection parameter value.
* Set the $bucket variable as the Bucket parameter value.
* Specify the Name parameter value.

Related Commands

* [Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md)
* [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md)
* [Get-VBRGoogleCloudBucket](get-vbrgooglecloudbucket.md)


