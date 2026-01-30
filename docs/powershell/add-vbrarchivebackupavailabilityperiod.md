---
title: "Add-VBRArchiveBackupAvailabilityPeriod"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrarchivebackupavailabilityperiod.html"
last_updated: "6/18/2024"
product_version: "13.0.1.1071"
---

# Add-VBRArchiveBackupAvailabilityPeriod


Short Description

Extends the availability period of the backup files from the archive storage.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRArchiveBackupAvailabilityPeriod -RestorePoint <COib> -AvailabilityPeriodDays <uint32> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet extends the availability of the backup files retrieved from the archive extent of the scale-out backup repository.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point for which you want to extend the availability. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| AvailabilityPeriodDays | Specifies a period (in days) during which the retrieved archive backup files will be available. | Int32 | True | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRPublishedBackupSession object.

Examples

Retrieving Backup Files from Amazon S3 Glacier Archive Extent

This example shows how to extend the availability of the backup files retrieved from the archive extent of the scale-out backup repository.

|  |
| --- |
| $backup = Get-VBRBackup -Name "NEW\_YEAR\_JOB\_2"  $rp = Get-VBRRestorePoint -Backup $backup | sort creation\_time | select -First 1  Add-VBRArchiveBackupAvailabilityPeriod -RestorePoint $rp[0] -AvailabilityPeriodDays 2 |

Perform the following steps:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $rp variable.

The Get-VBRRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the first restore point in the array).

1. Run the Add-VBRArchiveBackupAvailabilityPeriod cmdlet. Set the $rp variable as the RestorePoint parameter value. Specify the AvailabilityPeriodDays parameter value.

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)


