---
title: "Stop-VESQLRDSDatabaseRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vesqlrdsdatabaserestore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Stop-VESQLRDSDatabaseRestore


Short Description

Stops a restore job for a backed-up Microsoft SQL Server database running on Amazon RDS.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VESQLRDSDatabaseRestore [-DatabaseRestore] <VESQLRDSDatabaseRestore> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet stops a restore job for a backed-up Microsoft SQL Server database running on Amazon RDS.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| DatabaseRestore | Specifies a restore job for a Microsoft SQL Server database. | Accepts the [VESQLRDSDatabaseRestore](vesqlrdsdatabaserestore.md) object. To get this object, run the [Get-VESQLRDSDatabaseRestore](get-vesqlrdsdatabaserestore.md) cmdlet. | True | 0 | True (ByValue) |
| Force | Defines that the cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Restore Job

This example shows how to stop the restore job.

|  |
| --- |
| $restore = Get-VESQLRDSDatabaseRestore  Stop-VESQLRDSDatabaseRestore -DatabaseRestore $restore[3] -Force |

Perform the following steps:

1. Run the [Get-VESQLRDSDatabaseRestore](get-vesqlrdsdatabaserestore.md) cmdlet. Save the result to the $restore variable.

The cmdlet will return an array of active restore jobs. Note the ordinal number of the necessary restore job (in this example, it is the fourth restore job in the array).

1. Run the Stop-VESQLRDSDatabaseRestore cmdlet. Set the $restore variable as the DatabaseRestore parameter value and select the necessary restore job. Note that the Force parameter is also provided, which will cause the restore job to be stopped without any additional prompts or warnings.

Related Commands

[Get-VESQLRDSDatabaseRestore](get-vesqlrdsdatabaserestore.md)

Page updated 2026-04-10

