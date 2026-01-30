---
title: "Set-VBRSNMPReceiver"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrsnmpreceiver.html"
last_updated: "2/8/2024"
product_version: "13.0.1.1071"
---

# Set-VBRSNMPReceiver


Short Description

Modifies SNMP recipient settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRSNMPReceiver -Receiver <VBRSNMPReceiver> [-ReceiverIP <string>] [-ReceiverPort <int>] [-CommunityString <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies SNMP recipient settings.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Receiver | Specifies the SNMP recipient settings that you want to modify. | Accepts the VBRSNMPReceiver[] object. To create this object, run the [New-VBRSNMPReceiver](new-vbrsnmpreceiver.md) cmdlet. | True | Named | False |
| ReceiverIP | Specifies an IP addresses of the SNMP recipient. The cmdlet will modify this IP address. | String | False | Named | False |
| ReceiverPort | Specifies the port number that Veeam Backup & Replication will use to send messages. The cmdlet will modify this port number. | int | False | Named | False |
| CommunityString | Specifies the community identifier. The cmdlet will modify this community identifier. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSNMPReceiver object that defines SNMP recipient settings.

Examples

Modifying SNMP Recipient Settings Recepient IP

This example shows how to modify an IP address of the SNMP recipient from 172.17.53.28 to 172.17.53.23.

|  |
| --- |
| $options = New-VBRSNMPReceiver -ReceiverIP 172.17.53.28 -ReceiverPort 22 -CommunityString public  Set-VBRSNMPReceiver -Receiver $options -ReceiverIP  172.17.53.23 |

Perform the following steps:

1. Run the [New-VBRSNMPReceiver](new-vbrsnmpreceiver.md) cmdlet. Specify the ReceiverIP, ReceiverPort and the CommunityString parameters. Save the result to the $options variable.
2. Run the Set-VBRSNMPReceiver cmdlet. Set the $options variable as the Receiver parameter value. Specify the ReceiverIP parameter value.

Related Commands

[New-VBRSNMPReceiver](new-vbrsnmpreceiver.md)


