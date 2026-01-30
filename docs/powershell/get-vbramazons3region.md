---
title: "Get-VBRAmazonS3Region"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbramazons3region.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAmazonS3Region


Short Description

Returns Amazon S3 regions.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAmazonS3Region -Connection <IVBRAmazonS3Connection> [-RegionId <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of Amazon S3 regions. You can get regions for the following services:

* Amazon S3

* S3 compatible (including IBM Cloud Object Storage)

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Connection | Specifies an active session with AWS. The cmdlet will return an array of all Amazon S3 regions from this session. | Accepts the IVBRAmazonS3Connection object. To get this object, run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet. | True | Named | False |
| RegionId | Specifies an ID of Amazon S3 region. The cmdlet will return an array of Amazon S3 regions with these IDs. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRAmazonS3Region

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Amazon S3 Regions

|  |  |
| --- | --- |
| This example shows how to get Amazon S3 regions.  |  | | --- | | $account = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c"  $connection = Connect-VBRAmazonS3Service -Account $account -RegionType Global -ServiceType CapacityTier  Get-VBRAmazonS3Region -Connection $connection |  Perform the following steps:   1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable. 2. Run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet. Set the $account variable as the Account parameter value. Specify the RegionType and ServiceType parameter values. Save the result to the $connection variable. 3. Run the Get-VBRAmazonS3Region cmdlet. Set the $connection variable as the Connection parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Amazon S3 Regions for Amazon S3 Object Storage

|  |  |
| --- | --- |
| This example shows how to get Amazon S3 regions for Amazon S3 object storage.  |  | | --- | | $account = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c"  $connection = Connect-VBRAmazonS3Service -Account $account -RegionType Global -ServiceType CapacityTier  Get-VBRAmazonS3Region -Connection $connection -RegionId "eu-west-3" |  Perform the following steps:   1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable. 2. Run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet. Set the $account variable as the Account parameter value. Specify the RegionType and ServiceType parameter values. Save the result to the $connection variable. 3. Run the Get-VBRAmazonS3Region cmdlet. Set the $connection variable as the Connection parameter value. Specify the RegionId parameter value. |

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Connect-VBRAmazonS3Service](connect-vbramazons3service.md)


