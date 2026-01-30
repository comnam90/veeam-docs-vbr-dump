---
title: "Get-VBREntraIDTenantItemRestoreSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrentraidtenantitemrestoresession.html"
last_updated: "1/9/2025"
product_version: "13.0.1.1071"
---

# Get-VBREntraIDTenantItemRestoreSession


Short Description

Returns a restore session launched for the item or attribute restore.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBREntraIDTenantItemRestoreSession -Id <Guid> -ParentSession <VBREntraIDTenantRestoreSession>  [<CommonParameters>] |

Detailed Description

This cmdlet returns a restore session launched for the item or attribute restore.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies the ID of the session that you want to get. | Guid | True | Named | False |
| ParentSession | Specifies the parent restore session that was launched to start restore. | Accepts the VBREntraIDTenantRestoreSession object. To create this object, run the [Start-VBREntraIDTenantRestore](start-vbrentraidtenantrestore.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBREntraIDTenantItemRestoreSession](vbrentraidtenantitemrestoresession.md) object that contains settings of an item or attribute restore session.

Examples

Getting Item Restore Session

This example shows how to get an item restore session.

|  |
| --- |
| $tenantRestoreSession = Get-VBREntraIDTenantRestoreSession -Id "901e32ac-4c9e-4f7a-9b36-a4fd0f7248fe"  $backup = Get-VBREntraIDTenantBackup -Name "Tenant backup"  $restorePoint = Get-VBREntraIDTenantRestorePoint -Backup $backup -Id "a66808bc-780e-46f2-8538-63ace3c8f9be"  $item = Get-VBREntraIDTenantItem -Backup $backup -Type User -Name "Test Admin"  $defaultPsswd = Read-Host -Prompt "Enter password" -AsSecureString  $itemRestoreSessionId = Restore-VBREntraIDTenantItem -Session $tenantRestoreSession -Items $item -RestorePoint $restorePoint -DefaultUserPassword $defaultPsswd  $session = Get-VBREntraIDTenantItemRestoreSession -Id $itemRestoreSessionId -ParentSession $tenantRestoreSession |

Perform the following steps:

1. Run the [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md) cmdlet. Specify the Id parameter value. Save the result to the $tenantRestoreSession variable.
2. Run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
3. Run the [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Id parameter value. Save the result to the $restorePoint variable.
4. Run the [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Type and Name parameter value. Save the result to the $item variable.
5. Create the $defaultPsswd variable. Use the Read-Host cmdlet to get the application secret and convert it to a secure string.
6. Run the [Restore-VBREntraIDTenantItem](restore-vbrentraidtenantitem.md) cmdlet. Specify the following settings:

* Set the $tenantRestoreSession variable as the Session parameter value.
* Set the $item variable as the Items parameter value.
* Set the $restorePoint variable as the RestorePoint parameter value.
* Set the $defaultPsswd variable as the DefaultUserPassword parameter value.

* Save the result to the $itemRestoreSessionId variable.

1. Run the Get-VBREntraIDTenantItemRestoreSession cmdlet. Specify the following settings:

* Set the $itemRestoreSessionId variable as the Id parameter value.
* Set the $tenantRestoreSession variable as the ParentSession parameter value.

* Save the result to the $session variable.

Related Commands

* [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md)
* [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md)
* [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md)
* [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md)
* [Restore-VBREntraIDTenantItem](restore-vbrentraidtenantitem.md)


