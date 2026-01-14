---
title: "Set-VBREPPermission"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbreppermission.html"
last_updated: "6/6/2024"
product_version: "13.0.1.1071"
---

# Set-VBREPPermission

In this article

Short Description

Applies user access permissions to backup repositories used by Veeam Agent or Veeam Plug-in operating in the standalone mode.

Syntax

|  |
| --- |
| Set-VBREPPermission -Repository <CBackupRepository> [-Type <VBREPPermissionType> {Everyone | NoOne | OnlySelectedUsers}] [-User <String[]>] [-EnableEncryption] [-EncryptionKey <VBREncryptionKey>] [-KMSServer <VBRKMSServer>] [-PassThru] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet applies user access permissions to a selected repository that is used as a target by Veeam Agent or Veeam Plug-in operating in the standalone mode.

By default, the backup repositories are configured to have no permissions for writing backups created by Veeam Agent or Veeam Plug-in operating in the standalone mode. To start using a Veeam backup repository as a target, you need to change the access permissions to Everyone or OnlySelectedUsers.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies the repository for which you want to set permissions.  Note: You cannot set permissions for Veeam Cloud Connect repositories. | Accepts string (repository name) or the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Type | Specifies the permission type:   * Everyone: everyone has permissions. * NoOne: no one has permissions. * OnlySelectedUsers: the selected users have permissions. Use the User parameter to specify the users.   Default: the permissions type that is currently set for the selected repository. | VBREPPermissionType | False | Named | False |
| User | Used to set users for OnlySelectedUsers option.  Specifies names of users allowed to use the repository.  You can specify user names or names of Active Directory groups. | String[] | False | Named | False |
| EnableEncryption | Enables the option to encrypt the backups created by Veeam Agent or Veeam Backup for Nutanix AHV.  Use the EncryptionKey parameter to specify the encryption key.  Note: Do not enable the encryption option if you back up your data with Veeam Plug-in. Veeam Plug-ins cannot send backups to a backup repository where encryption is enabled. | SwitchParameter | False | Named | False |
| EncryptionKey | Used to specify the encryption key for the EnableEncryption parameter. | Accepts the [VBREncryptionKey](pscryptokey.md) object. To get this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will apply access permissions to a repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| KMSServer | Specifies KMS servers added to the Veeam Backup & Replication console. The cmdlet will decrypt data encrypted by this server. | Accepts the [VBRKMSServer](vbrkmsserver.md) object. To get this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBREPPermission](vbreppermission.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Granting Repository Permissions to Administrator

|  |  |
| --- | --- |
| This example shows how to grant permission to access the WinLocal repository to Administrator.  |  | | --- | | $repository = Get-VBRBackupRepository -Name "WinLocal"  Set-VBREPPermission -Repository $repository -Type OnlySelectedUsers -User "VEEAM\Administrator"  RepositoryId        : 88788f9e-d8f5-4eb4-bc4f-9b3f5403bcec PermissionType      : OnlySelectedUsers Users               : {VEEAM\Administrator1, VEEAM\Administrator2} IsEncryptionEnabled : False EncryptionKey       : |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save it to the $repository variable. 2. Run the Set-VBREPPermission cmdlet. Set the $repository variable as the Repository parameter value. Set the OnlySelectedUsers option for the Type parameter. Specify the User parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Enabling Encryption for Repository

|  |  |
| --- | --- |
| This command enables encryption for the WinLocal repository.  |  | | --- | | $encryptionkey = Get-VBREncryptionKey -Description "Veeam Administrator"  $repository = Get-VBRBackupRepository -Name "WinLocal"  Set-VBREPPermission -Repository $repository -EnableEncryption -EncryptionKey $encryptionkey  RepositoryId        : 88788f9e-d8f5-4eb4-bc4f-9b3f5403bcec PermissionType      : OnlySelectedUsers Users               : {VEEAM\Administrator} IsEncryptionEnabled : True EncryptionKey       : ac87709d-b1a9-4c2e-8d55-557f8e49f639 |  Perform the following steps:   1. Run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. Specify the Description parameter value. Save it to the $encryptionkey variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save it to the $repository variable. 3. Run the Set-VBREPPermission cmdlet. Set the $repository variable as the Repository parameter value. Provide the EnableEncryption parameter. Set the $encryptionkey variable as the EncryptionKey parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Granting User Access Permissions to Everyone

|  |  |
| --- | --- |
| This example shows how to grant user access permissions to everyone and enable encryption for the WinLocal repository.  |  | | --- | | $encryptionkey = Get-VBREncryptionKey -Description "Veeam Administrator"  $repository = Get-VBRBackupRepository -Name "WinLocal"  Set-VBREPPermission -Repository $repository -Type Everyone -EnableEncryption -EncryptionKey $encryptionkey  RepositoryId        : 88788f9e-d8f5-4eb4-bc4f-9b3f5403bcec PermissionType      : Everyone Users               : {VEEAM\Administrator} IsEncryptionEnabled : True EncryptionKey       : ac87709d-b1a9-4c2e-8d55-557f8e49f639 |  Perform the following steps:   1. Run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. Specify the Description parameter value. Save it to the $encryptionkey variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save it to the $repository variable. 3. Run the Set-VBREPPermission cmdlet. Specify the following settings:  * Set the $repository variable as the Repository parameter value. * Set the Everyone option for the Type parameter. * Provide the EnableEncryption parameter. * Set the $encryptionkey variable as the EncryptionKey parameter value. |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBREncryptionKey](get-vbrencryptionkey.md)
* [Get-VBRKMSServer](get-vbrkmsserver.md)

Page updated 6/6/2024

Page content applies to build 13.0.1.1071
