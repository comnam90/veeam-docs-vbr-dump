---
title: "Remove-VBRKMSServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrkmsserver.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRKMSServer


Short Description

Removes KMS servers from the Veeam Backup & Replication console.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRKMSServer -Server <VBRKMSServer> [-Confirm] [-WhatIf]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a KMS server from the Veeam Backup & Replication console.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies a KMS server that you want to remove. | Accepts the VBRKMSServer object. To get this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing KMS Server From Veeam Backup & Replication Console

This example shows how to remove the 8f723f68-82c6-430d-8915-58a0582440a4 KMS server from the Veeam Backup & Replication console.

|  |
| --- |
| $server = Get-VBRKMSServer -Id "8f723f68-82c6-430d-8915-58a0582440a4"  Remove-VBRKMSServer -Server $server -Port 5696 |

Perform the following steps:

1. Run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. Specify the Id parameter values. Save the result to the $server variable.
2. Run the Remove-VBRKMSServer cmdlet. Set the $server variable as the Server parameter value. Specify the Port parameter value.

Related Commands

[Get-VBRKMSServer](get-vbrkmsserver.md)


