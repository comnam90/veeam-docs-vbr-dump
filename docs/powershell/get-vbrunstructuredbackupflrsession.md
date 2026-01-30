---
title: "Get-VBRUnstructuredBackupFLRSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrunstructuredbackupflrsession.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRUnstructuredBackupFLRSession


Short Description

Returns restore sessions started to recover backups created by file backup jobs and object storage backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRUnstructuredBackupFLRSession  [<CommonParameters>] |

Detailed Description

This cmdlet returns restore sessions started to recover backups created by file backup jobs and object storage backup jobs.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUnstructuredBackupFLRSession object that contains settings of restore sessions started to recover backups created by file backup jobs and object storage backup jobs.

Examples

Getting Restore Sessions Running to Recover Backups of Unstructured Data Sources

This command gets all restore sessions that are started to recover backups created by file backup jobs and object storage backup jobs.

|  |
| --- |
| Get-VBRUnstructuredBackupFLRSession |


