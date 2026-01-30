---
title: "Restore-VBREntraIDTenantItem"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/restore-vbrentraidtenantitem.html"
last_updated: "7/28/2025"
product_version: "13.0.1.1071"
---

# Restore-VBREntraIDTenantItem


Short Description

Restores a Microsoft Entra ID item.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Restore-VBREntraIDTenantItem -Session <VBREntraIDTenantRestoreSession> [-CredentialsId <Guid>] -Items <VBREntraIDTenantItem[]> [-RequestPasswordChangeOnLogon] [-SkipObjectsIfExist] [-SkipRecycleBinRestore] [-SkipRelationships] -RestorePoint <VBREntraIDTenantRestorePoint> [-DefaultUserPassword <SecureString>] [-UserCredentials <VBREntraIDUserCredentials[]>] [-Reason <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet restores Entra ID items from a tenant backup. The items can be users, groups, roles, administrative units or applications.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the restore session started to recover items backed-up by a tenant backup job. | Accepts the VBREntraIDTenantRestoreSession object. To create this object, run the [Start-VBREntraIDTenantRestore](start-vbrentraidtenantrestore.md) cmdlet. | True | Named | False |
| Items | Specifies an array of Entra ID items that you want to restore. | Accepts the VBREntraIDTenantItem[] object. To get this object, run the [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md) cmdlet. | True | Named | False |
| RestorePoint | Specifies a restore point from which you want to restore Entra ID items. | Accepts the VBREntraIDTenantRestorePoint object. To get this object, run the [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md) cmdlet. | True | Named | False |
| CredentialsId | Used only if you requested login using the [Request-VBREntraIDLogin](request-vbrentraidlogin.md) cmdlet.  Specifies the ID of the login session. Set the parameter value to the value returned by the [Request-VBREntraIDLogin](request-vbrentraidlogin.md) cmdlet. | Guid | False | Named | False |
| RequestPasswordChangeOnLogon | For user restore.  Defines if the restored users must change their passwords on the first logon.  Default: False. | SwitchParameter | False | Named | False |
| SkipObjectsIfExist | Defines if the items existing in the production site must be skipped from restore. | SwitchParameter | False | Named | False |
| SkipRecycleBinRestore | Defines if all the items must be restored from backup.  If this parameter is set to True, the cmdlet will restore all items from the backup. Otherwise, if an item exists in the recycle bin, it will be restored from the bin. | SwitchParameter | False | Named | False |
| SkipRelationships | Defines if to skip item relationships from restore. | SwitchParameter | False | Named | False |
| DefaultUserPassword | For user restore.  Specifies the default password for the users being restored.  Note: When restoring a user, you must specify this parameter or UserCredentials. | SecureString | False | Named | False |
| UserCredentials | For user restore.  Specifies an array of passwords for users being restored.  Note: When restoring a user, you must specify this parameter or DefaultUserPassword. | Accepts the VBREntraIDUserCredentials[] object. To create this object, run the [New-VBREntraIDUserCredentials](new-vbrentraidusercredentials.md) cmdlet. | False | Named | False |
| Reason | Specifies the reason of the restore operation. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

Guid.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring User

|  |  |
| --- | --- |
| This example shows how to restore a user and assign new credentials to them. The user will need to change the password on the first logon.  |  | | --- | | $tenantRestoreSession = Get-VBREntraIDTenantRestoreSession -Id "901e32ac-4c9e-4f7a-9b36-a4fd0f7248fe"  $backup = Get-VBREntraIDTenantBackup -Name "Tenant backup"  $restorePoint = Get-VBREntraIDTenantRestorePoint -Backup $backup -Id "a66808bc-780e-46f2-8538-63ace3c8f9be"  $item = Get-VBREntraIDTenantItem -Backup $backup -Type User -Name "Test Admin"  $password = (Generate-VBREntraIDTenantUserPassword -Session $tenantRestoreSession -PasswordCount 1) | ConvertTo-SecureString -AsPlainText -Force  $userPassword = New-VBREntraIDUserCredentials -UserId $item.Id -Password $password  $itemRestoreSessionId = Restore-VBREntraIDTenantItem -Session $tenantRestoreSession -Items $item -RestorePoint $restorePoint -RequestPasswordChangeOnLogon -UserCredentials $userPassword |  Perform the following steps:   1. Run the [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md) cmdlet. Specify the Id parameter value. Save the result to the $tenantRestoreSession variable. 2. Run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 3. Run the [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Id parameter value. Save the result to the $restorePoint variable. 4. Run the [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Type and Name parameter values. Save the result to the $item variable. 5. Run the [Generate-VBREntraIDTenantUserPassword](generate-vbrentraidtenantuserpassword.md) cmdlet. Specify the following settings:  * Set the $session variable as the Session parameter value.  * Specify the PasswordCount parameter value. * Convert the result to a secure string.  * Save the result to the $password variable.  1. Run the [New-VBREntraIDUserCredentials](new-vbrentraidusercredentials.md) cmdlet. Set the $item.Id variable as the UserId parameter value. Set the $password variable as the Password parameter value. Save the result to the $userPassword variable. 2. Run the Restore-VBREntraIDTenantItem cmdlet. Specify the following settings:  * Set the $tenantRestoreSession variable as the Session parameter value. * Set the $item variable as the Items parameter value. * Set the $restorePoint variable as the RestorePoint parameter value.  * Provide the RequestPasswordChangeOnLogon parameter.  * Set the $userPassword variable as the UserCredentials parameter value.  * Save the result to the $itemRestoreSessionId variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Groups

|  |  |
| --- | --- |
| This example shows how to restore groups whose names start with "grp".  |  | | --- | | $tenantRestoreSession = Get-VBREntraIDTenantRestoreSession -Id "901e32ac-4c9e-4f7a-9b36-a4fd0f7248fe"  $backup = Get-VBREntraIDTenantBackup -Name "Tenant backup"  $restorePoint = Get-VBREntraIDTenantRestorePoint -Backup $backup -Id "a66808bc-780e-46f2-8538-63ace3c8f9be"  $groups = Get-VBREntraIDTenantItem -Backup $backup -Type Group -Name "grp\*"  $itemRestoreSessionId = Restore-VBREntraIDTenantItem -Session $tenantRestoreSession -Items $groups -RestorePoint $restorePoint |  Perform the following steps:   1. Run the [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md) cmdlet. Specify the Id parameter value. Save the result to the $tenantRestoreSession variable. 2. Run the [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 3. Run the [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Id parameter value. Save the result to the $restorePoint variable. 4. Run the [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Type and Name parameter values. Save the result to the $groups variable. 5. Run the Restore-VBREntraIDTenantItem cmdlet. Specify the following settings:  * Set the $tenantRestoreSession variable as the Session parameter value. * Set the $groups variable as the Items parameter value. * Set the $restorePoint variable as the RestorePoint parameter value.  * Save the result to the $itemRestoreSessionId variable. |

Related Commands

* [Get-VBREntraIDTenantRestoreSession](get-vbrentraidtenantrestoresession.md)
* [Get-VBREntraIDTenantBackup](get-vbrentraidtenantbackup.md)
* [Get-VBREntraIDTenantRestorePoint](get-vbrentraidtenantrestorepoint.md)
* [Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md)
* [Generate-VBREntraIDTenantUserPassword](generate-vbrentraidtenantuserpassword.md)
* [New-VBREntraIDUserCredentials](new-vbrentraidusercredentials.md)


