---
title: "Get-VBRNASBackupFLRItem (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnasbackupflritem.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Get-VBRNASBackupFLRItem (obsolete)

In this article

Short Description

Returns backed-up objects created by file backup jobs.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Get-VBRUnstructuredBackupFLRItem](get-vbrunstructuredbackupflritem.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRNASBackupFLRItem -Session <VBRNASBackupFLRSession> [-Name <string>] [-Folder < VBRNASBackupFLRFolder>] [-ChangedOnly] [-Recurse]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backed-up objects created by file backup jobs. These objects contain settings of guest OS files and folders backed up by file backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies a restore session. The cmdlet will return  backed-up object within this restore session. | Accepts the VBRNASBackupFLRSession object. To get this object, run the [Get-VBRNASBackupFLRSession](get-vbrnasbackupflrsession.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Name | Specifies a name of the backed-up object. The cmdlet will return folders and files with the specified name.  Note: By default, the cmdlet returns up to 10,000 records (folders and files). You can change the default value with a registry key. For more information, contact Veeam Customer Support. | String | False | Named | False |
| Folder | Specifies a backed-up folder. The cmdlet will return the specified folder and an array of objects that are added to this folder. | Accepts the VBRNASBackupFLRFolder object. To get this object, run the Get-VBRNASBackupFLRItem cmdlet. | False | Named | False |
| ChangedOnly | Defines that the cmdlet will return files and folders with changed attributes only. | SwitchParamter | False | Named | False |
| Recurse | Defines that the cmdlet will look for objects that are added to backed-up child folders.  If you provide this parameter, the cmdlet will return an array of all objects that are added to backed-up child folders. Otherwise, the cmdlet will return an array of objects that are added to the parent folder on the backed-up file share. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRNASBackupFLRItem](vbrnasbackupflritem.md) and VBRNASBackupFLRFolder objects that contain settings of guest OS files and folders backed up by file backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Objects Within Restore Session

|  |  |
| --- | --- |
| This example shows how to get objects within the specified restore session.  |  | | --- | | $restorepoint = Get-VBRNASBackupRestorePoint  $session = Start-VBRNASBackupFLRSession -RestorePoint $restorepoint[3]  Get-VBRNASBackupFLRItem -Session $session |  Perform the following steps:   1. Run the [Get-VBRNASBackupRestorePoint](get-vbrnasbackuprestorepoint.md) cmdlet. Save the result to the $restorepoint variable.   The Get-VBRNASBackupRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (An array starts with 0. In our example, it is the fourth restore point in the array).   1. Run the [Start-VBRNASBackupFLRSession](start-vbrnasbackupflrsession.md) cmdlet. Set the $restorepoint as the RestorePoint parameter value. Save the result to the $session variable. 2. Run the Get-VBRNASBackupFLRItem cmdlet. Set the $session as the Session parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Objects by Name

|  |  |
| --- | --- |
| This example shows how to get the Report001.txt file within the specified restore session.  |  | | --- | | $restorepoint = Get-VBRNASBackupRestorePoint  $session = Start-VBRNASBackupFLRSession -RestorePoint $restorepoint[4]  Get-VBRNASBackupFLRItem -Session $session -Name "Report001.txt" |  Perform the following steps:   1. Run the [Get-VBRNASBackupRestorePoint](get-vbrnasbackuprestorepoint.md) cmdlet. Save the result to the $restorepoint variable.   The Get-VBRNASBackupRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the fifth restore point in the array). Note that to count objects of the array you must start with 0.   1. Run the [Start-VBRNASBackupFLRSession](start-vbrnasbackupflrsession.md) cmdlet. Set the $restorepoint as the RestorePoint parameter value. Save the result to the $session variable. 2. Run the Get-VBRNASBackupFLRItem cmdlet. Specify the Name parameter value. Set the $session as the Session parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Objects from Specific Folder

|  |  |
| --- | --- |
| This example shows how to get all objects that are located in the the October Reports folder.  |  | | --- | | $restorepoint = Get-VBRNASBackupRestorePoint  $session = Start-VBRNASBackupFLRSession -RestorePoint $restorepoint[2]  $folder = Get-VBRNASBackupFLRItem -Session $session -Name "October Reports"  Get-VBRNASBackupFLRItem -Session $session -Folder $folder |  Perform the following steps:   1. Run the [Get-VBRNASBackupRestorePoint](get-vbrnasbackuprestorepoint.md) cmdlet. Save the result to the $restorepoint variable.   The Get-VBRNASBackupRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the third restore point in the array). Note that to count objects of the array you must start with 0.   1. Run the [Start-VBRNASBackupFLRSession](start-vbrnasbackupflrsession.md) cmdlet. Set the $restorepoint as the RestorePoint parameter value. Save the result to the $session variable. 2. Run the Get-VBRNASBackupFLRItem cmdlet. Set the $session as the Session parameter value. Specify the Name parameter value. Save the result to the $folder variable. 3. Run the Get-VBRNASBackupFLRItem cmdlet. Set the $folder as the Folder parameter value. Set the $session as the Session parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting All Objects Added to Backed-up Folders

|  |  |
| --- | --- |
| This example shows how to get all objects that are added to the backed-up folders.  |  | | --- | | $restorepoint = Get-VBRNASBackupRestorePoint  $session = Start-VBRNASBackupFLRSession -RestorePoint $restorepoint[5]  Get-VBRNASBackupFLRItem -Session $session -Recurse |  Perform the following steps:   1. Run the [Get-VBRNASBackupRestorePoint](get-vbrnasbackuprestorepoint.md) cmdlet. Save the result to the $restorepoint variable.   The Get-VBRNASBackupRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the sixth restore point in the array). Note that to count objects of the array you must start with 0.   1. Run the [Start-VBRNASBackupFLRSession](start-vbrnasbackupflrsession.md) cmdlet. Set the $restorepoint as the RestorePoint parameter value. Save the result to the $session variable. 2. Run the Get-VBRNASBackupFLRItem cmdlet. Set the $session as the Session parameter value. Provide the Recurse parameter. |

Related Commands

* [Get-VBRNASBackupRestorePoint](get-vbrnasbackuprestorepoint.md)
* [Start-VBRNASBackupFLRSession](start-vbrnasbackupflrsession.md)

Page updated 1/6/2025

Page content applies to build 13.0.1.1071
