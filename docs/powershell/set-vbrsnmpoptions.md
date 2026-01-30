---
title: "Set-VBRSNMPOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrsnmpoptions.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Set-VBRSNMPOptions


Short Description

Modifies global SNMP settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRSNMPOptions -Receiver <VBRSNMPReceiver[]>  [<CommonParameters>] |

Detailed Description

This cmdlet modifies global SNMP settings. You can run this cmdlet, if you want to add SNMP recipient settings to the global SNMP settings.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Receiver | Specifies an array of IP addresses of the SNMP recipient. | Accepts the VBRSNMPReceiver[] object. To create this object, run the [New-VBRSNMPReceiver](new-vbrsnmpreceiver.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSNMPOptions object that defines global SNMP settings.

Examples

Modifying Global SNMP Settings

This example shows how to add the following SNMP settings to the global SNMP settings:

* An IP addresses of the SNMP recipient is set to 172.17.53.28.
* The port that Veeam Backup & Replication will use to send messages is set to 22.
* The community identifier is set to public.

|  |
| --- |
| $recipient = New-VBRSNMPReceiver -ReceiverIP 172.17.53.28 -ReceiverPort 22 -CommunityString public  Set-VBRSNMPOptions -Receiver $recipient  ReceiverIP   ReceiverPort CommunityString  ----------   ------------ ---------------  172.17.53.28           22 public |

Perform the following steps:

1. Run the [New-VBRSNMPReceiver](new-vbrsnmpreceiver.md) cmdlet. Specify the ReceiverIP, ReceiverPort and the CommunityString parameters. Save the result to the $recipient variable.
2. Run the Set-VBRSNMPReceiver cmdlet. Set the $recipient variable as the Receiver parameter value.

The cmdlet output will contain the following SNMP settings: ReceiverIP, ReceiverPort and the CommunityString.

Related Commands

[New-VBRSNMPReceiver](new-vbrsnmpreceiver.md)


