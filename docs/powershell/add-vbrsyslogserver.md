---
title: "Add-VBRSyslogServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrsyslogserver.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Add-VBRSyslogServer


Short Description

Adds a syslog server to Veeam Backup & Replication.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRSyslogServer -ServerHost <String> -Port <Int32> -Protocol <VBRSyslogServerProtocol> [-CertificateThumbprint <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds a syslog server to manage Veeam Backup & Replication events.

|  |
| --- |
| Note |
| You can specify only one syslog server for one Veeam Backup & Replication server. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ServerHost | Specifies an IPv4 address or DNS name of the syslog server. | String | True | Named | False |
| Port | Specifies the port number that the syslog server uses to send messages.  Default: 514 for UDP, 514 for TCP, 6514 for TLS. | Int32 | True | Named | False |
| Protocol | Specifies the protocol that the syslog server uses: Udp, Tcp, Tls.  Use the CertificateThumbprint parameter to specify the certificate thumbprint for the Tls protocol. | VBRSyslogServerProtocol | True | Named | False |
| CertificateThumbprint | Specifies the certificate thumbprint. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSyslogServer](vbrsyslogserver.md)

Examples

Adding Syslog Server

This command add a syslog server with the following settings:

* The IP address of the server is 172.17.53.28.
* The port that the syslog server uses is set to 514.
* The protocol is set to Udp.

|  |
| --- |
| Add-VBRSyslogServer -ServerHost "172.17.53.28" -Port 514 -Protocol Udp |


