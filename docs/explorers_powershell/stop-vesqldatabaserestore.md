---
title: "Stop-VESQLDatabaseRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vesqldatabaserestore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Stop-VESQLDatabaseRestore


Short Description

Stops a restore job for a Microsoft SQL Server database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VESQLDatabaseRestore [-DatabaseRestore] <VESQLDatabaseRestore> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet stops a restore job for a Microsoft SQL Server database.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| DatabaseRestore | Specifies a restore job for a Microsoft SQL Server database. | Accepts the [VESQLDatabaseRestore](vesqldatabaserestore.md) object. To get this object, run the [Get-VESQLDatabaseRestore](get-vesqldatabaserestore.md) cmdlet. | True | 0 | True (ByValue) |
| Force | Defines that the cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Restore Job

This example shows how to stop a restore job.

|  |
| --- |
| $restore = Get-VESQLDatabaseRestore  Stop-VESQLDatabaseRestore -DatabaseRestore $restore[3] -Force |

Perform the following steps:

1. Run the [Get-VESQLDatabaseRestore](get-vesqldatabaserestore.md) cmdlet. Save the result to the $restore variable.

The cmdlet will return an array of active restore jobs. Note the ordinal number of the necessary restore job (in this example, it is the fourth restore job in the array).

1. Run the Stop-VESQLDatabaseRestore cmdlet. Set the $restore variable as the DatabaseRestore parameter value and select the necessary restore job. Note that the Force parameter is also provided, which will cause the restore job to be stopped without any additional prompts or warnings.

Related Commands

[Get-VESQLDatabaseRestore](get-vesqldatabaserestore.md)

Page updated 2026-02-03

