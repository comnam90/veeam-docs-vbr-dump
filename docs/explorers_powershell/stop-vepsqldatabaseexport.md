---
title: "Stop-VEPSQLDatabaseExport"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vepsqldatabaseexport.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# Stop-VEPSQLDatabaseExport


Short Description

Stops an active export session for a PostgreSQL database.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VEPSQLDatabaseExport [-Export] <VEPSQLDatabaseExport> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet stops an active export session for a PostgreSQL database.

|  |
| --- |
| Note |
| Export sessions will not stop automatically if you close the PowerShell console. To stop the export session, you must run the Stop-VEPSQLDatabaseExport cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Export | Specifies a PostgreSQL export session that you want to stop. | Accepts the [VEPSQLDatabaseExport](vepsqldatabaseexport.md) object. To get this object, run the [Get-VEPSQLDatabaseExport](get-vepsqldatabaseexport.md) cmdlet. | True | 0 | True (ByValue) |
| Force | Defines that the cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping PostgreSQL Export Session

This example shows how to stop a PostgreSQL export session.

|  |
| --- |
| $export = Get-VEPSQLDatabaseExport  Stop-VEPSQLDatabaseExport -Export $export[0] -Force |

Perform the following steps:

1. Run the [Get-VEPSQLDatabaseExport](get-vepsqldatabaseexport.md) cmdlet. Save the result to the $export variable.

The cmdlet will return an array of active export sessions. Note the ordinal number of the necessary export session (in our example, it is the first export session in the array).

1. Run the Stop-VEPSQLDatabaseExport cmdlet. Set the $export variable as the Export parameter value and select the necessary export session. Provide the Force parameter.

Related Commands

* [Get-VEPSQLDatabaseExport](get-vepsqldatabaseexport.md)
* [Start-VEPSQLDatabaseExport](start-vepsqldatabaseexport.md)


