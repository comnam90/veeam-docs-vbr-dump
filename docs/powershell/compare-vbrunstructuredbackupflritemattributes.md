---
title: "Compare-VBRUnstructuredBackupFLRItemAttributes"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/compare-vbrunstructuredbackupflritemattributes.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Compare-VBRUnstructuredBackupFLRItemAttributes

In this article

Short Description

Compares attributes of backed-up objects with objects on production file share or object storage.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Compare-VBRUnstructuredBackupFLRItemAttributes -Item <VBRUnstructuredBackupFLRItem[]> -Session <VBRUnstructuredBackupFLRSession>  [<CommonParameters>] |

Detailed Description

This cmdlet compares attributes of backed-up objects with objects on production file share or object storage.

|  |
| --- |
| Important |
| The cmdlet compares only backup files recovered to a certain restore point. You can not compare all versions of backup files. To recover files to a certain restore point, run the [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md) cmdlet and provide the RestorePoint parameter. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Item | Specifies an array of backed-up objects which attributes you want to compare with objects on production file share or object storage. | Accepts the VBRUnstructuredBackupFLRItem[] object. To get this object, run the [Get-VBRUnstructuredBackupFLRItem](get-vbrunstructuredbackupflritem.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Session | Specifies restore sessions started to recover objects backed-up by file backup jobs and object storage backup jobs. The cmdlet will compare attributes of the objects restored within this session with objects on production file share or object storage. | Accepts the VBRUnstructuredBackupFLRSession object. To create this object, run the [Get-VBRUnstructuredBackupFLRSession](get-vbrunstructuredbackupflrsession.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUnstructuredBackupFLRItemAttributes object that returns information on compare state and attributes of backed-up objects with objects on production file share or object storage.

Examples

Comparing Attributes of Backed-Up Objects with Attributes of Objects on Production Object Storage

This example shows how to compare attributes of backed-up objects with attributes of objects on production object storage.

|  |
| --- |
| $restorepoint = Get-VBRUnstructuredBackupRestorePoint -ID "51e4eced-3fce-465b-b516-f24cb5a068a4"  $session = Start-VBRUnstructuredBackupFLRSession -RestorePoint $restorepoint[3]  $item = Get-VBRUnstructuredBackupFLRItem -Session $session  Compare-VBRUnstructuredBackupFLRItemAttributes -Item $item[0,1,4,5] -Session $session |

Perform the following steps:

1. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Specify the ID parameter value. Save the result to the $restorepoint variable.

The Get-VBRUnstructuredBackupRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the fourth restore point in the array).

1. Run the [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md) cmdlet. Set the $restorepoint[3] variable as the RestorePoint parameter value. Save the result to the $session variable.
2. Run the [Get-VBRUnstructuredBackupFLRItem](get-vbrunstructuredbackupflritem.md) cmdlet. Set the $session variable as the Session parameter value. Save the result to the $item variable.
3. Run the Compare-VBRUnstructuredBackupFLRItemAttributes cmdlet. Set the $item[0,1,4,5] variable as the Item parameter value. Set the $session variable as the Session parameter value.

Related Commands

* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)
* [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md)
* [Get-VBRUnstructuredBackupFLRItem](get-vbrunstructuredbackupflritem.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
