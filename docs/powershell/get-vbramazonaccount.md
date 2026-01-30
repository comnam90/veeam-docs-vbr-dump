---
title: "Get-VBRAmazonAccount"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbramazonaccount.html"
last_updated: "1/30/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAmazonAccount


Short Description

Returns AWS credentials records.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides the following parameter sets:

* To get AWS credentials records by the AWS access key.

|  |
| --- |
| Get-VBRAmazonAccount [-AccessKey <string[]>]  [<CommonParameters>] |

* To get AWS credentials records by the AWS ID.

|  |
| --- |
| Get-VBRAmazonAccount [-Id <Guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of existing AWS credentials records managed by Veeam Backup & Replication. Veeam Backup & Replication will use these credentials records to access the following services:

* Amazon S3

* Amazon EC2

* S3 compatible (including IBM Cloud Object Storage)

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of IDs for AWS credentials records. The cmdlet will return AWS credentials records with these IDs. | Guid[] | False | Named | False |
| AccessKey | Specifies an array of access keys for AWS credentials records. The cmdlet will return AWS credentials records with these access keys. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAmazonAccount object that contains AWS credentials records.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting AWS Credentials Record by Access Key

|  |  |
| --- | --- |
| This command gets an AWS credentials record by the AWS access key.  |  | | --- | | Get-VBRAmazonAccount -AccessKey "XXXXXXXXXXXXXXXXXXXXXXX" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting AWS Credentials Record by AWS ID

|  |  |
| --- | --- |
| This command gets an AWS credentials record by the AWS ID.  |  | | --- | | Get-VBRAmazonAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c", "936edf7c-7cf3-4ddc-9895-c7485ef4bb2c" | |


