---
title: "Get-VEODDocument"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veoddocument.html"
last_updated: "3/25/2025"
product_version: "13.0.1.1071"
---

# Get-VEODDocument


Short Description

Returns OneDrive documents.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Community, Rental License, Subscription License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get documents of the specific user.

|  |
| --- |
| Get-VEODDocument [-User] <VBOOneDriveUser> [-Name <String[]>] [-Recurse] [<CommonParameters>] |

* Get all child documents of the specific document.

|  |
| --- |
| Get-VEODDocument [-ParentDocument] <VBOOneDriveDocument> [-Name <String[]>] [-Recurse] [<CommonParameters>] |

Detailed Description

This cmdlet returns documents that are stored in the OneDrive repository.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| User | Specifies OneDrive user. This cmdlet will return documents of the specified OneDrive user. | Accepts the [VBOOneDriveUser](vboonedriveuser.md) object. To get this object, run the [Get-VEODUser](get-veoduser.md) cmdlet. | True | 0 | True (ByValue) |
| Name | Specifies an array of document names. The cmdlet will return an array of documents with these names.  This parameter accepts wildcard characters. | String[] | False | Named | False |
| Recurse | Defines that the cmdlet will return all child items of the specified parent item.  Default: False | SwitchParameter | False | Named | False |
| ParentDocument | Specifies a parent document. The cmdlet will return the child documents of this parent document. | Accepts the [VBOOneDriveDocument](vboonedrivedocument.md) object. To get this object, run the Get-VEODDocument cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VBOOneDriveDocument](vboonedrivedocument.md) object that contains documents that are stored in the OneDrive repository.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Specified User Documents

|  |  |
| --- | --- |
| This example shows how to get the document.txt document and its child from the userAlpha user.  |  | | --- | | $session = Get-VEODRestoreSession  $user = Get-VEODUser -Session $session -Name "userAlpha"  Get-VEODDocument -User $user -Name "document.txt" -Recurse |  Perform the following steps:   1. Run the [Get-VEODRestoreSession](get-veodrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEODUser](get-veoduser.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $user variable. 3. Run the Get-VEODDocument cmdlet. Specify the following settings:  * Set the $user variable as the User parameter value. * Specify the Name parameter value. * Provide the Recurse parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Child Documents

|  |  |
| --- | --- |
| This example shows how to get child documents from the Document parent document.  |  | | --- | | $session = Get-VEODRestoreSession  $user = Get-VEODUser -Session $session -Name "userAlpha"  $document = Get-VEODDocument -User $user -Name "Document"  Get-VEODDocument -ParentDocument $document -Name "document.txt" -Recurse |  Perform the following steps:   1. Run the [Get-VEODRestoreSession](get-veodrestoresession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VEODUser](get-veoduser.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $user variable. 3. Run the Get-VEODDocument cmdlet. Specify the User and Name parameters. Save the result to the $document variable. 4. Run the Get-VEODDocument cmdlet. Specify the following settings:  * Set the $document variable as the ParentDocument parameter value. * Specify the Name parameter value. * Provide the Recurse parameter. |

Related Commands

* [Get-VEODRestoreSession](get-veodrestoresession.md)
* [Get-VEODUser](get-veoduser.md)


