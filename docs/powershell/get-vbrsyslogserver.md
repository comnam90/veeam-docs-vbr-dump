---
title: "Get-VBRSyslogServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrsyslogserver.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRSyslogServer

In this article

Short Description

Returns the syslog server added to Veeam Backup & Replication.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRSyslogServer  [<CommonParameters>] |

Detailed Description

This cmdlet returns the syslog server added to Veeam Backup & Replication.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSyslogServer](vbrsyslogserver.md)

Examples

Getting Syslog Server

This command returns the existing syslog server.

|  |
| --- |
| Get-VBRSyslogServer |

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
