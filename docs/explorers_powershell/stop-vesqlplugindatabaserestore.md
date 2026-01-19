---
title: "Stop-VESQLPluginDatabaseRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vesqlplugindatabaserestore.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---

# Stop-VESQLPluginDatabaseRestore


Short Description

Stops a restore job for a database backed up with Veeam Plug-in for Microsoft SQL Server.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VESQLPluginDatabaseRestore -RestoreJob <VESQLPluginRestore> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet stops a restore job for a database backed up by Veeam Plug-in for Microsoft SQL Server.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestoreJob | Specifies a restore job for a Microsoft SQL Server database. | Accepts the [VESQLPluginRestore](vesqlpluginrestore.md) object. To get this object, run the [Get-VESQLPluginDatabaseRestore](get-vesqlplugindatabaserestore.md) cmdlet. | True | Named | True (ByValue) |
| Force | Defines that the cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Restore Job

This example shows how to stop the restore job.

|  |
| --- |
| $restore = Get-VESQLPluginDatabaseRestore  Stop-VESQLPluginDatabaseRestore -RestoreJob $restore[3] -Force |

Perform the following steps:

1. Run the [Get-VESQLPluginDatabaseRestore](get-vesqlplugindatabaserestore.md) cmdlet. Save the result to the $restore variable.

The cmdlet will return an array of active restore jobs. Note the ordinal number of the necessary restore job (in our example, it is the fourth restore job in the array).

1. Run the Stop-VESQLPluginDatabaseRestore cmdlet. Set the $restore variable as the RestoreJob parameter value and select the necessary restore job. Note that the Force parameter is also provided, which will cause the restore job to be stopped without any additional prompts or warnings.

Related Commands

[Get-VESQLPluginDatabaseRestore](get-vesqlplugindatabaserestore.md)


