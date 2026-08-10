---
title: "Get-VBRUnstructuredBackupRetrieval"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrunstructuredbackupretrieval.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VBRUnstructuredBackupRetrieval


Short Description

Returns active unstructured data retrieval operations.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Return active unstructured data retrieval operations for specific backups.

|  |
| --- |
| Get-VBRUnstructuredBackupRetrieval -Backup <VBRUnstructuredBackup[]> [-Server <VBRUnstructuredServer[]>] [<CommonParameters>] |

* Return active unstructured data retrieval operations for specific restore points.

|  |
| --- |
| Get-VBRUnstructuredBackupRetrieval -RestorePoint <VBRUnstructuredBackupRestorePoint[]> [<CommonParameters>] |

Detailed Description

This cmdlet returns active unstructured data retrieval operations from archive object storage repositories.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Backup | Specifies an array of backups created by unstructured data backup jobs. The cmdlet will return active retrieval operations for these backups. | Accepts the VBRUnstructuredBackup[] object. To get this object, run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| RestorePoint | Specifies an array of restore points created by unstructured data backup jobs. The cmdlet will return active retrieval operations for these restore points. | Accepts the VBRUnstructuredBackupRestorePoint[] object. To get this object, run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. | True | Named | False |
| Server | Specifies an array of source servers that store unstructured data.  Note: Using this parameter together with the Backup parameter allows you to narrow down the list of active retrieval operations to those associated with the specified servers. | Accepts the VBRUnstructuredServer[] object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRUnstructuredBackupRetrievalOperation object that contains information about an active unstructured data retrieval operation.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Active Retrieval Operations for Backups

|  |  |
| --- | --- |
| This example shows how to get active retrieval operations for backups created by the Backup01 job.  |  | | --- | | $backup = Get-VBRUnstructuredBackup -Name "Backup01" Get-VBRUnstructuredBackupRetrieval -Backup $backup |  Perform the following steps:   1. Run the Get-VBRUnstructuredBackup cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the Get-VBRUnstructuredBackupRetrieval cmdlet. Set the $backup variable as the Backup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Active Retrieval Operations for Restore Points

|  |  |
| --- | --- |
| This example shows how to get active retrieval operations for restore points with the 8e9b3c1a-4d5f-4a2b-9c8d-7e6f5a4b3c2d ID.  |  | | --- | | $restorepoint = Get-VBRUnstructuredBackupRestorePoint -Id "8e9b3c1a-4d5f-4a2b-9c8d-7e6f5a4b3c2d" Get-VBRUnstructuredBackupRetrieval -RestorePoint $restorepoint |  Perform the following steps:   1. Run the Get-VBRUnstructuredBackupRestorePoint cmdlet. Specify the Id parameter value. Save the result to the $restorepoint variable. 2. Run the Get-VBRUnstructuredBackupRetrieval cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. |

Related Commands

* [Get-VBRObjectStorageRepository](get-vbrobjectstoragerepository.md)
* [Set-VBRNASObjectStorageTransformThreshold](set-vbrnasobjectstoragetransformthreshold.md)

Page updated 2026-06-29

