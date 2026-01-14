---
title: "Disconnect-VBRAmazonS3Service"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disconnect-vbramazons3service.html"
last_updated: "2/29/2024"
product_version: "13.0.1.1071"
---

# Disconnect-VBRAmazonS3Service

In this article

Short Description

Stops active sessions with Amazon S3 and S3 compatible object storage.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disconnect-VBRAmazonS3Service -Connection <IVBRAmazonS3Connection>  [<CommonParameters>] |

Detailed Description

This cmdlet stops active sessions with Amazon S3 object storage. You can stop current sessions for the following types of Amazon object storage:

* Amazon S3
* S3 compatible (including IBM Cloud Object Storage)

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Connection | Specifies a session with Amazon S3 object storage that you want to stop. | Accept the IVBRAmazonS3Connection object. To get this object, run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Stopping Active Session with Amazon S3 Object Storage

This example shows how to stops an active session with Amazon S3 object storage.

|  |
| --- |
| $account = Get-VBRAmazonAccount -AccessKey "ABCDEFGHIGKLMNOP"  $session = Connect-VBRAmazonS3Service -Account $account -RegionType Global -ServiceType CapacityTier  Disconnect-VBRAmazonS3Service -Connection $session |

Perform the following steps:

1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the AccessKey parameter value. Save the result to the $account variable.
2. Run the [Connect-VBRAmazonS3Service](connect-vbramazons3service.md) cmdlet. Set the $account variable as the Account parameter value. Specify the RegionType and ServiceType parameter values. Save the result to the $session variable.
3. Run the Disconnect-VBRAmazonS3Service cmdlet. Set the $session variable as the Connection parameter value.

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Connect-VBRAmazonS3Service](connect-vbramazons3service.md)

Page updated 2/29/2024

Page content applies to build 13.0.1.1071
