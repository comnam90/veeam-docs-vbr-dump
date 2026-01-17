---
title: "Stop-VEMDBDataRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vemdbdatarestore.html"
last_updated: "8/10/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Stops the restore process for backed-up MongoDB data.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VEMDBDataRestore -RestoreJob <VEMDBRestore> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet stops an ongoing restore job for backed-up MongoDB data.

|  |
| --- |
| Note |
| Restore jobs will not stop automatically if you close the PowerShell console. To stop the restore session, you must run the Stop-VEMDBDataRestore cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Force | Defines that the cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |
| RestoreJob | Specifies an initiated MongoDB restore job. The cmdlet will stop this job. | Accepts the [VEMDBRestore](vemdbrestore.md) object. To get this object, run the [Get-VEMDBDataRestore](get-vemdbdatarestore.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Notes

Stop-VEMDBDataRestore replaces the deprecated cmdlet Stop-VEMDBRestoreJob. The old cmdlet still works (as an alias of the new cmdlet, with identical functionality), but it may be removed in a future version.

Example

Stopping Restore Job

This example shows how to stop a MongoDB restore job.

|  |
| --- |
| $restore = Get-VEMDBDataRestore  Stop-VEMDBDataRestore -RestoreJob $restore[3] -Force |

Perform the following steps:

1. Run the [Get-VEMDBDataRestore](get-vemdbdatarestore.md) cmdlet. Save the result to the $restore variable.

The cmdlet will return an array of active restore jobs. Note the ordinal number of the necessary restore job (in our example, it is the fourth restore job in the array).

1. Run the Stop-VEMDBDataRestore cmdlet. Set the $restore variable as the RestoreJob parameter value and select the necessary restore job. Note that the Force parameter is also provided, which will cause the restore job to be stopped without any additional prompts or warnings.

Related Commands

[Get-VEMDBDataRestore](get-vemdbdatarestore.md)

Page updated 8/10/2025

Page content applies to build 13.0.1.1071
