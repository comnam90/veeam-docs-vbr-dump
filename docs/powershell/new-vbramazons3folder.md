---
title: "New-VBRAmazonS3Folder"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbramazons3folder.html"
last_updated: "2/29/2024"
product_version: "13.0.1.1071"
---

# New-VBRAmazonS3Folder


Short Description

Creates Amazon S3 folders.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRAmazonS3Folder -Connection <IVBRAmazonS3Connection> -Bucket <VBRAmazonS3Bucket> -Name <string>  [<CommonParameters>] |

Detailed Description

This cmdlet creates Amazon S3 folders in the selected bucket. Veeam Backup & Replication will use these folders to keep backup files there. You can create a new folder for the following types of Amazon object storage:

* Amazon S3

* S3 compatible (including IBM Cloud Object Storage)

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Connection | Specifies an active session with Amazon S3 object storage. The cmdlet will create a new folder in this Amazon S3 object storage. | Accepts the IVBRAmazonS3Connection object. To get this object, run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet and set the CapacityTier or ArchiveTier property as the ServiceType parameter value. | True | Named | False |
| Bucket | Specifies an Amazon S3 bucket. The cmdlet will add a new Amazon S3 folder to this bucket. | Accepts the VBRAmazonS3Bucket object. To get this object, run the [Get-VBRAmazonS3Bucket](get-vbramazons3bucket.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies a name of the Amazon S3 folder. The cmdlet will create the Amazon S3 folder with this name. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRAmazonS3Folder

Examples

Creating New Amazon S3 Folder

This example shows how to create a new Amazon S3 folder.

|  |
| --- |
| $account = Get-VBRAmazonAccount -Id "0x0x0xxx-000x-0x0x-000-000x00000x0x"  $connection = Connect-VBRAmazonS3Service -Account $account -RegionType Global -ServiceType CapacityTier  $bucket = Get-VBRAmazonS3Bucket -Connection $connection  New-VBRAmazonS3Folder -Connection $connection -Bucket $bucket -Name "NewFolder" |

Perform the following steps:

1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable.
2. Run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet. Set the $account variable as the Account parameter value. Specify the RegionType and ServiceType parameter values. Save the result to the $connection variable.
3. Run the [Get-VBRAmazonS3Bucket](get-vbramazons3bucket.md) cmdlet. Set the $connection variable as the Connection parameter value. Save the result to the $bucket variable.
4. Run the New-VBRAmazonS3Folder cmdlet. Set the $connection variable as the Connection parameter value. Set the $bucket variable as the Bucket parameter value. Specify the Name parameter value.

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Connect-VBRAmazonS3Service](connect-vbramazons3service.md)
* [Get-VBRAmazonS3Bucket](get-vbramazons3bucket.md)


