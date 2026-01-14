---
title: "Get-VBRRestorePoint"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrrestorepoint.html"
last_updated: "6/19/2024"
product_version: "13.0.1.1071"
---

# Get-VBRRestorePoint

In this article

Short Description

Returns restore points.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all restore points.

|  |
| --- |
| Get-VBRRestorePoint [-Backup <CBackup[]>] [-Name <String[]>] [-ObjectId <Guid[]>]  [<CommonParameters>] |

* Get restore points by their ID.

|  |
| --- |
| Get-VBRRestorePoint -Id <Guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns restore points created by Veeam Backup & Replication.

Restore points created by replication jobs are represented as snapshots.

Restore points created by backup jobs are represented as full and increment backup files.

|  |
| --- |
| Important |
| To get a list of restore points for a Veeam Agent job, you must provide the asterisks sign for the Name parameter value: Name "AgentJob\*". Otherwise, the Get-VBRRestorePoint cmdlet will not return any restore points for the Veeam Agent job. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of IDs of backed-up VMs. The cmdlet will return restore points of these VMs. | Guid[] | True | Named | True (ByPropertyName) |
| Backup | Specifies the array of backups. The cmdlet will return restore points of these backups. | Accepts the CBackup[] object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | False | 0 | True (ByValue, |
| Name | Specifies an array of VM names. The cmdlet will return restore points of these VMs.  Note: For Cloud Director and CDP replica you must specify a vApp. | String[] | False | Named | False |
| ObjectId | Specifies an array of IDs of backed-up hosts and VMs. The cmdlet will return restore points of these hosts and VMs. | Guid[] | False | Named | True ( ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the COib object that contains information on restore points created by Veeam Backup & Replication.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Restore Points

|  |  |
| --- | --- |
| This command looks for all restore points of all VMs registered in the database.  |  | | --- | | Get-VBRRestorePoint | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Restore Points by ID

|  |  |
| --- | --- |
| This command looks for the 2ee79fec-9aa8-4058-a147-ff6b76ef2924 restore point.  |  | | --- | | Get-VBRRestorePoint -Id 2ee79fec-9aa8-4058-a147-ff6b76ef2924 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Restore Points Created by Backup Job

|  |  |
| --- | --- |
| This example shows how to get all restore points of the MSExchange02 VM that is backed up by the MSExchange backup job.  |  | | --- | | $backup = Get-VBRBackup -Name "MSExchange"  Get-VBRRestorePoint -Name \*MSExchange02\* -Backup $backup |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the Get-VBRRestorePoint cmdlet. Specify the Name parameter value. Set the $backup variable as the Backup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Restore Points Created by Replication Job

|  |  |
| --- | --- |
| This example shows how to get all restore points of VMs that are replicated by the DC Replica replication job.  |  | | --- | | $replica = Get-VBRReplica -Name "DC Replica"  Get-VBRRestorePoint -Backup $replica |  Perform the following steps:   1. Run the [Get-VBRReplica](get-vbrreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable. 2. Run the Get-VBRRestorePoint cmdlet. Set the $replica variable as the Backup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Getting Restore Points Created by Veeam Agent

|  |  |
| --- | --- |
| This example shows how to get all restore points of Windows-based machines backed up by the WinBackup Veeam Agent job.  |  | | --- | | $winbackup = Get-VBRBackup -Name "WinBackup"  Get-VBRRestorePoint -Backup $winbackup |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $winbackup variable. 2. Run the Get-VBRRestorePoint cmdlet. Set the $winbackup variable as the Backup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 6. Getting Latest Restore Point Created by Backup Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to look for the latest restore point of VMs that are backed up by the MSExchange Backup backup job.  |  | | --- | | Get-VBRBackup -Name MSExchange Backup | Get-VBRRestorePoint -Name MSExchange02 | Sort-Object –Property CreationTime –Descending | Select-Object -First 1 |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Get-VBRRestorePoint cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter. 4. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Specify the First parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 7. Getting Latest Restore Point Created by Replication Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to return the latest restore point of the MSExchange02 VM that is replicated by the Replica\_Exchange replication job.  |  | | --- | | Get-VBRReplica -Name Replica\_Exchange | Get-VBRRestorePoint -Name MSExchange02 | Sort-Object -Property CreationTime -Descending | Select -First 1 |  Perform the following steps:   1. Run the [Get-VBRReplica](get-vbrreplica.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Get-VBRRestorePoint cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value as the Property parameter value. Provide the Descending parameter. 4. Pipe the cmdlet output to the [Select](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Specify the First parameter value. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRReplica](get-vbrreplica.md)
* [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7)
* [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7)

Page updated 6/19/2024

Page content applies to build 13.0.1.1071
