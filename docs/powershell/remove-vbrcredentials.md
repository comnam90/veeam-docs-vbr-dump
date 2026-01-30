---
title: "Remove-VBRCredentials"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrcredentials.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRCredentials


Short Description

Removes credentials records from Veeam Backup & Replication.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRCredentials -Credential <CCredentials>  [<CommonParameters>] |

Detailed Description

This cmdlet permanently removes the selected credentials record from the Veeam Backup & Replication database.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Credential | Specifies credentials you want to remove. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Credentials Record Using User Name [Using Variable]

|  |  |
| --- | --- |
| This example shows how to remove the credentials record with the Administrator user name.  |  | | --- | | $credentials = Get-VBRCredentials -Name "Administrator"  Remove-VBRCredentials -Credential $credentials |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $credentials variable. 2. Run the Remove-VBRCredentials cmdlet. Set the $credentials variable as the Credential parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Credentials Record Using User Name [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove the credentials record with the Administrator user name.  |  | | --- | | Get-VBRCredentials -Name "Administrator" | Remove-VBRCredentials |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Remove-VBRCredentials cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Removing Specific Credentials Record

|  |  |
| --- | --- |
| This example shows how to remove the specific credentials record.  |  | | --- | | $credentials = Get-VBRCredentials  Remove-VBRCredentials -Credential $credentials[1] |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $credentials variable.   The Get-VBRCredentials cmdlet will return an array of credential records. Mind the ordinal number of the necessary credential record (in our example, it is the second credential record in the array).   1. Run the Remove-VBRCredentials cmdlet. Set the $credentials variable as the Credential parameter value. |

Related Commands

[Get-VBRCredentials](get-vbrcredentials.md)


