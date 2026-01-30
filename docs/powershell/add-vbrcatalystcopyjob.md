---
title: "Add-VBRCatalystCopyJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrcatalystcopyjob.html"
last_updated: "4/25/2024"
product_version: "13.0.1.1071"
---

# Add-VBRCatalystCopyJob


Short Description

Creates backup copy jobs for HPE StoreOnce repositories.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRCatalystCopyJob -Name <String> [-Description <String>] -SourceRepository <CBackupRepository[]> -TargetRepository <CBackupRepository[]> [-EnableHealthCheck] [-KeepSecondaryCopies] [-SecondaryCopiesRetentionPeriod <Int32>] [-NotificationOptions <VBRNotificationOptions>] [-ScriptOptions <VBRJobScriptOptions>] [-BackupWindowOptions <VBRBackupWindowOptions>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet creates backup copy jobs for HPE StoreOnce repositories.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name of a backup copy job. The cmdlet will create the copy job with this name. | String | True | 0 | False |
| SourceRepository | Specifies an array of source HPE StoreOnce repositories. The cmdlet will copy backup files from these repositories.  You can specify the following types of repositories:   * HPE StoreOnce repositories. * HPE StoreOnce repositories added as extents to a Scale-Out Backup Repository.   Note: The array of source repositories must contain the same number of the repositories as the array of the target repositories. | Accepts the string and the CBackupRepository[] object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| TargetRepository | Specifies an array of target HPE StoreOnce repositories. The cmdlet will copy backup files to these repositories.  You can specify the following types of repositories:   * HPE StoreOnce repositories. * HPE StoreOnce repositories added as extents to a Scale-Out Backup Repository.   Note: The array of target repositories must contain the same number of the repositories as the array of the source repositories. | Accepts the string and the CBackupRepository[] object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| Description | Specifies a description of a backup copy job. The cmdlet will create the backup copy job with this description. | String | False | Named | False |
| NotificationOptions | Specifies notification settings. The cmdlet will create the backup copy job with these settings. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| ScriptOptions | Specifies job scrip options. The cmdlet will create a copy job with these script options. | Accepts the VBRJobScriptOptions object. To create this object, run the [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) cmdlet. | False | Named | False |
| BackupWindowOptions | Specifies backup window settings for a job. The cmdlet will create the the backup copy job with these settings. | Accepts the VBRBackupWindowOptions object. To create this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |
| KeepSecondaryCopies | Defines that the cmdlet will enable retention policy for the backup files in the target location. | SwitchParameter | False | Named | False |
| SecondaryCopiesRetentionPeriod | Specifies a number of days for which you want to store backup files in the target location. | Int32 | False | Named | False |
| EnableHealthCheck | Defines that the cmdlet will enable the Health check option. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will create backup copy jobs without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCatalystCopyJob object that contains settings of backup copy jobs for HPE StoreOnce repositories.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Backup Copy Job for Specific HPE StoreOnce Repositories

|  |  |
| --- | --- |
| This example shows how to create a backup copy job that will copy data from the source HPE StoreOnce 1 repository to the target HPE StoreOnce 2 repository.  |  | | --- | | $source = Get-VBRBackupRepository -Name "HPE StoreOnce 1"  $target = Get-VBRBackupRepository -Name "HPE StoreOnce 2"  Add-VBRCatalystCopyJob -Name "StoreOnce copy job" -SourceRepository $source -TargetRepository $target -Description "Copy job for StoreOnce repository" |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $source variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $target variable. 3. Run the Add-VBRCatalystCopyJob cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $source variable as the SourceRepository parameter value. * Set the $target variable as the TargetRepository parameter value. * Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Backup Copy Job for List of HPE StoreOnce Repositories

|  |  |
| --- | --- |
| This example shows how to create a backup copy job that will copy data from a list of source repositories to a list of the target repositories. Veeam Backup & Replication will copy data according to the following scheme:   * From HPE StoreOnce 1 to HPE StoreOnce 4 * From HPE StoreOnce 2 to HPE StoreOnce 5 * From HPE StoreOnce 3 to HPE StoreOnce 6   |  | | --- | | $source = Get-VBRBackupRepository -Name "HPE StoreOnce 1", "HPE StoreOnce 2", "HPE StoreOnce 3"  $target = Get-VBRBackupRepository -Name "HPE StoreOnce 4", "HPE StoreOnce 5", "HPE StoreOnce 6"  Add-VBRCatalystCopyJob -Name "StoreOnce copy job" -SourceRepository $source -TargetRepository $target -Description "Copy job for StoreOnce repository" |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value.   Save the result to the $source variable. The [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet will return an array of source HPE StoreOnce repositories.   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $target variable.   The [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet will return an array of target HPE StoreOnce repositories.   1. Run the Add-VBRCatalystCopyJob cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $source variable as the SourceRepository parameter value. * Set the $target variable as the TargetRepository parameter value. * Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Creating Backup Copy Job for HPE StoreOnce Repository with Backup Window Options

|  |  |
| --- | --- |
| This example shows how to create a backup copy job for an HPE StoreOnce repository. The job will run during the following period of time:   * From 22:00 to 22:59 on Friday * From 22:00 to 22:59 on Saturday   |  | | --- | | $source = Get-VBRBackupRepository -Name "HPE SO 05"  $target = Get-VBRBackupRepository -Name "HPE SO 07"  $windowoptions = New-VBRBackupWindowOptions -FromDay Friday -FromHour 22 -ToDay Saturday -ToHour 22 -Enabled  Add-VBRCatalystCopyJob -Name "StoreOnce copy job" -SourceRepository $source -TargetRepository $target -Description "Copy job for StoreOnce repository" -BackupWindowOptions $windowoptions |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $source variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $target variable. 3. Run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. Specify the necessary parameters. Save the result to the $windowoptions variable. 4. Run the Add-VBRCatalystCopyJob cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $source variable as the SourceRepository parameter value. * Set the $target variable as the TargetRepository parameter value. * Specify the Description  parameter value. * Set the $windowoptions variable as the BackupWindowOptions parameter value. |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md)


