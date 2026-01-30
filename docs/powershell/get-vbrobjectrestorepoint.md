---
title: "Get-VBRObjectRestorePoint"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrobjectrestorepoint.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRObjectRestorePoint


Short Description

Returns restore points created by jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get restore points for specific backups or replicas.

|  |
| --- |
| Get-VBRObjectRestorePoint -Backup <CBackup[]>  [<CommonParameters>] |

* Get restore points by their ID.

|  |
| --- |
| Get-VBRObjectRestorePoint -Id <Guid[]>  [<CommonParameters>] |

* Get restore points by their name.

|  |
| --- |
| Get-VBRObjectRestorePoint -Name <String[]>  [<CommonParameters>] |

* Get restore points ID of backed-up machines.

|  |
| --- |
| Get-VBRObjectRestorePoint -ObjectId <Guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns restore points created by jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies an array of backup or replica objects. The cmdlet will return restore points of these backups or replicas. | Accepts the CBackup[] object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) or [Get-VBRReplica](get-vbrreplica.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Id | Specifies an array of IDs, The cmdlet will return restore points of these backups or replicas. | String[] | True | Named | True (ByPropertyName, ByValue) |
| Name | Specifies an array of names for backed-up machines or replicated VMs. The cmdlet will return restore points of these machines.  Note: For Cloud Director and CDP replica you must specify a vApp. | String[] | True | Named | True (ByPropertyName, ByValue) |
| ObjectId | Specifies an array of IDs of backed-up hosts and machines. The cmdlet will return restore points of these hosts and machines. | Guid[] | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRObjectRestorePoint](vbrobjectrestorepoint.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Restore Points

|  |  |
| --- | --- |
| This command looks for all restore points of all machines registered in the database.  |  | | --- | | Get-VBRObjectRestorePoint | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Restore Points by ID

|  |  |
| --- | --- |
| This command looks for the 2ee79fec-9aa8-4058-a147-ff6b76ef2924 restore point.  |  | | --- | | Get-VBRObjectRestorePoint -Id "2ee79fec-9aa8-4058-a147-ff6b76ef2924" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Restore Points Created by Backup Job

|  |  |
| --- | --- |
| This example shows how to get all restore points of the MSExchange02 machine that is backed up by the MSExchange backup job.  |  | | --- | | $backup = Get-VBRBackup -Name "MSExchange"  Get-VBRObjectRestorePoint -Name \*MSExchange02\* -Backup $backup |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the Get-VBRObjectRestorePoint cmdlet. Specify the Name parameter value. Set the $backup variable as the Backup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Restore Points Created by Replication Job

|  |  |
| --- | --- |
| This example shows how to get all restore points of machines that are replicated by the DC Replica replication job.  |  | | --- | | $replica = Get-VBRReplica -Name "DC Replica"  Get-VBRObjectRestorePoint -Backup $replica |  Perform the following steps:   1. Run the [Get-VBRReplica](get-vbrreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable. 2. Run the Get-VBRObjectRestorePoint cmdlet. Set the $replica variable as the Backup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Getting Restore Points Created by Veeam Agent

|  |  |
| --- | --- |
| This example shows how to get all restore points of Windows-based machines backed up by the WinBackup Veeam Agent job.  |  | | --- | | $winbackup = Get-VBRBackup -Name "WinBackup\*"  Get-VBRObjectRestorePoint -Backup $winbackup |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $winbackup variable.   Note: To get a list of restore points for a Veeam Agent job, you must provide the asterisks sign for the Name parameter value: Name "AgentJob\*". Otherwise, the Get-VBRObjectRestorePoint cmdlet will not return any restore points for the Veeam Agent job.   1. Run the Get-VBRObjectRestorePoint cmdlet. Set the $winbackup variable as the Backup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 6. Getting Latest Restore Point Created by Backup Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to look for the latest restore point of machines that are backed up by the MSExchange Backup backup job.  |  | | --- | | Get-VBRBackup -Name MSExchange Backup | Get-VBRObjectRestorePoint -Name MSExchange02 | Sort-Object –Property CreationTime –Descending | Select-Object -First 1 |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Get-VBRObjectRestorePoint cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter. 4. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Set the 1 number as the First parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 7. Getting Latest Restore Point Created by Replication Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to return the latest restore point of the MSExchange02 machine that is replicated by the Replica\_Exchange replication job.  |  | | --- | | Get-VBRReplica -Name Replica\_Exchange | Get-VBRObjectRestorePoint -Name MSExchange02 | Sort-Object -Property CreationTime -Descending | Select -First 1 |  Perform the following steps:   1. Run the [Get-VBRReplica](get-vbrreplica.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Get-VBRObjectRestorePoint cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value as the Property parameter value. Provide the Descending parameter. 4. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Set the 1 number as the First parameter value. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRReplica](get-vbrreplica.md)
* [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7)
* [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7)


