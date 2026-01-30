---
title: "Forget-VBRCloudUnavailableBackupFile"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/forget-vbrcloudunavailablebackupfile.html"
last_updated: "2/29/2024"
product_version: "13.0.1.1071"
---

# Forget-VBRCloudUnavailableBackupFile


Short Description

Removes backup files, that are no longer available, from a cloud repository.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Forget-VBRCloudUnavailableBackupFile -BackupFiles <VBRCloudUnavailableBackupFile[]> [-IncludeDependentFiles]  [<CommonParameters>] |

Detailed Description

This cmdlet removes backup files, that are no longer available, from a cloud repository.

|  |
| --- |
| Note |
| Any restore points on a repository or extent that is inaccessible, on in Maintenance mode, will be considered as unavailable. Before you remove these backup files, check the list of the files that the [Get-VBRCloudUnavailableBackupFile](get-vbrcloudunavailablebackupfile.md) cmdlet returns to ensure the correct files will be removed. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| BackupFiles | Specifies backup files that you want to remove. | Accepts the VBRCloudUnavailableBackupFile[] object. To create this object, run the [Get-VBRCloudUnavailableBackupFile](get-vbrcloudunavailablebackupfile.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| IncludeDependentFiles | Defines that the cmdlet will remove incremental backup files that are related to the full backup files. If you do not provide this parameter, the cmdlet will not remove full backup files and incremental backup files that are related to these full backup files.  Note: If full backup files that you want to remove do not have incremental backup files, the cmdlet will remove these full backup files even if you do not provide the IncludeDependentFiles parameter. | SwitchParameter | False | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Unavailable Backup Files from Cloud Repository

This example shows how to remove backup files that are no longer available from a cloud repository for the ABC Company cloud tenant account. The cmdlet will remove incremental files as well.

|  |
| --- |
| $tenant = Get-VBRCloudTenant -Name "ABC Company"  $backupfiles = Get-VBRCloudUnavailableBackupFile -CloudTenant $tenant  Forget-VBRCloudUnavailableBackupFile -BackupFiles $backupfiles |

Perform the following steps:

1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable.
2. Run the [Get-VBRCloudUnavailableBackupFile](get-vbrcloudunavailablebackupfile.md) cmdlet. Set the $tenant variable as the CloudTenant parameter value. Save the result to the $backupfiles variable.
3. Run the Forget-VBRCloudUnavailableBackupFile cmdlet. Set the $backupfiles variable as the BackupFiles parameter value.

Related Commands

* [Get-VBRCloudTenant](get-vbrcloudtenant.md)
* [Get-VBRCloudUnavailableBackupFile](get-vbrcloudunavailablebackupfile.md)


