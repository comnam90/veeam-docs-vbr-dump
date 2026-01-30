---
title: "Set-VBRSelectedFilesBackupOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrselectedfilesbackupoptions.html"
last_updated: "5/6/2024"
product_version: "13.0.1.1071"
---

# Set-VBRSelectedFilesBackupOptions


Short Description

Modifies the backup scope settings for Veeam Agent backup jobs.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRSelectedFilesBackupOptions -Options <VBRSelectedFilesBackupOptions> [-BackupOS] [-BackupPersonalFiles] [-BackupSelectedFiles] [-SelectedPersonalFolders <VBRSelectedPersonalFolders>] [-SelectedFiles <string[]>] [-IncludeMask <string[]>] [-ExcludeMask <string[]>] [<CommonParameters>] |

Detailed Description

This cmdlet modifies the backup scope settings for Veeam Agent backup jobs.

|  |
| --- |
| Tip |
| For Windows machines you can use system environment variables to specify the backup scope and the exclude mask settings. You must type the backslash sign before the environment variable. For example: \%TEMP%, \%ProgramFiles% or \%WinDir%. |

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the file-level backup scope settings that you want to modify. | Accepts the VBRSelectedFilesBackupOptions object. To get this object, run the [New-VBRSelectedFilesBackupOptions](new-vbrselectedfilesbackupoptions.md) cmdlet. | True | Named | True (ByValue) |
| BackupOS | Note: This option works only for Veeam Agent jobs that back up Windows machines.  Defines that Veeam Backup & Replication will include the OS related data into the backup scope. | SwitchParameter | False | Named | False |
| BackupPersonalFiles | Note: This option works only for Veeam Agent jobs that back up Windows machines.  Defines that Veeam Backup & Replication will include all user profile folders into the backup scope except for the roaming user profiles and data stored in the OneDrive folder. | SwitchParameter | False | Named | False |
| BackupSelectedFiles | Defines that Veeam Backup & Replication will include the following types of folders into the backup scope:   * Volumes * Individual folders on Windows machines * Directories on Linux machines * Directories on macOS machines  * Directories on Unix machines   Use the SelectedFiles parameter to specify the backup scope. | SwitchParameter | False | Named | False |
| SelectedPersonalFolders | Defines the scope of personal data for Agent Backup jobs that back up Microsoft Windows machines.  Note: To use this setting, you must provide the BackupPersonalFiles parameter. | Accepts the [VBRSelectedPersonalFolders](vbrselectedpersonalfolders.md) object. To get this object, run the [New-VBRSelectedPersonalFolders](new-vbrselectedpersonalfolders.md) cmdlet. | False | Named | False |
| SelectedFiles | For the BackupSelectedFiles parameter.  Specifies the backup scope settings. To back up the folders, you must specify either of the following settings:   * Volume name * The path to the individual folder on Windows machines * The path to the directory on Linux machines  * Directories on macOS machines  * Directories on Unix machines | String[] | False | Named | False |
| IncludeMask | Specifies the file names and/or masks for file types that you want to include into the backup scope. | String[] | False | Named | False |
| ExcludeMask | Specifies the files that you want to exclude from the backup scope. You can specify the following types of files:   * File names * File masks for file types | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRSelectedFilesBackupOptions object that contains the backup scope settings.

Examples

Modifying Existing Backup Scope Settings for Windows Computer

This example shows how to modify the existing backup scope settings for a Windows computer.

|  |
| --- |
| $scope = New-VBRSelectedFilesBackupOptions -OSPlatform Windows -BackupPersonalFiles  Set-VBRSelectedFilesBackupOptions -Options $scope -BackupOS |

Perform the following steps:

1. Run the [New-VBRSelectedFilesBackupOptions](new-vbrselectedfilesbackupoptions.md) cmdlet. Set the Windows value for the OSPlatform parameter. Provide the BackupPersonalFiles parameter. Save the result to the $scope variable.
2. Run the Set-VBRSelectedFilesBackupOptions cmdlet. Set the $scope variable as the Options parameter value. Provide the BackupOS parameter.

Related Commands

[New-VBRSelectedFilesBackupOptions](new-vbrselectedfilesbackupoptions.md)


