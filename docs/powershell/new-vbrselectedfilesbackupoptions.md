---
title: "New-VBRSelectedFilesBackupOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrselectedfilesbackupoptions.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# New-VBRSelectedFilesBackupOptions

In this article

Short Description

Defines backup scope settings for Veeam Agent backup jobs.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRSelectedFilesBackupOptions -OSPlatform {Windows | Linux | Mac | Unix} [-BackupOS] [-BackupPersonalFiles] [-SelectedPersonalFolders <VBRSelectedPersonalFolders>] [-BackupSelectedFiles] [-SelectedFiles <string[]>] [-IncludeMask <string[]>] [-ExcludeMask <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a VBRSelectedFilesBackupOptions object that contains the backup scope settings. The backup scope includes individual folders and volumes that you want to back up.

For Veeam Agent jobs applied to Windows machines the backup scope may include:

* OS related data
* User profile folder with all settings and data
* Volumes or individual folders

For Veeam Agent jobs applied to Linux machines, the scope may include volumes or individual directories only.

|  |
| --- |
| Tip |
| For Windows machines you can use system environment variables to specify the backup scope and the exclude mask settings. You must type the backslash sign before the environment variable. For example: \%TEMP%, \%ProgramFiles% or \%WinDir%. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| OSPlatform | Specifies the OS of the protected machine:   * Windows: for Microsoft Windows machines. * Linux: for Linux machines. * Mac: for macOS machines. Note: Indexing for macOS machines is not supported in current version of Veeam PowerShell. * Unix: for Unix machines. | VBRAgentType | True | Named | False |
| BackupOS | Note: This option works only for Veeam Agent jobs that back up Windows machines.  Defines that Veeam Backup & Replication will include the OS related data into the backup scope. | SwitchParameter | False | Named | False |
| BackupPersonalFiles | Note: This option works only for Veeam Agent jobs that back up Windows machines.  Defines that Veeam Backup & Replication will include all user profile folders into the backup scope except for the roaming user profiles and data stored in the OneDrive folder. | SwitchParameter | False | Named | False |
| SelectedPersonalFolders | Defines the scope of personal data for Agent Backup jobs that back up Microsoft Windows machines.  Note: To use this setting, you must provide the BackupPersonalFiles parameter. | Accepts the [VBRSelectedPersonalFolders](vbrselectedpersonalfolders.md) object. To get this object, run the [New-VBRSelectedPersonalFolders](new-vbrselectedpersonalfolders.md) cmdlet. | False | Named | False |
| BackupSelectedFiles | Defines that Veeam Backup & Replication will include the following types of folders into the backup scope:   * Volumes * Individual folders on Windows machines * Directories on Linux machines * Directories on macOS machines * Directories on Unix machines   Use the SelectedFiles parameter to specify the backup scope. | SwitchParameter | False | Named | False |
| SelectedFiles | For the BackupSelectedFiles parameter.  Specifies the backup scope settings. To back up the folders, you must specify either of the following settings:   * Volume name * The path to the individual folder on Windows machines * The path to the directory on Linux machines  * Directories on macOS machines  * Directories on Unix machines | String[] | False | Named | False |
| IncludeMask | Specifies the file names and/or masks for file types that you want to include into the backup scope. | String[] | False | Named | False |
| ExcludeMask | Specifies files and directories that you want to exclude from the backup scope. You can specify the following types of files:   * File names * File masks for file types | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRSelectedFilesBackupOptions object that contains the backup scope settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Backup Scope Settings for Veeam Agent Job (Windows)

|  |  |
| --- | --- |
| This command creates the backup scope settings for the Veeam Agent job that backs up a Windows computer. The backup scope will include the user profile folders and settings.  |  | | --- | | New-VBRSelectedFilesBackupOptions -OSPlatform Windows -BackupPersonalFiles | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Backup Scope Settings with Selected Directory for Veeam Agent Job (Linux)

|  |  |
| --- | --- |
| This command creates the backup scope settings for the Veeam Agent job that backs up a Linux computer. The backup scope will include the files from the /home/administrator/mydir directory.  |  | | --- | | New-VBRSelectedFilesBackupOptions -OSPlatform Linux -BackupSelectedFiles -SelectedFiles "/home/administrator/mydir" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Creating Backup Scope Settings with OS Related Files for Veeam Agent Job (Windows)

|  |  |
| --- | --- |
| This command creates the backup scope settings for the Veeam Agent job that backs up a Windows computer. The backup scope will include OS related files and will exclude the temporary folder from the backup.  |  | | --- | | New-VBRSelectedFilesBackupOptions -OSPlatform Windows -BackupOS -ExcludeMask "\%Temp%" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Creating Backup Scope Settings with Excluded Files for Veeam Agent Job (Linux)

|  |  |
| --- | --- |
| This command creates the backup scope settings for the Veeam Agent job that backs up a Linux computer. The backup scope will include the files from the /home/user01/ directory and will exclude all files of the PDF format.  |  | | --- | | New-VBRSelectedFilesBackupOptions -OSPlatform Linux -BackupSelectedFiles -SelectedFiles "/home/user01/" -ExcludeMask '\*.pdf' | |

Page updated 2/12/2024

Page content applies to build 13.0.1.1071
