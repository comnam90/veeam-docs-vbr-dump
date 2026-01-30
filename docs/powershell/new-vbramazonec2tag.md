---
title: "New-VBRAmazonEC2Tag"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbramazonec2tag.html"
last_updated: "12/13/2023"
product_version: "13.0.1.1071"
---

# New-VBRAmazonEC2Tag


Short Description

Defines AWS tags.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRAmazonEC2Tag -Key <string> -Value <string>  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRAmazonEC2Tag object that contains settings of AWS tags.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Key | Specifies a key for the AWS tag. The cmdlet will create the cmdlet with the specified key. | String | True | Named | False |
| Value | Specifies a value for the the AWS tag. The cmdlet will create the cmdlet with the specified value. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAmazonEC2Tag object that contains settings of AWS tags.

Examples

Defining AWS Tags

This command defines AWS tags.

|  |
| --- |
| New-VBRAmazonEC2Tag -Key webserver -Value production |


