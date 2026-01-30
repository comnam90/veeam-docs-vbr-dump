---
title: "Remove-VBRAmazonAccount"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbramazonaccount.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRAmazonAccount


Short Description

Removes AWS credentials records from Veeam Backup & Replication.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRAmazonAccount -Account <VBRAmazonAccount> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes AWS credentials records from Veeam Backup & Replication. You can remove credentials records for the following services:

* Amazon S3

* Amazon EC2

* S3 compatible (including IBM Cloud Object Storage)

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies AWS credentials records that you want to remove. | Accepts the VBRAmazonAccount object. To get this object, run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. | True | Named | True (ByValue) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing AWS Credentials Record

This example shows how to remove an AWS credentials record.

|  |
| --- |
| $creds = Get-VBRAmazonAccount -AccessKey "ABCDEFGHIGKLMNOP"  Remove-VBRAmazonAccount -Account $creds |

Perform the following steps:

1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the AccessKey parameter value. Save the result to the $creds variable.
2. Run the Remove-VBRAmazonAccount cmdlet. Set the $creds variable as the Account parameter value.

Related Commands

[Get-VBRAmazonAccount](get-vbramazonaccount.md)


