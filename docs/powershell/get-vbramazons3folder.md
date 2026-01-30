---
title: "Get-VBRAmazonS3Folder"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbramazons3folder.html"
last_updated: "3/8/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAmazonS3Folder


Short Description

Returns Amazon S3 folders.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAmazonS3Folder -Connection <IVBRAmazonS3Connection> -Bucket <VBRAmazonS3Bucket> -Name <string>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the VBRAmazonS3Folder object that contains an array of Amazon S3 folders. You can get the array of the folders for the following types of Amazon object storage:

* Amazon S3

* S3 compatible (including IBM Cloud Object Storage)

|  |
| --- |
| Note |
| The Get-VBRAmazonS3Folder cmdlet returns the array of Amazon S3 folders that are created under the following paths:   * [For Capacity Tier] - /Veeam/Archive/ * [For External Repository] - /Veeam/Backup/ |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Connection | Specifies an active session with Amazon S3 object storage. The cmdlet will return an array of the folders added to this object storage. | Accepts the IVBRAmazonS3Connection object. To get this object, run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet. | True | Named | False |
| Bucket | Specifies an Amazon S3 bucket. The cmdlet will return an array of the folders added to this bucket. | Accepts the VBRAmazonS3Bucket object. To get this object, run the [Get-VBRAmazonS3Bucket](get-vbramazons3bucket.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies a name of the Amazon S3 folder. Veeam Backup & Replication will return the folder with this name. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRAmazonS3Folder

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Folders Added to Amazon Object Storage

|  |  |
| --- | --- |
| This example shows how to get all folders added to Amazon object storage.  |  | | --- | | $account = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c"  $connection = Connect-VBRAmazonS3Service -Account $account -RegionType Global -ServiceType CapacityTier  $bucket = Get-VBRAmazonS3Bucket -Connection $connection  Get-VBRAmazonS3Folder -Connection $connection -Bucket $bucket |  Perform the following steps:   1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable. 2. Run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet. Set the $account variable as the Account parameter value. Specify the RegionType and ServiceType parameter values. Save the result to the $connection variable. 3. Run the [Get-VBRAmazonS3Bucket](get-vbramazons3bucket.md) cmdlet. Set the $connection variable as the Connection parameter value. Save the result to the $bucket variable. 4. Run the Get-VBRAmazonS3Folder cmdlet. Set the $connection variable as the Connection parameter value. Set the $bucket variable as the Bucket parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Folder Added to Amazon Object Storage

|  |  |
| --- | --- |
| This example shows how to get a folder added to Amazon object storage.  |  | | --- | | $account = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c"  $connection = Connect-VBRAmazonS3Service -Account $account -RegionType Global -ServiceType CapacityTier  $bucket = Get-VBRAmazonS3Bucket -Connection $connection  Get-VBRAmazonS3Folder -Connection $connection -Bucket $bucket -Name "NewBucket" |  Perform the following steps:   1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable. 2. Run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet. Set the $account variable as the Account parameter value. Specify the RegionType and ServiceType parameter values. Save the result to the $connection variable. 3. Run the [Get-VBRAmazonS3Bucket](get-vbramazons3bucket.md) cmdlet. Set the $connection variable as the Connection parameter value. Save the result to the $bucket variable. 4. Run the Get-VBRAmazonS3Folder cmdlet. Set the $connection variable as the Connection parameter value. Set the $bucket variable as the Bucket parameter value. Specify the Name parameter value. |

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Connect-VBRAmazonS3Service](connect-vbramazons3service.md)
* [Get-VBRAmazonS3Bucket](get-vbramazons3bucket.md)


