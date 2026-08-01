---
title: "Stop-VESQLDatabaseExport"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vesqldatabaseexport.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Stop-VESQLDatabaseExport


Short Description

Stops an active export job for a Microsoft SQL Server database.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VESQLDatabaseExport [-DatabaseExport] <VESQLDatabaseExport> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet stops an active export job for a Microsoft SQL Server database.

|  |
| --- |
| Note |
| Export jobs will not stop automatically if you close the PowerShell console. To stop the export job, you must run the Stop-VESQLDatabaseExport cmdlet. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| DatabaseExport | Specifies an export job that you want to stop. | Accepts the [VESQLDatabaseExport](vesqldatabaseexport.md) object. To get this object, run the [Get-VESQLDatabaseExport](get-vesqldatabaseexport.md) cmdlet. | True | 0 | True (ByValue) |
| Force | Defines that the cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Export Job

This example shows how to stop an export job for a Microsoft SQL Server database.

|  |
| --- |
| $export = Get-VESQLDatabaseExport  Stop-VESQLDatabaseExport -DatabaseExport $export[0] -Force |

Perform the following steps:

1. Run the [Get-VESQLDatabaseExport](get-vesqldatabaseexport.md) cmdlet. Save the result to the $export variable.

The cmdlet will return an array of active export jobs. Note the ordinal number of the necessary export job (in this example, it is the first export job in the array).

1. Run the Stop-VESQLDatabaseExport cmdlet. Set the $export variable as the DatabaseExport parameter value and select the necessary export job. Provide the Force parameter.

Related Commands

* [Get-VESQLDatabaseExport](get-vesqldatabaseexport.md)
* [Start-VESQLDatabaseExport](start-vesqldatabaseexport.md)

Page updated 2026-02-05

