---
title: "Get-VEMDBDataRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vemdbdatarestore.html"
last_updated: "8/10/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns active MongoDB restore jobs.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Return an active restore job using the job ID.

|  |
| --- |
| Get-VEMDBDataRestore -JobId <Guid> [<CommonParameters>] |

* Return an active restore job using the name of the restored collection.

|  |
| --- |
| Get-VEMDBDataRestore [-CollectionName <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of ongoing MongoDB restore jobs. After you specify the restore job you need, you can stop the restore process with the [Stop-VEMDBDataRestore](stop-vemdbdatarestore.md) cmdlet.

Note the difference between a restore session and a restore job. A restore session is a preliminary step where Veeam Explorer for MongoDB has retrieved the backup from the backup repository, pending restore operations. A restore job is the process of restoring data from the backup to the target MongoDB deployment.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CollectionName | Specifies an array of restored collections. The cmdlet will return information about the restore process performed for the specified collections.  This parameter accepts wildcard characters. | String[] | False | Named | False |
| JobId | Specifies the job ID of the required restore job. The cmdlet will return information about the restore process performed for the specified database. | Guid | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEMDBRestore](vemdbrestore.md)[] array that contains information about ongoing MongoDB restore jobs.

Notes

Get-VEMDBDataRestore replaces the deprecated cmdlet Get-VEMDBRestoreJob. The old cmdlet still works (as an alias of the new cmdlet, with identical functionality), but it may be removed in a future version.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Active Restore Jobs

|  |  |
| --- | --- |
| This command gets all running restore jobs. Save the result to the $restore variable to be able to use it with other cmdlets.  |  | | --- | | $restore = Get-VEMDBDataRestore | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Restore Job by Job ID

|  |  |
| --- | --- |
| This example shows how to get a specific restore job by its job ID.  |  | | --- | | $restore = Get-VEMDBDataRestore  $restore = Get-VEMDBDataRestore -JobId $restore.JobId[0] |  Perform the following steps:   1. Run the Get-VEMDBDataRestore cmdlet. Save the result to the $restore variable.   The cmdlet will return an array of active restore jobs. Note the ordinal number of the necessary restore job. In our example, it is the first restore job in the array.   1. Run the Get-VEMDBDataRestore cmdlet. Set a subset of the $restore variable, containing the first value in the JobId column, as the JobId parameter value. Save the result to the $restore variable to be able to use it with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Restore Job by Collection Name

|  |  |
| --- | --- |
| This example shows how to get a specific restore session to perform operations with MongoDB databases.  |  | | --- | | $restore = Get-VEMDBDataRestore  $collections = @("on-site", "off-site")  $restore = Get-VEMDBDataRestore -CollectionName $collections |  Perform the following steps:   1. Run the Get-VEMDBDataRestore cmdlet. Save the result to the $restore variable.   The cmdlet will return an array of active restore jobs. Note the ordinal number of the necessary restore job. In our example, it is the first restore job in the array.   1. Declare the $collections variable. Assign to this variable an array with the names of the necessary MongoDB collections. 2. Run the Get-VEMDBDataRestore cmdlet. Set the $collections variable as the CollectionName parameter value. Save the result to the $restore variable to be able to use it with other cmdlets. |

Related Commands

[Stop-VEMDBDataRestore](stop-vemdbdatarestore.md)

Page updated 8/10/2025

Page content applies to build 13.0.1.1071
