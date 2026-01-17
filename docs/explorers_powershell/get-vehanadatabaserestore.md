---
title: "Get-VEHANADatabaseRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vehanadatabaserestore.html"
last_updated: "8/21/2025"
product_version: "13.0.1.1071"
---

# Get-VEHANADatabaseRestore


Short Description

Returns active SAP HANA restore jobs.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Return an active restore job using the job ID.

|  |
| --- |
| Get-VEHANADatabaseRestore -JobId <Guid> [<CommonParameters>] |

* Return an active restore job using the name of the restored database.

|  |
| --- |
| Get-VEHANADatabaseRestore [-DatabaseName <String>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of ongoing SAP HANA restore jobs. After you specify the restore job you need, you can use the [Get-VEHANARestoreJobActionLogItems](get-vehanarestorejobactionlogitems.md) cmdlet to get an overview of the restore process. You can also stop the restore process with the [Stop-VEHANADatabaseRestore](stop-vehanadatabaserestore.md) cmdlet or restart a failed restore job using the [Restart-VEHANADatabaseRestore](restart-vehanadatabaserestore.md) cmdlet.

Note the difference between a restore session and a restore job. A restore session is a preliminary step where Veeam Explorer for SAP HANA has retrieved the backup from the backup repository, pending restore operations. A restore job is the process of restoring data from the backup to the target SAP HANA system.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| DatabaseName | Specifies the name of a restored SAP HANA database. The cmdlet will return information about the restore process performed for the specified database. | String | False | Named | False |
| JobId | Specifies the job ID of the required restore job. The cmdlet will return information about the restore process performed for the specified database. | Guid | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEHANARestore](vehanarestore.md)[] array that contains information about ongoing SAP HANA restore jobs.

Notes

Get-VEHANADatabaseRestore replaces the deprecated cmdlet Get-VEHANARestoreJob. The old cmdlet still works (as an alias of the new cmdlet, with identical functionality), but it may be removed in a future version.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Active Restore Jobs

|  |  |
| --- | --- |
| This command gets all running restore jobs. Save the result to the $restore variable to be able to use it with other cmdlets.  |  | | --- | | $restore = Get-VEHANADatabaseRestore | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Restore Job by Job ID

|  |  |
| --- | --- |
| This example shows how to get a specific restore job by its job ID.  |  | | --- | | $restore = Get-VEHANADatabaseRestore  $restore = Get-VEHANADatabaseRestore -JobId $restore.Id[0] |  Perform the following steps:   1. Run the Get-VEHANADatabaseRestore cmdlet. Save the result to the $restore variable.   The cmdlet will return an array of active restore jobs. Note the ordinal number of the necessary restore job. In our example, it is the first restore job in the array.   1. Run the Get-VEHANADatabaseRestore cmdlet. Set a subset of the $restore variable, containing the first value in the Id column, as the JobId parameter value. Save the result to the $restore variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Restore Job by Database Name

|  |  |
| --- | --- |
| This example shows how to get a specific restore job by its database name.  |  | | --- | | $restore = Get-VEHANADatabaseRestore  $restore = Get-VEHANADatabaseRestore -DatabaseName $restore.Database[0] |  Perform the following steps:   1. Run the Get-VEHANADatabaseRestore cmdlet. Save the result to the $restore variable.   The cmdlet will return an array of active restore jobs. Note the ordinal number of the necessary restore job. In our example, it is the first restore job in the array.   1. Run the Get-VEHANADatabaseRestore cmdlet. Set a subset of the $restore variable, containing the first value in the Database column, as the DatabaseName parameter value. Save the result to the $restore variable to be able to use it with other cmdlets. |

Related Commands

* [Restart-VEHANADatabaseRestore](restart-vehanadatabaserestore.md)
* [Stop-VEHANADatabaseRestore](stop-vehanadatabaserestore.md)


