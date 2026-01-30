---
title: "Add-VBRAmazonAccount"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbramazonaccount.html"
last_updated: "1/30/2024"
product_version: "13.0.1.1071"
---

# Add-VBRAmazonAccount


Short Description

Creates AWS credentials records.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRAmazonAccount -AccessKey <string> -SecretKey <string> [-Description <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRAmazonAccount object. This object contains AWS credentials records to access the following services:

* Amazon S3

* Amazon EC2

* S3 compatible (including IBM Cloud object storage)

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| AccessKey | Specifies an access key. The cmdlet will use this key to add AWS credentials records to Veeam Backup & Replication. | String | True | Named | False |
| SecretKey | Specifies a secret key. The cmdlet will use this secret key to add the Amazon credentials records to Veeam Backup & Replication. | String | True | Named | False |
| Description | Specifies a description for AWS credentials records. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAmazonAccount object that contains AWS credentials records.

Examples

Creating AWS Credentials Record

This command creates an AWS credentials record.

|  |
| --- |
| Add-VBRAmazonAccount -AccessKey "ABCDEFGHIGKLMNOP" -SecretKey "vmdkflvm8908GUIEIE" -Description "Amazon credentials" |


