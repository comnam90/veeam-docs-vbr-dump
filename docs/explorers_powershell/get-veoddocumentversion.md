---
title: "Get-VEODDocumentVersion"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veoddocumentversion.html"
last_updated: "3/12/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns other versions of a OneDrive document.

Applies to

Veeam Backup for Microsoft 365

Product Edition: Rental License, Subscription License

Syntax

|  |
| --- |
| Get-VEODDocumentVersion [-Document] <VBOOneDriveDocument> [<CommonParameters>] |

Detailed Description

This cmdlet returns other versions of a document stored in a OneDrive repository.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Document | Specifies OneDrive document. This cmdlet will return other versions of this document. | Accepts the [VBOOneDriveDocument](vboonedrivedocument.md) object. To get this object, run the [Get-VEODDocument](get-veoddocument.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VBOOneDriveDocument](vboonedrivedocument.md)[] array that contains other versions of the specified One Drive document.

Example

Getting Versions of OneDrive Document

This example shows how to get versions of the document.txt document.

|  |
| --- |
| $session = Get-VEODRestoreSession  $user = Get-VEODUser -Session $session -Name "userAlpha"  $document = Get-VEODDocument -User $user -Name "document.txt"  Get-VEODDocumentVersion -Document $document |

Perform the following steps:

1. Run the [Get-VEODRestoreSession](get-veodrestoresession.md) cmdlet. Save the result to the $session variable.
2. Run the [Get-VEODUser](get-veoduser.md) cmdlet. Set the $session variable as the Session parameter value. Specify the Name parameter value. Save the result to the $user variable.
3. Run the [Get-VEODDocument](get-veoddocument.md) cmdlet. Specify the $user variable as the User parameter value. Specify the Name parameter value. Save the result to the $document variable.
4. Run the Get-VEODDocumentVersion cmdlet. Set the $document variable as the Document parameter value.

Related Commands

* [Get-VEODRestoreSession](get-veodrestoresession.md)
* [Get-VEODUser](get-veoduser.md)
* [Get-VEODDocument](get-veoddocument.md)

Page updated 3/12/2025

Page content applies to build 13.0.1.1071
