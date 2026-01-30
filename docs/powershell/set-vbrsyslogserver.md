---
title: "Set-VBRSyslogServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrsyslogserver.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Set-VBRSyslogServer


Short Description

Modifies the existing syslog server settings.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRSyslogServer -Server <VBRSyslogServer> [-ServerHost <String>] [-Port <Int32>] [-Protocol <VBRSyslogServerProtocol>] [-CertificateThumbprint <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the existing syslog server settings.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. This cmdlet will overwrite the previous parameter values with the new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the syslog server you want to modify. | Accepts the [VBRSyslogServer](vbrsyslogserver.md) object. To get this object, run the [Get-VBRSyslogServer](get-vbrsyslogserver.md) cmdlet. | True | Named | True (ByValue) |
| ServerHost | Specifies an IPv4 address or DNS name of the syslog server. | String | False | Named | False |
| Port | Specifies the port number that Veeam Backup & Replication will use to send messages.  Default: 514 for UDP, 514 for TCP, 6514 for TLS. | Int32 | False | Named | False |
| Protocol | Specifies the transport that Veeam Backup & Replication will use: Udp, Tcp, Tls.  Use the CertificateThumbprint parameter to specify the certificate thumbprint for Tls transport. | VBRSyslogServerProtocol | False | Named | False |
| CertificateThumbprint | Specifies the certificate thumbprint. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSyslogServer](vbrsyslogserver.md)

Examples

Modifying Protocol for Syslog Server

This example shows how to modify the existing syslog server settings to use Tcp protocol.

|  |
| --- |
| $server = Get-VBRSyslogServer  Set-VBRSyslogServer -Server $server -Protocol Tcp |

Perform the following steps:

1. Run the [Get-VBRSyslogServer](get-vbrsyslogserver.md) cmdlet. Save the result to the $server variable.
2. Run the Set-VBRSyslogServer cmdlet. Set the $server variable as the Server parameter value. Specify the Tcp value as the Protocol parameter value.

Related Commands

[Get-VBRSyslogServer](get-vbrsyslogserver.md)


