---
title: "Set-VBRAmazonAccount"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbramazonaccount.html"
last_updated: "1/30/2024"
product_version: "13.0.1.1071"
---

# Set-VBRAmazonAccount

In this article

Short Description

Modifies AWS credentials records.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRAmazonAccount -Account <VBRAmazonAccount> [-AccessKey <string>] [-SecretKey <string>] [-Description <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to modify AWS credentials records. You can modify credentials records for the following services:

* Amazon S3

* Amazon EC2

* S3 compatible (including IBM Cloud Object Storage)

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies AWS credentials records that you want to modify. | Accepts the VBRAmazonAccount object. To get this object, run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. | True | Named | True (ByValue) |
| Description | Specifies a description for AWS credentials records. | String | False | Named | False |
| AccessKey | Specifies an access key. The cmdlet will use this access key to add AWS credentials records to Veeam Backup & Replication. | String | False | Named | False |
| SecretKey | Specifies a secret key. The cmdlet will use this secret key to add AWS credentials records to Veeam Backup & Replication. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAmazonAccount object that contains AWS credentials records.

Examples

Modifying AWS Credentials Record

This example shows how to modify an AWS credentials record.

|  |
| --- |
| $creds = Get-VBRAmazonAccount -AccessKey "ABCDEFGHIGKLMNOP"  Set-VBRAmazonAccount -Account $creds -SecretKey "vmdkfdvdvdvEIE" |

Perform the following steps:

1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the AccessKey parameter value. Save the result to the $creds variable.
2. Run the Set-VBRAmazonAccount cmdlet. Set the $creds variable as the Account parameter value. Specify the SecretKey parameter value.

Related Commands

[Get-VBRAmazonAccount](get-vbramazonaccount.md)

Page updated 1/30/2024

Page content applies to build 13.0.1.1071
