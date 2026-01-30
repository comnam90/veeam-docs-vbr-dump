---
title: "New-VBRNASPermissionSet"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrnaspermissionset.html"
last_updated: "7/28/2025"
product_version: "13.0.1.1071"
---

# New-VBRNASPermissionSet


Short Description

Creates a permission set for instant restore of file share backups that will be used if the file share backup does not contain security information.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create a permission set that denies access to the published SMB share to everyone except its owner.

|  |
| --- |
| New-VBRNASPermissionSet [-RestorePoint] <VBRUnstructuredBackupRestorePoint[]> [-Owner] <string> -DenyEveryone [-Server <CHost>] [-UseLinuxLocalUser] [<CommonParameters>] |

* Create a permission set that allows access to the published SMB share to everyone.

|  |
| --- |
| New-VBRNASPermissionSet [-RestorePoint] <VBRUnstructuredBackupRestorePoint[]> [-Owner] <string> [-AllowEveryone] [-Server <CHost>] [-UseLinuxLocalUser] [<CommonParameters>] |

* Create a permission set that allows access to the published SMB share to the limited number of users. specified in the PermissionScope parameter. This parameter must be specified together with the PermissionScope parameter.

|  |
| --- |
| New-VBRNASPermissionSet [-RestorePoint] <VBRUnstructuredBackupRestorePoint[]> [-Owner] <string> -AllowSelected -PermissionScope <string[]> [-Server <CHost>] [-UseLinuxLocalUser] [<CommonParameters>] |

Detailed Description

The cmdlet creates a permission set for instant restore of file share backups that will be used if the file share backup does not contain security information.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies an array of restore points. The cmdlet will create a permission set with specific security settings for each of the specified restore points. | Accepts the VBRUnstructuredBackupRestorePoint[] object. To get this object, run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| Owner | Specifies a name of the account or group in the user name or domain\user name format. The cmdlet will use this parameter if the file share backup does not contain security information. | String | True | 1 | False |
| DenyEveryone | Defines that the permission set will deny access to the published SMB share to everyone except its owner. | SwitchParameter | True | Named | False |
| AllowEveryone | Defines that the permission set will allow access to the published SMB share to everyone.  Note: If the DenyEveryone, AllowSelected, or AllowEveryone parameter is not specified, the cmdlet will use the AllowEveryone parameter by default. | SwitchParameter | True | Named | False |
| AllowSelected | Defines that the permission set will allow access to the published SMB share to the limited number of users specified in the PermissionScope parameter. This parameter must be specified together with the PermissionScope parameter. | SwitchParameter | True | Named | False |
| PermissionScope | Specifies an array of users. The cmdlet will provide these users with the access to the published SMB share. This parameter must be specified together with the AllowSelected parameter. | String | True | Named | False |
| Server | Specifies the Linux mount server which local user account you want to use. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| UseLinuxLocalUser | Defines that the permission set will use the Linux local user account. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns a VBRNASPermissionSet object for each specified restore point. This object defines permission settings that will be applied to instant restore of file share backups.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Permission Set to Deny Access to SMB Share to Everyone Except Owner

|  |  |
| --- | --- |
| The following request creates a permission set that denies access to the published SMB share to everyone except its owner.  |  | | --- | | $backup = Get-VBRUnstructuredBackup -Name "Daily SMB1 Backup"  $nasBackupPoint = Get-VBRUnstructuredBackupRestorePoint -NASBackup $backup  $permissions = New-VBRNASPermissionSet -RestorePoint $nasBackupPoint[0] -Owner "User 1" -DenyEveryone |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Set the $backup variable as the NASBackup parameter value. Save the result to the $nasBackupPoint variable. 3. Run the New-VBRNASPermissionSet cmdlet. Specify the following parameters:  * Specify the first value from the array returned to the $nasBackupPoint variable as the RestorePoint parameter. * Specify the Owner parameter value. * Provide the DenyEveryone parameter. * Save the result to the $permissions variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Permission Set to Allow Access to SMB Share to Everyone

|  |  |
| --- | --- |
| The following request creates a permission set that allows access to the published SMB share to everyone.  |  | | --- | | $backup = Get-VBRUnstructuredBackup -Name "Daily SMB1 Backup"  $nasBackupPoint = Get-VBRUnstructuredBackupRestorePoint -NASBackup $backup  $permissions = New-VBRNASPermissionSet -RestorePoint $nasBackupPoint[0] -Owner "User 1" -AllowEveryone |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Set the $backup variable as the NASBackup parameter value. Save the result to the $nasBackupPoint variable. 3. Run the New-VBRNASPermissionSet cmdlet. Specify the following parameters:  * Specify the first value from the array returned to the $nasBackupPoint variable as the RestorePoint parameter.  * Specify the Owner parameter value.  * Provide the AllowEveryone parameter. * Save the result to the $permissions variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Creating Permission Set to Allow Access to SMB Share to Selected Users

|  |  |
| --- | --- |
| The following request creates a permission set that allows access to the published SMB share to selected users.  |  | | --- | | $backup = Get-VBRUnstructuredBackup -Name "Daily SMB1 Backup"  $nasBackupPoint = Get-VBRUnstructuredBackupRestorePoint -NASBackup $backup  $permissions = New-VBRNASPermissionSet -RestorePoint $nasBackupPoint[0] -Owner "User 1" -AllowSelected -PermissionScope ("domain\user 2") |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Set the $backup variable as the NASBackup parameter value. Save the result to the $nasBackupPoint variable. 3. Run the New-VBRNASPermissionSet cmdlet. Specify the following parameters:  * Specify the first value from the array returned to the $nasBackupPoint variable as the RestorePoint parameter. * Specify the Owner parameter value. * Provide the AllowSelected parameter. * Specify the PermissionScope parameter. * Save the result to the $permissions variable. |

Related Commands

* [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md)
* [Get-VBRUnstructuredBackupRestorePoint](get-vbrnasbackuprestorepoint.md)


