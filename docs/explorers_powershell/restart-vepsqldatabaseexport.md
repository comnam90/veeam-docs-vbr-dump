---
title: "Restart-VEPSQLDatabaseExport"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/restart-vepsqldatabaseexport.html"
last_updated: "1/7/2025"
product_version: "13.0.1.1071"
---

# Restart-VEPSQLDatabaseExport


Short Description

Restarts a failed export process for a backed-up PostgreSQL database.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Restart-VEPSQLDatabaseExport [-Export] <VEPSQLDatabaseExport> [<CommonParameters>] |

Detailed Description

This cmdlet restarts a failed export process for a PostgreSQL database.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Export | Specifies the PostgreSQL database export session that the cmdlet will restart. | Accepts the [VEPSQLDatabaseExport](vepsqldatabaseexport.md) object. To get this object, run the [Get-VEPSQLDatabaseExport](get-vepsqldatabaseexport.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Restarting PostgreSQL Export Session

This example shows how to restart a failed export process for a PostgreSQL database.

|  |
| --- |
| $export = Get-VEPSQLDatabaseExport  Restart-VEPSQLDatabaseExport -Export $export[0] |

Perform the following steps:

1. Run the [Get-VEPSQLDatabaseExport](get-vepsqldatabaseexport.md) cmdlet. Save the result to the $export variable.

The cmdlet will return an array of PostgreSQL export sessions. Note the ordinal number of the necessary export session. In our example, it is the first export session in the array.

1. Run the Restart-VEPSQLDatabaseExport cmdlet. Set the $export variable as the Export parameter value and select the necessary export session.

Related Commands

[Get-VEPSQLDatabaseExport](get-vepsqldatabaseexport.md)


