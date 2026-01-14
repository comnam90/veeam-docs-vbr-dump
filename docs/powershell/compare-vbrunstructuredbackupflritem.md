---
title: "Compare-VBRUnstructuredBackupFLRItem"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/compare-vbrunstructuredbackupflritem.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Compare-VBRUnstructuredBackupFLRItem

In this article

Short Description

Compares backed-up objects with objects on production file share or object storage.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Compare-VBRUnstructuredBackupFLRItem -Item <VBRUnstructuredBackupFLRItem[]> -Session <VBRUnstructuredBackupFLRSession> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet compares backed-up objects with objects on production file share or object storage.

|  |
| --- |
| Important |
| The cmdlet compares only backup files recovered to a certain restore point. You can not compare all versions of backup files. To recover files to a certain restore point, run the [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md) cmdlet and provide the RestorePoint parameter. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Item | Specifies an array of backed-up objects that you want to compare with production file share or object storage. | Accepts the VBRUnstructuredBackupFLRItem[] object. To get this object, run the [Get-VBRUnstructuredBackupFLRItem](get-vbrunstructuredbackupflritem.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Session | Specifies restore sessions started to recover objects backed-up by file backup jobs and object storage backup jobs. The cmdlet will compare the objects restored within this session with objects on production file share or object storage. | Accepts the VBRUnstructuredBackupFLRSession object. To create this object, run the [Get-VBRUnstructuredBackupFLRSession](get-vbrunstructuredbackupflrsession.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUnstructuredBackupFLRItem object that contains compare state of backed-up objects with objects on production file share or object storage.

Examples

Comparing Backed-Up Objects with Objects on Production Object Storage

This example shows how to compare backed-up objects with objects on production object storage.

|  |
| --- |
| $restorepoint = Get-VBRUnstructuredBackupRestorePoint -ID "51e4eced-3fce-465b-b516-f24cb5a068a4"  $session = Start-VBRUnstructuredBackupFLRSession -RestorePoint $restorepoint[3]  $item = Get-VBRUnstructuredBackupFLRItem -Session $session  Compare-VBRUnstructuredBackupFLRItem -Item $item[0,1,4,5] -Session $session |

Perform the following steps:

1. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Specify the ID parameter value. Save the result to the $restorepoint variable.

The Get-VBRUnstructuredBackupRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the fourth restore point in the array).

1. Run the [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md) cmdlet. Specify the RestorePoint parameter value. Save the result to the $session variable.
2. Run the [Get-VBRUnstructuredBackupFLRItem](get-vbrunstructuredbackupflritem.md) cmdlet. Specify the Session parameter value. Save the result to the $item variable.
3. Run the Compare-VBRUnstructuredBackupFLRItem cmdlet. Set the $item[0,1,4,5] variable as the Item parameter value. Set the $session variable as the Session parameter value.

Related Commands

* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)
* [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md)
* [Get-VBRUnstructuredBackupFLRItem](get-vbrunstructuredbackupflritem.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
