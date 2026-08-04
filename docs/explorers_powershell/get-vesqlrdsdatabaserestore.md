---
title: "Get-VESQLRDSDatabaseRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqlrdsdatabaserestore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VESQLRDSDatabaseRestore


Short Description

Returns active restore jobs for backed-up Microsoft SQL Server databases running on Amazon RDS.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get an active restore job using the job ID.

|  |
| --- |
| Get-VESQLRDSDatabaseRestore -JobId <Guid>  [<CommonParameters>] |

* Get an active restore job using the name of the restored database.

|  |
| --- |
| Get-VESQLRDSDatabaseRestore [-DatabaseName <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns information about active restore jobs for a backed-up Microsoft SQL Server database running on Amazon RDS. You can stop the restore process with the [Stop-VESQLRDSDatabaseRestore](stop-vesqlrdsdatabaserestore.md) cmdlet.

Note the difference between a restore session and a restore job. A restore session is a preliminary step where Veeam Explorer for Microsoft SQL Server has retrieved the backup from the backup repository, pending restore operations. A restore job is the process of restoring data from the backup to the target Microsoft SQL Server server.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| JobId | Specifies the job ID of the required restore job. The cmdlet will return information about the specified restore job. | Guid | True | Named | True (ByValue) |
| DatabaseName | Specifies names of restored Microsoft SQL Server databases. The cmdlet will return restore jobs performed for the specified databases.  This parameter accepts wildcard characters. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLRDSDatabaseRestore](vesqlrdsdatabaserestore.md)[] array that contains information about the restore process of backed-up Microsoft SQL Server databases running on Amazon RDS.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Restore Processes

|  |  |
| --- | --- |
| This command returns a list of all active restore processes for backed-up Microsoft SQL Server databases running on Amazon RDS. Save the result to the $restore variable to be able to use it with other cmdlets.  |  | | --- | | $restore = Get-VESQLRDSDatabaseRestore | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Restore Process by Job ID

|  |  |
| --- | --- |
| This example shows how to get a specific restore job by its job ID. Save the result to the $restore variable to be able to use it with other cmdlets.  |  | | --- | | $restore = Get-VESQLRDSDatabaseRestore -JobId "b6b9b806-bc7c-491c-8ef7-0490d0d2608c" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Restore Processes for Specific Database

|  |  |
| --- | --- |
| This command returns all active restore processes for a specific database. Save the result to the $restore variable to be able to use it with other cmdlets.  |  | | --- | | $restore = Get-VESQLRDSDatabaseRestore -DatabaseName "location1" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Restore Processes for Specific Databases Using Wildcards

|  |  |
| --- | --- |
| This command returns all active restore jobs for databases whose names begin with "db". Save the result to the $restore variable to be able to use it with other cmdlets.  |  | | --- | | $restore = Get-VESQLRDSDatabaseRestore -DatabaseName "db\*" | |

Page updated 2026-01-27

