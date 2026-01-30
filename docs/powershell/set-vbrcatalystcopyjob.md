---
title: "Set-VBRCatalystCopyJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcatalystcopyjob.html"
last_updated: "4/25/2024"
product_version: "13.0.1.1071"
---

# Set-VBRCatalystCopyJob


Short Description

Modifies backup copy jobs for HPE StoreOnce repositories.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify backup copy jobs for HPE StoreOnce repositories with the custom job backup window settings.

|  |
| --- |
| Set-VBRCatalystCopyJob -Job <VBRCatalystCopyJob> [-Name <String>] [-Description <String>] [-SourceRepository <CBackupRepository[]>] [-TargetRepository <CBackupRepository[]>] [-EnableHealthCheck] [-KeepSecondaryCopies] [-SecondaryCopiesRetentionPeriod <Int32>] [-NotificationOptions <VBRNotificationOptions>] [-ScriptOptions <VBRJobScriptOptions>] [-BackupWindowOptions <VBRBackupWindowOptions>] [-Force]  [<CommonParameters>] |

* Modify backup copy jobs for HPE StoreOnce repositories with the continuous backup option.

|  |
| --- |
| Set-VBRCatalystCopyJob -Job <VBRCatalystCopyJob> [-Name <String>] [-Description <String>] [-SourceRepository <CBackupRepository[]>] [-TargetRepository <CBackupRepository[]>] [-EnableHealthCheck] [-KeepSecondaryCopies] [-SecondaryCopiesRetentionPeriod <Int32>] [-NotificationOptions <VBRNotificationOptions>] [-ScriptOptions <VBRJobScriptOptions>] [-AnyTime] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies backup copy jobs that are created for HPE StoreOnce repositories.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specify a backup copy job for an HPE StoreOnce repository. The cmdlet will modify the settings of this job. | Accepts the VBRCatalystCopyJob object. To get this object, run the [Get-VBRCatalystCopyJob](get-vbrcatalystcopyjob.md) cmdlet. | True | Named | True (ByValue) |
| Name | Specifies a name of a backup copy job. The cmdlet will create the backup copy job with this name. | String | False | Named | False |
| Description | Specifies a description of a backup copy job. The cmdlet will create the backup copy job with this description. | String | False | Named | False |
| SourceRepository | Specifies an array of source HPE StoreOnce repositories. The cmdlet will copy backup files from these repositories.  You can specify the following types of repositories:   * HPE StoreOnce repositories. * HPE StoreOnce repositories added as extents to a Scale-Out Backup Repository. | Accepts the string and the CBackupRepository[] object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| TargetRepository | Specifies an array of target HPE StoreOnce repositories. The cmdlet will copy backup files to these repositories.  You can specify the following types of repositories:   * HPE StoreOnce repositories. * HPE StoreOnce repositories added as extents to a Scale-Out Backup Repository. | Accepts the string and the CBackupRepository[] object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| NotificationOptions | Specifies notification settings. The cmdlet will create the backup copy job with these settings | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| ScriptOptions | Specifies job scrip options. The cmdlet will create a copy job with these script options. | Accepts the VBRJobScriptOptions object. To create this object, run the [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) cmdlet. | False | Named | False |
| BackupWindowOptions | Specifies backup window settings for a job. The cmdlet will create the the backup copy job with these settings. | Accepts the VBRBackupWindowOptions object. To create this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |
| AnyTime | Defines that Veeam Backup & Replication will run a backup job continuously. | SwitchParameter | False | Named | False |
| KeepSecondaryCopies | Defines that the cmdlet will enable retention policy for the backup files in the target location. | SwitchParameter | False | Named | False |
| SecondaryCopiesRetentionPeriod | Specifies a number of days for which you want to store backup files in the target location. | Int32 | False | Named | False |
| EnableHealthCheck | Defines that the cmdlet will enable the Health check option. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will modify backup copy jobs that are created for HPE StoreOnce repositories without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCatalystCopyJob object that contains settings of backup copy jobs for HPE StoreOnce repositories.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Backup Copy Job Schedule to Run at Specific Time

|  |  |
| --- | --- |
| This example shows how to modify backup window settings for a backup copy job. The backup copy job will run from 20:00 to 22:59 every day from Monday to Friday.  |  | | --- | | $job = Get-VBRCatalystCopyJob -Name "Backup Copy StoreOnce 05"  $windowoptions = New-VBRBackupWindowOptions -FromDay Monday -ToDay Friday -FromHour 20 -ToHour 22 -Enabled  Set-VBRCatalystCopyJob -Job $job -BackupWindowOptions $windowoptions |  Perform the following steps:   1. Run the [Get-VBRCatalystCopyJob](get-vbrcatalystcopyjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. Specify the necessary parameters. Save the result to the $windowoptions variable. 3. Run the Set-VBRCatalystCopyJob cmdlet. Set the $job variable as the Job parameter value. Set the $windowoptions variable as the BackupWindowOptions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Backup Copy Job Schedule to Run Continuously

|  |  |
| --- | --- |
| This example shows how to modify schedule settings for a backup copy job. The backup copy job will run continuously.  |  | | --- | | $job = Get-VBRCatalystCopyJob -Name "Backup Copy StoreOnce 05"  Set-VBRCatalystCopyJob -Job $job -BackupWindowOptions $windowoptions -AnyTime |  Perform the following steps:   1. Run the [Get-VBRCatalystCopyJob](get-vbrcatalystcopyjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Set-VBRCatalystCopyJob cmdlet. Set the $job variable as the Job parameter value. Set the $windowoptions variable as the BackupWindowOptions parameter value. Provide the AnyTime parameter. |

Related Commands

* [Get-VBRCatalystCopyJob](get-vbrcatalystcopyjob.md)
* [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md)


