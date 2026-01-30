---
title: "New-VBREntraIDUserCredentials"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrentraidusercredentials.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# New-VBREntraIDUserCredentials


Short Description

Defines an object that matches a Microsoft Entra ID user and a password.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBREntraIDUserCredentials -UserId <String> -Password <SecureString>  [<CommonParameters>] |

Detailed Description

This cmdlet defines an object that matches an Entra ID user and a password. This object is used for the user restore using the [Restore-VBREntraIDTenantItem](restore-vbrentraidtenantitem.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| UserId | Specifies the ID of a user to whom you want to assign the password during further restore. | String | True | Named | False |
| Password | Specifies a password. | SecureString | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBREntraIDUserCredentials](vbrentraidusercredentials.md) object that matches an Entra ID user and a password.

Examples

Matching Entra ID User with Password

This example shows how to match a user with a password.

|  |
| --- |
| $session = Get-VBREntraIDTenantRestoreSession -Id "901e32ac-4c9e-4f7a-9b36-a4fd0f7248fe"  $user = Get-VBREntraIDTenantItem -Backup $backup -Type User -Name "admin"  $passwords = (Generate-VBREntraIDTenantUserPassword -Session $session -PasswordCount 3) | ConvertTo-SecureString -AsPlainText -Force  $userPassword = New-VBREntraIDUserCredentials -UserId $user.Id -Password $passwords[0] |

Perform the following steps:

1. Run the [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md) cmdlet. Specify the Id parameter value. Save the result to the $session variable.
2. Run the [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md) cmdlet. Specify the following settings:

* Set the $backup variable as the Backup parameter value.
* Specify the Type and Name parameter values.
* Save the result to the $session variable.

1. Run the [Generate-VBREntraIDTenantUserPassword](generate-vbrentraidtenantuserpassword.md) cmdlet. Specify the following settings:

* Set the $session variable as the Session parameter value.

* Specify the PasswordCount parameter value.
* Convert the result to a secure string.

* Save the result to the $passwords variable.

1. Run the New-VBREntraIDUserCredentials cmdlet. Specify the following settings:

* Set the $user.Id variable as the UserId parameter value.
* Set the $passwords[0] variable as the Password parameter value.

* Save the result to the $userPassword variable.

Related Commands

* [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md)
* [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md)
* [Generate-VBREntraIDTenantUserPassword](generate-vbrentraidtenantuserpassword.md)


