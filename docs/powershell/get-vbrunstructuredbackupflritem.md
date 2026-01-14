---
title: "Get-VBRUnstructuredBackupFLRItem"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrunstructuredbackupflritem.html"
last_updated: "11/12/2024"
product_version: "13.0.1.1071"
---

# Get-VBRUnstructuredBackupFLRItem

In this article

Short Description

Returns backed-up objects created by file backup jobs or object storage backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRUnstructuredBackupFLRItem -Session <VBRUnstructuredBackupFLRSession> [-ChangedOnly] [-Folder <VBRUnstructuredBackupFLRFolder>] [-Name <String>] [-Recurse]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backed-up objects created by file backup jobs or object storage backup jobs. These objects contain settings of guest OS files and folders backed up by file backup jobs or object storage backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session. The cmdlet will return backed-up objects within this restore session. | Accepts the VBRUnstructuredBackupFLRSession object. To create this object, run the [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| ChangedOnly | Defines that the cmdlet will return backed-up objects with changed attributes only. | SwichParameter | False | Named | False |
| Name | Specifies a name of the backed-up object. The cmdlet will return folders and files with the specified name.  Note: By default, the cmdlet returns up to 10,000 records (folders and files). You can change the default value with a registry key. For more information, contact [Veeam Customer Support](https://www.veeam.com/de/support.html?ad=menu-support). | String | False | Named | False |
| Folder | Specifies a backed-up folder. The cmdlet will return the specified folder and an array of objects that are added to this folder. | Accepts the VBRUnstructuredBackupFLRFolder object. To get this object, run the Get-VBRUnstructuredBackupFLRItem cmdlet. | False | Named | False |
| Recurse | Defines that the cmdlet will look for objects that are added to backed-up child folders.  If you provide this parameter, the cmdlet will return an array of all objects that are added to backed-up child folders. Otherwise, the cmdlet will return an array of objects that are added to the parent folder on the backed-up file share or an object storage server. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUnstructuredBackupFLRItem objects that contain settings of guest OS files and folders backed up by file backup jobs or object storage backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Objects Within Restore Session

|  |  |
| --- | --- |
| This example shows how to get objects within the specified restore session.  |  | | --- | | $restorepoint = Get-VBRUnstructuredBackupRestorePoint  $session = Start-VBRUnstructuredBackupFLRSession -RestorePoint $restorepoint[3]  Get-VBRUnstructuredBackupFLRItem -Session $session |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Save the result to the $restorepoint variable.   The Get-VBRUnstructuredBackupRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point, for arrays it starts with 0. In our example, it is the fourth restore point in the array.   1. Run the [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable. 2. Run the Get-VBRUnstructuredBackupFLRItem cmdlet. Set the $session variable as the Session parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Objects by Name

|  |  |
| --- | --- |
| This example shows how to get the Report001.txt file within the specified restore session.  |  | | --- | | $restorepoint = Get-VBRUnstructuredBackupRestorePoint  $session = Start-VBRUnstructuredBackupFLRSession -RestorePoint $restorepoint[4]  Get-VBRUnstructuredBackupFLRItem -Session $session -Name "Report001.txt" |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Save the result to the $restorepoint variable.   The Get-VBRUnstructuredBackupRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point, for arrays it starts with 0. In our example, it is the fifth restore point in the array.   1. Run the [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable. 2. Run the Get-VBRUnstructuredBackupFLRItem cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Objects from Specific Folder

|  |  |
| --- | --- |
| This example shows how to get all objects that are located in the the October Reports folder.  |  | | --- | | $restorepoint = Get-VBRUnstructuredBackupRestorePoint  $session = Start-VBRUnstructuredBackupFLRSession -RestorePoint $restorepoint[2]  $folder =Get-VBRUnstructuredBackupFLRItem -Session $session -Name "October Reports"  Get-VBRUnstructuredBackupFLRItem -Session $session -Folder $folder |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Save the result to the $restorepoint variable.   The Get-VBRUnstructuredBackupRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point, for arrays it starts with 0. In our example, it is the third restore point in the array.   1. Run the [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable. 2. Run the Get-VBRUnstructuredBackupFLRItem cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. 3. Run the Get-VBRUnstructuredBackupFLRItem cmdlet. Set the $session variable as the Session parameter value. Set the $folder variable as the Folder parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting All Objects Added to Backed-up Folders

|  |  |
| --- | --- |
| This example shows how to get all objects that are added to the backed-up folders.  |  | | --- | | $restorepoint = Get-VBRUnstructuredBackupRestorePoint  $session = Start-VBRUnstructuredBackupFLRSession -RestorePoint $restorepoint[5]  Get-VBRUnstructuredBackupFLRItem -Session $session -Recurse |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Save the result to the $restorepoint variable.   The Get-VBRUnstructuredBackupRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point, for arrays it starts with 0. In our example, it is the sixth restore point in the array.   1. Run the [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable. 2. Run the Get-VBRUnstructuredBackupFLRItem cmdlet. Set the $session variable as the Session parameter value. Provide the Recurse parameter. |

Related Commands

* [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md)
* [Start-VBRUnstructuredBackupFLRSession](start-vbrunstructuredbackupflrsession.md)

Page updated 11/12/2024

Page content applies to build 13.0.1.1071
