---
title: "Publish-VBRBackupContent"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/publish-vbrbackupcontent.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Publish-VBRBackupContent

In this article

Short Description

Publishes disks from a backup or replica using the iSCSI or FUSE protocol.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Publish-VBRBackupContent -RestorePoint <COib> [-AllowedIps <string[]>] [-DiskNames <string[]>] [-RunAsync] [-TargetServerName <string>] [-TargetServerCredentials <CCredentials>] [-MountHostId <guid>] [-Reason <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet publishes content using the iSCSI protocol for disks with Microsoft Windows-based file system or the FUSE protocol for disks with Unix-based file systems. You can publish disks from backups and replicas. For the list of supported backup types, see the [Publishing Disks (Data Integration API)](https://helpcenter.veeam.com/docs/vbr/userguide/data_integration_api.html?ver=13) section in the Veeam Backup & Replication User Guide.

[For Microsoft Windows-based file systems] Depending on how you want to configure an iSCSI session, you can use one of the following mount modes:

* Automatic — use this mode if you want Veeam Backup & Replication to automatically configure the iSCSI initiator, start iSCSI session and allow the specified target server to access disk content. To use this option, you must specify a name (the TargetServerName parameter) and credentials (the TargetServerCredentials parameter) of the target server. For more information, see [Example 2](#ex_two).

|  |
| --- |
| Note |
| If you want to automatically mount data to Unix-based machines, you must use the FUSE protocol (the EnableFUSEProtocol parameter). For more details, see Example 3. |

* Manual — use this mode if you want to manually start an iSCSI session from any server that has access to the iSCSI Target Server (mount server). In this case, you must specify an array of IP addresses of servers that are allowed to access the iSCSI Target Server (the AllowedIps parameter). For more information, see [Example 1](#ex_one).

After you started the publishing session, you can check details on this session and stop it from the PowerShell console or the Veeam Backup & Replication UI.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point. The cmdlet will publish disks in the state stored in the specified restore point. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| AllowedIps | For Microsoft Windows-based file systems and the manual mount mode.  Specifies an array of IP addresses of target servers (iSCSI initiators) that are allowed to access the iSCSI Target Server (mount server).  Note: This parameter is required if you do not specify the TargetServerName parameter. After the cmdlet finishes its work, you need to manually start the iSCSI session from any server specified in this parameter to the iSCSI Target Server. | String[] | False | Named | False |
| DiskNames | Specifies disk names. The cmdlet will publish disks with the specified names. If you do not specify this parameter, the cmdlet will publish all disks from the backup or replica. | String[] | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| TargetServerName | For the automatic mount mode.  Specifies the name of the target server. The cmdlet will give the specified server access to the disk content.  Note: You must specify the TargetServerCredentials parameter to provide credentials that Veeam Backup & Replication will use to authenticate against the target server. | String | False | Named | False |
| TargetServerCredentials | Specifies credentials that the cmdlet will use to authenticate against the target server. | Accepts the CCredentials object. To create this object, run the [Add-VBRCredentials](add-vbrcredentials.md) cmdlet. | False | Named | False |
| MountHostId | Specifies the ID of a server that has the mount server role. The mount server acts as an intermediary between the backup repository and the target server.  If you specify the ID, the cmdlet will use the specified server as the mount server. If you do not specify the ID, the cmdlet will use the mount server associated with the backup repository where backups are stored.  Note: You must add the server with this ID as the mount server to any backup repository in your backup infrastructure. For more information, see the [Specify Mount Server Settings](https://helpcenter.veeam.com/docs/vbr/userguide/repository_mount_server.html?ver=13) section in the Veeam Backup & Replication User Guide. | GUID | False | Named | False |
| EnableFUSEProtocol | Enables the FUSE protocol.  Note: This parameter is required if you want to publish disks with Unix-based file systems. | SwitchParameter | False | Named | False |
| Reason | Specifies the reason for disk publishing. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRBackupContent object that contains settings of published backed-up files.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Publishing Disks and Giving Access for Specific Target Server (Manual Mode)

|  |  |
| --- | --- |
| This example shows how to allow the 198.51.100.0 server to access the content of the published disks.  |  | | --- | | $backup = Get-VBRBackup -Name "Webservers Backup Job"  $point = Get-VBRRestorePoint -Backup $backup -Name "Webserver03" | Sort-Object –Property CreationTime | Select -Last 1  Publish-VBRBackupContent -RestorePoint $point -AllowedIps "198.51.100.0" -RunAsync |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Name parameter value. Pipe the cmdlet output to the Sort-Object cmdlet and set the CreationTime value as the Property parameter value. Pipe the output to the Select cmdlet to select the last restore point. Save the result to the $point variable. 3. Run the Publish-VBRBackupContent cmdlet. Specify the following settings:  * Set the $point variable as the RestorePoint parameter value. * Specify the AllowedIps parameter value. * Provide the RunAsync parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Publishing Disks (Automatic Mode)

|  |  |
| --- | --- |
| This example shows how to publish disks to the WinSrv2049 iSCSI target server.  |  | | --- | | $backup = Get-VBRBackup -Name "Webservers Backup Job"  $point = Get-VBRRestorePoint -Backup $backup -Name "Webserver03" | Sort-Object –Property CreationTime | Select -Last 1  $creds = Add-VBRCredentials -User "WinSrv2049\Administrator" -Password "Pa$$w0rd"  Publish-VBRBackupContent -RestorePoint $point -TargetServerName "WinSrv2049" -TargetServerCredentials $creds |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Name parameter value. Pipe the cmdlet output to the Sort-Object cmdlet and set the CreationTime value as the Property parameter value. Pipe the output to the Select cmdlet to select the last restore point. Save the result to the $point variable. 3. Run the [Add-VBRCredentials](add-vbrcredentials.md) cmdlet. Specify the User and the Password parameter values. Save the result to the $creds variable. 4. Run the Publish-VBRBackupContent cmdlet. Specify the following settings:  * Set the $point variable as the RestorePoint parameter value.  * Specify the TargetServerName parameter value. * Set the $creds variable as the TargetServerCredentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Publishing Disks to Linux Server

|  |  |
| --- | --- |
| This example shows how to publish disks to the 192.0.8.1 Linux server.  |  | | --- | | $backup = Get-VBRBackup -Name "LinSrv2049"  $restorepoint = Get-VBRRestorePoint -Backup $backup | Sort-Object –Property CreationTime | Select -Last 1  $creds = Get-VBRCredentials -Name "LinAdministrator"  $session = Publish-VBRBackupContent -RestorePoint $restorepoint -TargetServerName 192.0.8.1 -TargetServerCredentials $creds -EnableFUSEProtocol |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Pipe the cmdlet output to the Sort-Object cmdlet and set the CreationTime value as the Property parameter value. Pipe the output to the Select cmdlet to select the last restore point. Save the result to the $restorepoint variable. 3. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $creds variable. 4. Run the Publish-VBRBackupContent cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Specify the TargetServerName parameter value.  * Set the $creds variable as the TargetServerCredentials parameter value.  * Provide the EnableFUSEProtocol parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Publishing Disks and Specifying Mount Server ID

|  |  |
| --- | --- |
| This example shows how to publish disks to the WinSrv2049 target server and specify the mount server ID.  |  | | --- | | $backup = Get-VBRBackup -Name "Webservers Backup Job"  $point = Get-VBRRestorePoint -Backup $backup -Name "Webserver03" | Sort-Object –Property CreationTime | Select -Last 1  $creds = Add-VBRCredentials -User "WinSrv2049\Administrator" -Password "Pa$$w0rd"  Publish-VBRBackupContent -RestorePoint $point -TargetServerName "WinSrv2049" -TargetServerCredentials $creds -MountHostId "c3498ba3eefd4576bc0kaeb38b4e9qs5" |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Name parameter value. Pipe the cmdlet output to the Sort-Object cmdlet and set the CreationTime value as the Property parameter value. Pipe the output to the Select cmdlet to select the last restore point. Save the result to the $point variable. 3. Run the [Add-VBRCredentials](add-vbrcredentials.md) cmdlet. Specify the User parameter value. Specify the Password parameter value. Save the result to the $creds variable. 4. Run the Publish-VBRBackupContent cmdlet. Specify the following settings:  * Set the $point variable as the RestorePoint parameter value. * Specify the TargetServerName parameter. * Set the $creds variable as the TargetServerCredentials parameter value. * Specify the MountHostId parameter. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Add-VBRCredentials](add-vbrcredentials.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
