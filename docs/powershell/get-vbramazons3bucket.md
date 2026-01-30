---
title: "Get-VBRAmazonS3Bucket"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbramazons3bucket.html"
last_updated: "3/8/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAmazonS3Bucket


Short Description

Returns Amazon S3 buckets.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAmazonS3Bucket -Connection <IVBRAmazonS3Connection> [-Region <VBRAmazonS3Region[]>] [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the VBRAmazonS3Bucket object that contains an array of Amazon S3 buckets for the following Amazon services:

* Amazon S3

* S3 compatible (including IBM Cloud Object Storage)

|  |
| --- |
| Important |
| To be able to get a list of all buckets, you must configure the s3:ListAllMyBuckets permission. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Connection | Specifies an active session with Amazon object storage. The cmdlet will return an array of Amazon S3 buckets for this Amazon object storage. | Accepts the IVBRAmazonS3Connection object. To get this object, run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet. | True | Named | False |
| Region | Specifies an array of Amazon S3 regions where Amazon S3 buckets are located. The cmdlet will return an array of Amazon S3 buckets from these Amazon S3 regions. | Accepts the VBRAmazonS3Region[] object. To get this object, run the [Get-VBRAmazonS3Region](get-vbramazons3region.md) cmdlet. | False | Named | True (ByValue) |
| Name | Specifies a name of the Amazon S3 bucket. The cmdlet will return the bucket with this name.  Note: If you do not grant necessary  permissions to the get all buckets, the cmdlet will not return the necessary bucket. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRAmazonS3Bucket

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Amazon S3 Buckets from Specific Amazon S3 Region

|  |  |
| --- | --- |
| This example shows how to get an array of all Amazon S3 buckets from a particular Amazon S3 region.  |  | | --- | | $account = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4ddc-9895-c7485ef4bb2c"  $connection = Connect-VBRAmazonS3Service -Account $account -RegionType Global -ServiceType CapacityTier  $region = Get-VBRAmazonS3Region -Connection $connection  Get-VBRAmazonS3Bucket -Connection $connection -Region $region |  Perform the following steps:   1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable. 2. Run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet. Set the $account variable as the Account parameter value. Specify the RegionType and ServiceType parameter values. Save the result to the $connection variable. 3. Run the [Get-VBRAmazonS3Region](get-vbramazons3region.md) cmdlet. Set the $connection variable as the Connection parameter value. Save the result to the $region variable. 4. Run the Get-VBRAmazonS3Bucket cmdlet. Set the $connection variable as the Connection parameter value. Set the $region variable as the Region parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All Amazon S3 Buckets from Specific Amazon S3 Region

|  |  |
| --- | --- |
| This example shows how to get an array of all Amazon S3 buckets from the selected Amazon S3 region.  |  | | --- | | $account = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4ddc-9895-c7485ef4bb2c"  $connection = Connect-VBRAmazonS3Service -Account $account -RegionType Global -ServiceType CapacityTier  $region = Get-VBRAmazonS3Region -Connection $connection -Regionid eu-west-1  Get-VBRAmazonS3Bucket -Connection $connection -Region $region |  Perform the following steps:   1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable. 2. Run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet. Set the $account variable as the Account parameter value. Specify the RegionType and ServiceType parameter values. Save the result to the $connection variable. 3. Run the [Get-VBRAmazonS3Region](get-vbramazons3region.md) cmdlet. Set the $connection variable as the Connection parameter value. Specify the Regionid parameter value. Save the result to the $region variable. 4. Run the Get-VBRAmazonS3Bucket cmdlet. Set the $connection variable as the Connection parameter value. Set the $region variable as the Region parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Amazon S3 Bucket

|  |  |
| --- | --- |
| This example shows how to get an Amazon S3 bucket.  |  | | --- | | $account = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4ddc-9895-c7485ef4bb2c"  $connection = Connect-VBRAmazonS3Service -Account $account -RegionType Global -ServiceType CapacityTier  Get-VBRAmazonS3Bucket -Connection $connection -Name "MyBucket" |  Perform the following steps:   1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable. 2. Run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet. Set the $account variable as the Account parameter value. Specify the RegionType and ServiceType parameter values. Save the result to the $connection variable. 3. Run the Get-VBRAmazonS3Bucket cmdlet. Set the $connection variable as the Connection parameter value. Specify the Name parameter value. |

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Connect-VBRAmazonS3Service](connect-vbramazons3service.md)
* [Get-VBRAmazonS3Region](get-vbramazons3region.md)


