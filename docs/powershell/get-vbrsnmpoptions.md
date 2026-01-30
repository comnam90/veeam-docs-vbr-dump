---
title: "Get-VBRSNMPOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrsnmpoptions.html"
last_updated: "1/29/2024"
product_version: "13.0.1.1071"
---

# Get-VBRSNMPOptions


Short Description

Returns global SNMP settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRSNMPOptions  [<CommonParameters>] |

Detailed Description

This cmdlet returns global SNMP settings.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSNMPOptions object that defines global SNMP settings.

Examples

Getting Global SNMP Settings

This example shows how to get global SNMP settings that are set up in your backup infrastructure.

|  |
| --- |
| $options = Get-VBRSNMPOptions  $options.Receiver  ReceiverIP   ReceiverPort CommunityString  ----------   ------------ ---------------  172.17.53.28           22 public  172.17.53.28           22 public  172.17.53.28           22 public |

Perform the following steps:

1. Run the Get-VBRSNMPOptions cmdlet. Save the result to the $options variable.
2. Provide the Receiver property of the $options variable.

The cmdlet output will contain the following details on the global SNMP settings: ReceiverIP, ReceiverPort and CommunityString.


