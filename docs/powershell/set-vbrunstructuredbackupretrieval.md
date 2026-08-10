---
title: "Set-VBRUnstructuredBackupRetrieval"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrunstructuredbackupretrieval.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Set-VBRUnstructuredBackupRetrieval


Short Description

Modifies the availability period of an active unstructured data retrieval operation.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRUnstructuredBackupRetrieval -AvailabilityPeriodDays <UInt32> -RetrievalOperation <VBRUnstructuredBackupColdStorageRetrievalOperation> [-RunAsync] [<CommonParameters>] |

Detailed Description

This cmdlet modifies the availability period of an active unstructured data retrieval operation.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| AvailabilityPeriodDays | Specifies a period in days during which the retrieved archive backup files will be available. | UInt32 | True | Named | False |
| RetrievalOperation | Specifies the active retrieval operation that you want to modify. | Accepts the VBRUnstructuredBackupColdStorageRetrievalOperation object. To get this object, run the [Get-VBRUnstructuredBackupColdStorageRetrieval](get-vbrunstructuredbackupretrieval.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Example

Modifying Active Data Retrieval Operation

This example shows how to modify the availability period of an active retrieval operation. The new availability period is set to 10 days.

|  |
| --- |
| $backup = Get-VBRUnstructuredBackup -Name "Compliance Archive" $retrieval = Get-VBRUnstructuredBackupColdStorageRetrieval -Backup $backup Set-VBRUnstructuredBackupRetrieval -RetrievalOperation $retrieval -AvailabilityPeriodDays 10 |

Perform the following steps:

1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the [Get-VBRUnstructuredBackupRetrieval](get-vbrunstructuredbackupretrieval.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $retrieval variable.
3. Run the Set-VBRUnstructuredBackupRetrieval cmdlet. Specify the following settings:

* Set the $retrieval variable as the RetrievalOperation parameter value.
* Set the AvailabilityPeriodDays parameter value to 10.

Related Commands

* [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md)
* [Get-VBRUnstructuredBackupColdStorageRetrieval](get-vbrunstructuredbackupretrieval.md)

Page updated 2026-06-29

