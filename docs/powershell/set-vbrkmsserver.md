---
title: "Set-VBRKMSServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrkmsserver.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Set-VBRKMSServer


Short Description

Modifies settings of KMS servers.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRKMSServer -Server <VBRKMSServer> [-CACertificate <X509Certificate2>] [-ClientCertificate <X509Certificate2>] [-Description <String>] [-Port <Int32>] [-Confirm] [-WhatIf]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of Key Management System servers (KMS server) added to the Veeam Backup & Replication console.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies a KMS server which settings you want to modify. | Accepts the VBRKMSServer object. To get this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| CACertificate | Specifies the KMS server certificate. | X509Certificate2 | False | Named | False |
| ClientCertificate | Specifies the client certificate issued by the KMS administrator for Veeam Backup & Replication. | X509Certificate2 | False | Named | False |
| Description | Specifies description of the KMS server. | String | False | Named | False |
| Port | Specifies a port number to connect to the KMS server.  Default: 5696. | Int32 | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRKMSServer](vbrkmsserver.md)

Examples

Modifying KMS Server Settings

This example shows how to modify the port number for the KMS server added to the Veeam Backup & Replication console.

|  |
| --- |
| $server = Get-VBRKMSServer -Id "8f723f68-82c6-430d-8915-58a0582440a4"  Set-VBRKMSServer -Server $server -Port 5696 |

Perform the following steps:

1. Run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. Specify the Id parameter values. Save the result to the $server variable.
2. Run the Set-VBRKMSServer cmdlet. Set the $server variable as the Server parameter value. Specify the Port parameter value.

Related Commands

[Get-VBRKMSServer](get-vbrkmsserver.md)


