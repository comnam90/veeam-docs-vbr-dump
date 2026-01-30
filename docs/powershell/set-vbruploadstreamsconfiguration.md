---
title: "Set-VBRUploadStreamsConfiguration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbruploadstreamsconfiguration.html"
last_updated: "4/23/2024"
product_version: "13.0.1.1071"
---

# Set-VBRUploadStreamsConfiguration


Short Description

Modifies data transfer settings for job sessions.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRUploadStreamsConfiguration -Configuration <VBRUploadStreamsConfiguration> [-Enable] [-StreamCount <Int32>] [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies existing data transfer settings for job sessions.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Configuration | Specifies data transfer settings for job sessions. The cmdlet will modify these settings. | Accepts the VBRUploadStreamsConfiguration object. To get this object, run the [Get-VBRUploadStreamsConfiguration](get-vbruploadstreamsconfiguration.md) cmdlet. | True | Named | False |
| Enable | Enables the multithreaded data transfer option if it is disabled. | SwitchParameter | False | Named | False |
| StreamCount | Specifies a number of TCP/IP connections per job session. | Int | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRUploadStreamsConfiguration

Examples

Modifying Data Transfer Settings to Change Number of TCP/IP Connections

This example shows how to modify data transfer settings and change a number of TCP/IP connections per job session. The cmdlet will return details about the modified data transfer settings.

|  |
| --- |
| $transfersettings = Get-VBRUploadStreamsConfiguration  Set-VBRUploadStreamsConfiguration -Configuration $transfersettings -StreamCount 7 -PassThru                                   Enabled                                                 StreamCount                                   -------                                                 -----------                                      True                                                           7 |

Perform the following steps:

1. Run the [Get-VBRUploadStreamsConfiguration](get-vbruploadstreamsconfiguration.md) cmdlet. Save the result to the $transfersettings variable.
2. Run the Set-VBRUploadStreamsConfiguration cmdlet. Set the $transfersettings variable as the Configuration parameter value. Specify the StreamCount parameter value. Provide the PassThru parameter.

Related Commands

[Get-VBRUploadStreamsConfiguration](get-vbruploadstreamsconfiguration.md)


