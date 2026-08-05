---
title: "Stop-VESQLDatabasePublish"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vesqldatabasepublish.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Stop-VESQLDatabasePublish


Short Description

Unpublishes a Microsoft SQL Server database from the target server.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VESQLDatabasePublish [-DatabasePublish] <VESQLDatabasePublish> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet unpublishes a Microsoft SQL Server database from the target server.

|  |
| --- |
| Note |
| Publishing jobs will not stop automatically if you close the PowerShell console. To stop a publishing job, you must run the Stop-VESQLDatabasePublish cmdlet. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| DatabasePublish | Specifies the publishing process for a Microsoft SQL Server database. The cmdlet will stop the process and unpublish the database from the target Microsoft SQL Server machine. | Accepts the [VESQLDatabasePublish](vesqldatabasepublish.md) object. To get this object, run the [Get-VESQLDatabasePublish](get-vesqldatabasepublish.md) cmdlet. | True | 0 | True (ByValue) |
| Force | Defines that the cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Publishing Process for a Microsoft SQL Server Database

This example shows how to unpublish a Microsoft SQL Server database.

|  |
| --- |
| $publish = Get-VESQLDatabasePublish -DatabaseName "db1"  Stop-VESQLDatabasePublish -DatabasePublish $publish |

Perform the following steps:

1. Run the [Get-VESQLDatabasePublish](get-vesqldatabasepublish.md) cmdlet. Specify the DatabaseName parameter value and save the result to the $publish variable.
2. Run the Stop-VESQLDatabasePublish cmdlet. Set the $publish variable as the DatabasePublish parameter value.

Related Commands

[Get-VESQLDatabasePublish](get-vesqldatabasepublish.md)

Page updated 2026-04-10

