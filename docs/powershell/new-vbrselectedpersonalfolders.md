---
title: "New-VBRSelectedPersonalFolders"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrselectedpersonalfolders.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---

# New-VBRSelectedPersonalFolders


Short Description

Defines the scope of personal data for Agent Backup jobs that back up Microsoft Windows and Mac computers.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRSelectedPersonalFolders [-Desktop] [-Documents] [-Pictures] [-Video] [-Music] [-Favorites] [-Downloads] [-ApplicationData] [-Custom] [-Library] [-ExcludeRoamingUsers] [-ExcludeOneDrive] [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRSelectedPersonalFolders](vbrselectedpersonalfolders.md) object that specifies the scope of personal data for Agent Backup jobs that back up Microsoft Windows and Mac computers.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
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

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Including Desktop Folder in Backup Scope

|  |  |
| --- | --- |
| This command includes to the backup scope data stored in the Desktop folder on the system volume. Save the result to the $folders variable.  |  | | --- | | $folders = New-VBRSelectedPersonalFolders -Desktop | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Including Pictures Folder in Backup Scope

|  |  |
| --- | --- |
| This command includes to the backup scope data stored in the Pictures folder on the system volume. Save the result to the $folders variable.  |  | | --- | | $folders = New-VBRSelectedPersonalFolders -Pictures | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Excluding Roaming User Profiles from Backup Scope

|  |  |
| --- | --- |
| This command excludes roaming user profiles from the backup scope. Save the result to the $folders variable.  |  | | --- | | $folders = New-VBRSelectedPersonalFolders -ExcludeRoamingUsers | |


