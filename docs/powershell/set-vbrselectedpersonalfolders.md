---
title: "Set-VBRSelectedPersonalFolders"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrselectedpersonalfolders.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---

# Set-VBRSelectedPersonalFolders


Short Description

Modifies the scope of personal data for Agent Backup jobs that back up Microsoft Windows and Mac computers.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRSelectedPersonalFolders -SelectedPersonalFolders <VBRSelectedPersonalFolders> [-Desktop] [-Documents] [-Pictures] [-Video] [-Music] [-Favorites] [-Downloads] [-ApplicationData] [-Custom] [-Library] [-ExcludeRoamingUsers] [-ExcludeOneDrive] [<CommonParameters>] |

Detailed Description

This cmdlet modifies the scope of personal data for Veeam Agent Backup jobs that back up Microsoft Windows and Mac computers.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SelectedPersonalFolders | Specifies the scope of personal data that you want to modify. | Accepts the [VBRSelectedPersonalFolders](vbrselectedpersonalfolders.md) object. To create this object, run the [New-VBRSelectedPersonalFolders](new-vbrselectedpersonalfolders.md) cmdlet. | True | Named | True(ByValue) |
| Desktop | Defines that the cmdlet will include to the backup scope data stored in the Desktop folder on the system volume. | SwitchParameter | False | Named | False |
| Documents | Defines that the cmdlet will include to the backup scope data stored in the Documents folder on the system volume. | SwitchParameter | False | Named | False |
| Pictures | Defines that the cmdlet will include to the backup scope data stored in the Pictures folder on the system volume. | SwitchParameter | False | Named | False |
| Video | Defines that the cmdlet will include to the backup scope data stored in the following folders on the system volume:   * Video — for Microsoft Windows computers. * Movies — for Mac computers. | SwitchParameter | False | Named | False |
| Music | Defines that the cmdlet will include to the backup scope data stored in the Music folder on the system volume. | SwitchParameter | False | Named | False |
| Favorites | Defines that the cmdlet will include to the backup scope data stored in the Favorites folder on the system volume of Microsoft Windows computers. | SwitchParameter | False | Named | False |
| Downloads | Defines that the cmdlet will include to the backup scope data stored in the Downloads folder on the system volume. | SwitchParameter | False | Named | False |
| ApplicationData | Defines that the cmdlet will include to the backup scope application data stored on the system volume. | SwitchParameter | False | Named | False |
| Custom | Defines that the cmdlet will include to the backup scope data stored in the in custom locations on the system volume. | SwitchParameter | False | Named | False |
| Library | Defines that the cmdlet will include to the backup scope data stored in the Library folder on the system volume of Mac computers. | SwitchParameter | False | Named | False |
| ExcludeRoamingUsers | Excludes roaming user profiles from the backup scope on Microsoft Windows computers. If you do not provide this parameter, the cmdlet will include roaming user profiles to the backup scope. | SwitchParameter | False | Named | False |
| ExcludeOneDrive | Excludes data stored in the OneDrive folder from the backup scope on Microsoft Windows computers. If you do not provide this parameter, the cmdlet will include data stored in the OneDrive folder to the backup scope. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSelectedPersonalFolders](vbrselectedpersonalfolders.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Excluding Pictures Folder from Backup Scope

|  |  |
| --- | --- |
| This example shows how to exclude data stored in the Pictures folder from the backup scope.  |  | | --- | | $job = Get-VBRComputerBackupJob -Name 'Backup policy'  $selectedFilesOptions = $job.SelectedFilesOptions  $selectedPersonalFolders = $selectedFilesOptions.SelectedPersonalFolders  $newSelectedPersonalFolders = Set-VBRSelectedPersonalFolders -SelectedPersonalFolders $selectedPersonalFolders -Pictures:$False  $newSelectedFilesOptions = Set-VBRSelectedFilesBackupOptions -Options $selectedFilesOptions -SelectedPersonalFolders $newSelectedPersonalFolders  Set-VBRComputerBackupJob -Job $job -SelectedFilesOptions $newSelectedFilesOptions |  Perform the following steps:   1. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Get the SelectedFilesOptions property of the $job variable. Save the result to the $selectedFilesOptions variable. 3. Get the SelectedPersonalFolders property of the $selectedFilesOptions variable. Save the result to the $selectedPersonalFolders variable. 4. Run the Set-VBRSelectedPersonalFolders cmdlet. Set the $selectedPersonalFolders variable as the SelectedPersonalFolders parameter value. Set the False option for the Pictures parameter value. Save the result to the $newSelectedPersonalFolders variable. 5. Run the [Set-VBRSelectedFilesBackupOptions](set-vbrselectedfilesbackupoptions.md) cmdlet. Set the $selectedFilesOptions variable as the Options parameter value. Set the $newSelectedPersonalFolders variable as the SelectedPersonalFolders parameter value. Save the result to the $newSelectedFilesOptions variable. 6. Run the [Set-VBRComputerBackupJob](set-vbrcomputerbackupjob.md) cmdlet. Set the $job variable as the Job parameter value. Set the $newSelectedFilesOptions variable as the SelectedFilesOptions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Scope of Personal Data for Backup Jobs that Back Up Microsoft Windows Computers

|  |  |
| --- | --- |
| This example shows how to define the following settings for personal data scope:   * The cmdlet will include data stored in the Favorites and Downloads folders to the backup scope. * The cmdlet will exclude data stored in the OneDrive folder from the backup scope.   |  | | --- | | $folders = New-VBRSelectedPersonalFolders  Set-VBRSelectedPersonalFolders -SelectedPersonalFolders $folders -Favorites -Downloads -ExcludeOneDrive |  Perform the following steps:   1. Run the [New-VBRSelectedPersonalFolders](new-vbrselectedpersonalfolders.md) cmdlet. Save the result to the $folders variable. 2. Run the Set-VBRSelectedPersonalFolders cmdlet. Specify the following settings:  * Set the $folders variable as the SelectedPersonalFolders parameter value.  * Provide the Favorites parameter. * Provide the Downloads parameter. * Provide the ExcludeOneDrive parameter. |


