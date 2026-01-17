---
title: "Save-VEODDocument"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/save-veoddocument.html"
last_updated: "3/12/2025"
product_version: "13.0.1.1071"
---

# Save-VEODDocument


Short Description

Saves OneDrive documents.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Rental License, Subscription License

Syntax

This cmdlet provides parameter sets that allow you to:

* Save a specific OneDrive document.

|  |
| --- |
| Save-VEODDocument [-Document] <VBOOneDriveDocument[]> [-Path] <String> [-AsZip] [<CommonParameters>] |

* Save documents of a specific OneDrive user.

|  |
| --- |
| Save-VEODDocument [-User] <VBOOneDriveUser> [-Path] <String> [-AsZip] [<CommonParameters>] |

* Save documents of the multiple OneDrive users.

|  |
| --- |
| Save-VEODDocument [-MultipleUsers] <VBOOneDriveUser[]> [-Path] <String> [-AsZip] [<CommonParameters>] |

Detailed Description

This cmdlet saves OneDrive documents.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Document | Specifies an array of OneDrive documents that you want to save. | Accepts the [VBOOneDriveDocument](vboonedrivedocument.md)[] object. To get this object, run the [Get-VEODDocument](get-veoddocument.md) cmdlet. | True | 0 | True (ByValue) |
| Path | Specifies a path to the folder. The cmdlet will save the OneDrive document to the specified path. | String | True | 1 | False |
| AsZip | Defines that the cmdlet will save the specified document as a ZIP archive.  Default: False | SwitchParameter | False | Named | False |
| User | Specifies OneDrive user. The cmdlet will will save documents of this user. | Accepts the [VBOOneDriveUser](vboonedriveuser.md) object. To get this object, run the [Get-VEODUser](get-veoduser.md) cmdlet. | True | 0 | True (ByValue) |
| MultipleUsers | Specifies an array of OneDrive users. The cmdlet will save documents of the specified users. | Accepts the [VBOOneDriveUser](vboonedriveuser.md)[] object. To get this object, run the [Get-VEODUser](get-veoduser.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Saving OneDrive Document of Specific User

|  |  |
| --- | --- |
| This example shows how to save all OneDrive documents of the userAlpha user to the ZIP archive file.  |  | | --- | | $session = Get-VEODRestoreSession  $user = Get-VEODUser -Session $session -Name "userAlpha"  Save-VEODDocument -User $user -Path "C:\Save\archive.zip" -AsZip |  Perform the following steps:   1. Run the [Get-VEODRestoreSession](get-veodrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEODUser](get-veoduser.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $user variable. 3. Run the Save-VEODDocument cmdlet. Set the $user variable as the User parameter value. Specify the Path parameter value. Provide the AsZip parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Saving Specific OneDrive Document

|  |  |
| --- | --- |
| This example shows how to save the document.txt OneDrive document from the userAlpha user.  |  | | --- | | $session = Get-VEODRestoreSession  $user = Get-VEODUser -Session $session -Name "userAlpha"  $document = Get-VEODDocument -User $user -Name "document.txt" -Recurse  Save-VEODDocument -Document $document -Path "C:\Save\archive.zip" -AsZip |  Perform the following steps:   1. Run the [Get-VEODRestoreSession](get-veodrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEODUser](get-veoduser.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $user variable. 3. Run the [Get-VEODDocument](get-veoddocument.md) cmdlet. Set the $user variable as the User parameter value. Specify the Name parameter value. Provide the Recurse parameter. Save the result to the $document variable. 4. Run the Save-VEODDocument cmdlet. Set the $document variable as the Document parameter value. Specify the Path parameter value. Provide the AsZip parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Saving Documents of Multiple OneDrive Users

|  |  |
| --- | --- |
| This example shows how to save OneDrive documents from multiple users.  |  | | --- | | $session = Get-VEODRestoreSession  $users = Get-VEODUser -Session $session  Save-VEODDocument -MultipleUsers $users -Path "C:\Save\archive.zip" -AsZip |  Perform the following steps:   1. Run the [Get-VEODRestoreSession](get-veodrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEODUser](get-veoduser.md) cmdlet. Set the $session variable as the Session parameter value. Save the result to the $users variable. 3. Run the Save-VEODDocument cmdlet. Set the $users variable as the MultipleUsers parameter value. Specify the Path parameter value. Provide the AsZip parameter. |

Related Commands

* [Get-VEODRestoreSession](get-veodrestoresession.md)
* [Get-VEODUser](get-veoduser.md)
* [Get-VEODDocument](get-veoddocument.md)


