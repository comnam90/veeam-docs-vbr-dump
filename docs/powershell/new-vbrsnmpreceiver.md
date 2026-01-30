---
title: "New-VBRSNMPReceiver"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrsnmpreceiver.html"
last_updated: "1/29/2024"
product_version: "13.0.1.1071"
---

# New-VBRSNMPReceiver


Short Description

Defines SNMP recipient settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRSNMPReceiver -ReceiverIP <string> [-ReceiverPort <int>] [-CommunityString <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRSNMPReceiver object that defines recipients SNMP settings. You can define settings for 5 different recipients.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ReceiverIP | Specifies an IP addresses of the SNMP recipient. | String | False | Named | False |
| ReceiverPort | Specifies the port number that Veeam Backup & Replication will use to send messages. | int | False | Named | False |
| CommunityString | Specifies the community identifier. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSNMPReceiver object that defines SNMP recepients settings.

Examples

Defining SNMP Recepients Settings

This command defines the following SNMP recepients settings:

* An IP addresses of the SNMP recipient is set to 172.17.53.28.
* The port that Veeam Backup & Replication will use to send messages is set to 22.
* The community identifier is set to public.

|  |
| --- |
| New-VBRSNMPReceiver -ReceiverIP 172.17.53.28 -ReceiverPort 22 -CommunityString public |


