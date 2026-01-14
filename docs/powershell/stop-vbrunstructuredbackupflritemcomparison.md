---
title: "Stop-VBRUnstructuredBackupFLRItemComparison"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrunstructuredbackupflritemcomparison.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRUnstructuredBackupFLRItemComparison

In this article

Short Description

Stops sessions that are running to compare backed-up objects with objects on production file share or object storage.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRUnstructuredBackupFLRItemComparison -Item <VBRUnstructuredBackupFLRItem[]> -Session <VBRUnstructuredBackupFLRSession>  [<CommonParameters>] |

Detailed Description

This cmdlet stops sessions that are running to compare backed-up objects with objects on production file share or object storage.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Item | Specifies an array of backed-up objects. The cmdlet will stop compare session for these objects. | Accepts the VBRUnstructuredBackupFLRItem[] object. To get this object, run the [Get-VBRUnstructuredBackupFLRItem](get-vbrunstructuredbackupflritem.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Session | Specifies restore sessions started to recover objects backed-up by file backup jobs and object storage backup jobs. The cmdlet will stop the compare session for these objects. | Accepts the VBRUnstructuredBackupFLRSession object. To create this object, run the [Get-VBRUnstructuredBackupFLRSession](get-vbrunstructuredbackupflrsession.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Example

Stopping Session that Compare Backed-Up Objects with Objects on Production Object Storage

This example shows how to compare attributes of backed-up objects with of objects on production object storage.

|  |
| --- |
| $restorepoint = Get-VBRUnstructuredBackupRestorePoint -ID "51e4eced-3fce-465b-b516-f24cb5a068a4"  $session = Start-VBRUnstructuredBackupFLRSession -RestorePoint $restorepoint[3]  $item = Get-VBRUnstructuredBackupFLRItem -Session $session  Stop-VBRUnstructuredBackupFLRItemComparison -Item $item[0,1,4,5] -Session $session |

Perform the following steps:

1. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Specify the ID parameter value. Save the result to the $restorepoint variable.

The [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the fourth restore point in the array).

1. Run the [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md) cmdlet. Set the $restorepoint[3] variable as the RestorePoint parameter value. Save the result to the $session variable.
2. Run the [Get-VBRUnstructuredBackupFLRItem](get-vbrunstructuredbackupflritem.md) cmdlet. Set the $session variable as the Session parameter value. Save the result to the $item variable.
3. Run the Stop-VBRUnstructuredBackupFLRItemComparison cmdlet. Set the $item[0,1,4,5] variable as the Item parameter value. Set the $session variable as the Session parameter value.

Related Commands

* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)
* [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md)
* [Get-VBRUnstructuredBackupFLRItem](get-vbrunstructuredbackupflritem.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
