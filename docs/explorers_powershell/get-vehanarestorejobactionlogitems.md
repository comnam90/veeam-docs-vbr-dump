---
title: "Get-VEHANARestoreJobActionLogItems"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vehanarestorejobactionlogitems.html"
last_updated: "7/29/2025"
product_version: "13.0.1.1071"
---

# Get-VEHANARestoreJobActionLogItems


Short Description

Returns action log items for a SAP HANA restore job.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEHANARestoreJobActionLogItems [-Session] <VEHANARestoreSession> -RestoreJob <VEHANARestore> [<CommonParameters>] |

Detailed Description

This cmdlet returns action log items for a specific SAP HANA restore job, giving you a detailed overview of the restore process.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the restore session in which the restore job was started. | Accepts the [VEHANARestoreSession](vehanarestoresession.md) object. To get this object, run the [Get-VEHANARestoreSession](get-vehanarestoresession.md) cmdlet. | True | 0 | True (ByValue) |
| RestoreJob | Specifies an SAP HANA restore job. The cmdlet will return information about the specified restore job. | Accepts the [VEHANARestore](vehanarestore.md) object. To get this object, run the [Get-VEHANADatabaseRestore](get-vehanadatabaserestore.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEHANARestoreActionLogItem](vehanarestoreactionlogitem.md)[]object that contains information about the SAP HANA restore job.

Example

Getting Action Log Items for Specific Restore Job

This example gets action log items for the specified restore job.

|  |
| --- |
| $session = Get-VEHANARestoreSession  $system = Get-VEHANASystem $session[0]  $database = (Get-VEHANADatabase $system)[0]  $restorejob = Start-VEHANADatabaseRestore -Database $database  Get-VEHANARestoreJobActionLogItems -Session $session -RestoreJob $restoreJob |

Perform the following steps:

1. Run the [Get-VEHANARestoreSession](get-vehanarestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.

1. Run the [Get-VEHANASystem](get-vehanasystem.md) cmdlet. Set the first restore session in the $session variable as the Session parameter value.
2. Run the [Get-VEHANADatabase](get-vehanadatabase.md) cmdlet and set the $system variable as the System parameter value. Select the necessary database returned by this command and save it to the $database variable. In our example, it is the first database in the array.
3. Run the [Start-VEHANADatabaseRestore](start-vehanadatabaserestore.md) cmdlet and set the $database variable as the Database parameter value. Save the result to the $restorejob variable.
4. Run the Get-VEHANARestoreJobActionLogItems cmdlet. Set the $session variable as the Session parameter value and set the $restorejob variable as the RestoreJob parameter value.

Related Commands

* [Get-VEHANARestoreSession](get-vehanarestoresession.md)
* [Get-VEHANASystem](get-vehanasystem.md)
* [Get-VEHANADatabase](get-vehanadatabase.md)
* [Start-VEHANADatabaseRestore](start-vehanadatabaserestore.md)


