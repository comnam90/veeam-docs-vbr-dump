---
title: "Get-VESQLDatabaseRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqldatabaserestore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VESQLDatabaseRestore


Short Description

Returns active restore jobs for Microsoft SQL Server databases.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get an active restore job using the job ID.

|  |
| --- |
| Get-VESQLDatabaseRestore -JobId <Guid> [<CommonParameters>] |

* Get an active restore job using the name of the restored database.

|  |
| --- |
| Get-VESQLDatabaseRestore [-DatabaseName <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns information about active restore jobs for a Microsoft SQL Server database. You can stop the restore process with the [Stop-VESQLDatabaseRestore](stop-vesqldatabaserestore.md) cmdlet.

Note the difference between a restore session and a restore job. A restore session is a preliminary step where Veeam Explorer for Microsoft SQL Server has retrieved the backup from the backup repository, pending restore operations. A restore job is the process of restoring data from the backup to the target Microsoft SQL Server server.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| JobId | Specifies the job ID of the required restore job. The cmdlet will return information about the specified restore job. | Guid | True | Named | True (ByValue) |
| DatabaseName | Specifies names of restored Microsoft SQL Server databases. The cmdlet will return restore jobs performed for the specified databases.  This parameter accepts wildcard characters. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLDatabaseRestore](vesqldatabaserestore.md)[] array that contains details on the restore job for a Microsoft SQL Server database.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Restore Processes

|  |  |
| --- | --- |
| This command returns a list of all active restore processes for Microsoft SQL Server databases. Save the result to the $restore variable to be able to use it with other cmdlets.  |  | | --- | | $restore = Get-VESQLDatabaseRestore | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Restore Process by Job ID

|  |  |
| --- | --- |
| This example shows how to get a specific restore job by its job ID. Save the result to the $restore variable to be able to use it with other cmdlets.  |  | | --- | | $restore = Get-VESQLDatabaseRestore -JobId "b6b9b806-bc7c-491c-8ef7-0490d0d2608c" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Restore Processes for Specific Database

|  |  |
| --- | --- |
| This command returns all active restore processes for a specific database. Save the result to the $restore variable to be able to use it with other cmdlets.  |  | | --- | | $restore = Get-VESQLDatabaseRestore -DatabaseName "location1" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Restore Processes for Specific Databases Using Wildcards

|  |  |
| --- | --- |
| This command returns all active restore jobs for databases whose names begin with "db". Save the result to the $restore variable to be able to use it with other cmdlets.  |  | | --- | | $restore = Get-VESQLDatabaseRestore -DatabaseName "db\*" | |

Page updated 2026-02-05

