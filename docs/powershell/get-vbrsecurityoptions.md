---
title: "Get-VBRSecurityOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrsecurityoptions.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Get-VBRSecurityOptions

In this article

Short Description

Returns Veeam Backup & Replication security settings.

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRSecurityOptions  [<CommonParameters>] |

Detailed Description

This cmdlet returns information on the following Veeam Backup & Replication security settings:

* [Backup Server Certificate](https://helpcenter.veeam.com/docs/vbr/userguide/backup_server_certificate.html?ver=13)
* [Linux Host Authentication](https://helpcenter.veeam.com/docs/vbr/userguide/linux_fingerprint_check.html?ver=13)
* [Audit Logs Location](https://helpcenter.veeam.com/docs/vbr/userguide/audit-logs-location.html?ver=13)

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSecurityOptions object that contains Veeam Backup & Replication security settings.

Examples

Getting Veeam Backup & Replication Security Settings

This example returns Veeam Backup & Replication security settings. The cmdlet output will contain the following details on the security settings: Certificate, TrustedHosts, HostPolicy, AuditLogsPath,CompressOldAuditLogs and the FipsCompliantModeEnabled.

|  |
| --- |
| Get-VBRSecurityOptions  Certificate              : Veeam.Backup.PowerShell.Infos.VBRBackupServerCertificate  TrustedHosts             : 0  HostPolicy               : Veeam.Backup.PowerShell.Infos.VBRLinuxTrustedHostPolicy  AuditLogsPath            : C:\ProgramData\Veeam\Backup\Audit  CompressOldAuditLogs     : True  FipsCompliantModeEnabled : False |

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
