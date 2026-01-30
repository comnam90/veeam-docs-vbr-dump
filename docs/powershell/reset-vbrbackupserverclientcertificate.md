---
title: "Reset-VBRBackupServerClientCertificate"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/reset-vbrbackupserverclientcertificate.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Reset-VBRBackupServerClientCertificate


Short Description

Creates a new TLS certificate in the Veeam Backup & Replication database.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Reset-VBRBackupServerClientCertificate |

Detailed Description

The cmdlet removes an old TLS certificate from the Veeam Backup & Replication database and issues a new TLS certificate.

Parameters

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Creating New TLS Certificate

This command returns creates a new TLS certificate and adds it to the Veeam Backup & Replication database.

|  |
| --- |
| Reset-VBRBackupServerClientCertificate |


