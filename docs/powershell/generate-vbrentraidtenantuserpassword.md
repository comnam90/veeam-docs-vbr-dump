---
title: "Generate-VBREntraIDTenantUserPassword"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/generate-vbrentraidtenantuserpassword.html"
last_updated: "1/30/2025"
product_version: "13.0.1.1071"
---

# Generate-VBREntraIDTenantUserPassword


Short Description

Creates passwords.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Generate-VBREntraIDTenantUserPassword -Session <VBREntraIDTenantRestoreSession> -PasswordCount <Int32>  [<CommonParameters>] |

Detailed Description

This cmdlet creates passwords that can further be used for the Entra ID restore session.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the restore session for which you want to create passwords. | Accepts the VBREntraIDTenantRestoreSession object. To create this object, run the [Start-VBREntraIDTenantRestore](start-vbrentraidtenantrestore.md) cmdlet. | True | Named | False |
| PasswordCount | Specifies how many passwords to generate. | Int32 | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the String[] object that contains the generated passwords.

Examples

Generating Passwords for Entra ID Restore Session

This example shows how to generate 3 passwords.

|  |
| --- |
| $session = Get-VBREntraIDTenantRestoreSession -Id "901e32ac-4c9e-4f7a-9b36-a4fd0f7248fe"  $passwords = Generate-VBREntraIDTenantUserPassword -Session $session -PasswordCount 3 |

Perform the following steps:

1. Run the [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md) cmdlet. Specify the Id parameter value. Save the result to the $session variable.
2. Run the Generate-VBREntraIDTenantUserPassword cmdlet. Specify the following settings:

* Set the $session variable as the Session parameter value.

* Specify the PasswordCount parameter value.

* Save the result to the $restorePoint variable.

Related Commands

[Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md)


