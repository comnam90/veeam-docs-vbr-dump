---
title: "VBRSyslogServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrsyslogserver.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRSyslogServer


Contains settings of the syslog server.

Properties

| Property | Type | Description |
| --- | --- | --- |
| ServerHost | string | Syslog server. |
| Port | int | Syslog server port. |
| Protocol | VBRSyslogServerProtocol | Protocol that the syslog server uses. |
| CertificateThumbprint | string | [For TLS protocol] Certificate thumbprint. |

Related Commands

* [Add-VBRSyslogServer](add-vbrsyslogserver.md)
* [Set-VBRSyslogServer](set-vbrsyslogserver.md)
* [Get-VBRSyslogServer](get-vbrsyslogserver.md)
* [Remove-VBRSyslogServer](remove-vbrsyslogserver.md)


