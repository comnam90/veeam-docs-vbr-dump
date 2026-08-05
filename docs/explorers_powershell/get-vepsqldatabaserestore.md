---
title: "Get-VEPSQLDatabaseRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vepsqldatabaserestore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VEPSQLDatabaseRestore


Short Description

Returns information about restore processes for backed-up PostgreSQL databases.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get an active restore job using the job ID.

|  |
| --- |
| Get-VEPSQLDatabaseRestore -JobId <Guid>  [<CommonParameters>] |

* Get an active restore job using the name of the restored database.

|  |
| --- |
| Get-VEPSQLDatabaseRestore [-DatabaseName <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns information about the restore process for a backed-up PostgreSQL database.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| JobId | Specifies the job ID of the required restore job. The cmdlet will return information about the specified restore job. | Guid | True | Named | True (ByValue) |
| DatabaseName | Specifies names of restored PostgreSQL databases. The cmdlet will return restore jobs performed for the specified databases.  This parameter accepts wildcard characters. | String[] | False | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEPSQLDatabaseRestore](vepsqldatabaserestore.md)[] array that contains information about the restore process of PostgreSQL databases.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Restore Processes

|  |  |
| --- | --- |
| This command returns a list of all active restore processes for backed-up PostgreSQL databases. Save the result to the $restore variable to be able to use it with other cmdlets.  |  | | --- | | $restore = Get-VEPSQLDatabaseRestore | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Restore Process by Job ID

|  |  |
| --- | --- |
| This example shows how to get a specific restore job by its job ID. Save the result to the $restore variable to be able to use it with other cmdlets.  |  | | --- | | $restore = Get-VEPSQLDatabaseRestore -JobId "b6b9b806-bc3c-491c-8ef4-0490d0d2608c" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Restore Processes for Specific Database

|  |  |
| --- | --- |
| This command returns all active restore processes for a specific database. Save the result to the $restore variable to be able to use it with other cmdlets.  |  | | --- | | $restore = Get-VEPSQLDatabaseRestore -DatabaseName "location1" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Restore Processes for Specific Databases Using Wildcards

|  |  |
| --- | --- |
| This command returns all active restore jobs for databases whose names begin with "db". Save the result to the $restore variable to be able to use it with other cmdlets.  |  | | --- | | $restore = Get-VEPSQLDatabaseRestore -DatabaseName "db\*" | |

Page updated 2026-04-10

