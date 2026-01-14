---
title: "Remove-VBRSyslogServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrsyslogserver.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRSyslogServer

In this article

Short Description

Removes the syslog server.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRSyslogServer -Server <VBRSyslogServer>  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the syslog server added to Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the syslog server you want to remove. | Accepts the [VBRSyslogServer](vbrsyslogserver.md) object. To get this object, run the [Get-VBRSyslogServer](get-vbrsyslogserver.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Syslog Server from Veeam Backup & Replication

This example shows how to remove the existing syslog server.

|  |
| --- |
| $server = Get-VBRSyslogServer  Remove-VBRSyslogServer -Server $server |

Perform the following steps:

1. Run the [Get-VBRSyslogServer](get-vbrsyslogserver.md) cmdlet. Save the result to the $server variable.
2. Run the Remove-VBRSyslogServer cmdlet. Set the $server variable as the Server parameter value.

Related Commands

[Get-VBRSyslogServer](get-vbrsyslogserver.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
