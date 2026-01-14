---
title: "Get-VBRBackupServerInfo"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrbackupserverinfo.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRBackupServerInfo

In this article

Short Description

Returns the backup server information.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRBackupServerInfo  [<CommonParameters>] |

Detailed Description

This cmdlet returns the following information on the backup server:

* Name — the IP or name of the backup server.
* Build — the build version of you Veeam Backup & Replication installation.
* PatchLevel — patch details.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRBackupServerInfo](vbrbackupserverinfo.md)

Examples

Getting Information on Backups Server

This command returns the IP address, current build version and patch details of the backup server.

|  |
| --- |
| Get-VBRBackupServerInfo |

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
