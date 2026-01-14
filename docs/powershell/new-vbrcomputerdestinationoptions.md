---
title: "New-VBRComputerDestinationOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrcomputerdestinationoptions.html"
last_updated: "5/6/2024"
product_version: "13.0.1.1071"
---

# New-VBRComputerDestinationOptions

In this article

Short Description

Creates the target location settings for backup policies.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Store backups in the following locations:

* On a removable storage device attached to the protected computer.
* On a local drive of the protected computer.

|  |
| --- |
| New-VBRComputerDestinationOptions -LocalPath <string> -OSPlatform <VBRAgentType> {Windows | Linux | Mac}  [<CommonParameters>] |

* Store backups in a network shared folder.

|  |
| --- |
| New-VBRComputerDestinationOptions -OSPlatform <VBRAgentType> {Windows | Linux | Mac} -NetworkFolderPath <string> [-TargetShareType <VBRDestinationTargetShareType> {Smb | Nfs}] [-UseNetworkCredentials] [-NetworkCredentials <CCredentials>]  [<CommonParameters>] |

* Store backups on the following types of backup repositories:

* Backup repository managed by the Veeam backup server.
* Veeam Cloud Connect repository.

|  |
| --- |
| New-VBRComputerDestinationOptions -OSPlatform <VBRAgentType> {Windows | Linux | Mac} -BackupRepository <CBackupRepository> [-BackupServerName <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRComputerDestinationOptions object that contains the target location settings for the backup policy. Veeam Backup & Replication applies this policy to the protected computers.

Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet to get the repository.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| OSPlatform | Specifies the OS of the protected computers:   * Windows: for Windows computers. * Linux: for Linux computers. * Mac: for macOS computers. Note: Indexing for macOS computers is not supported in current version of Veeam PowerShell. | VBRAgentType | True | Named | False |
| LocalPath | Use this parameter if you want to keep backups on the following target locations:   * On a removable storage device attached to a protected computer. * On a local drive of a protected computer. | String | True | Named | False |
| NetworkFolderPath | Use this option if you want to keep backups in a network shared folder. | String | True | Named | False |
| BackupRepository | Use this option if you want to save a backup on either of the following types of a backup repository:   * Backup repository managed by the Veeam backup server. * Veeam Cloud Connect repository. Note: Cloud repositories added from Cloud Director tenant are not supported. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | True (ByValue) |
| TargetShareType | Specifies the protocol that you will use to keep backups on shared folders.   * SMB * NFS   Note: The NFS protocol type does not work for Windows computers.  Default: SMB | VBRDestinationTargetShareType | False | Named | False |
| UseNetworkCredentials | Defines that the network shared folder requires authentication. | SwitchParameter | False | Named | False |
| NetworkCredentials | Specifies the credentials which Veeam Agent will use to authenticate to the network shared folder. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| BackupServerName | Specifies the DNS name or an external IP address of the Veeam backup server that manages the target backup repository.  Note: You can use only the Veeam backup server where the Veeam Agent backup job is configured. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerDestinationOptions object that contains the target location settings for the backup policy.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Target Location Settings for Veeam Agent Backup Policy (Local Drive)

|  |  |
| --- | --- |
| This command creates target location settings for the backup policy that Veeam Agent job applies to the protected computers. The job will save the backups to a local drive of the protected computer. Use the LocalPath parameter to specify the local drive path settings.  |  | | --- | | New-VBRComputerDestinationOptions -LocalPath "D:\Backup" -OSPlatform Windows | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Target Location Settings for Veeam Agent Backup Policy (Network Shared Folder)

|  |  |
| --- | --- |
| This example shows how to create target location settings for the backup policy that Veeam Agent job applies to the protected computers. The job will save the backups to the network shared folder.  |  | | --- | | $creds = Get-Credential  New-VBRComputerDestinationOptions -NetworkFolderPath "172.17.53.14:/Veeam" -OSPlatform Linux -TargetShareType NFS -UseNetworkCredentials -NetworkCredentials $creds |  Perform the following steps:   1. Run the [Get-Credential](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.4) cmdlet. Save the result to the $creds variable. 2. Run the New-VBRComputerDestinationOptions cmdlet. Specify the following settings:  * Specify the NetworkFolderPath parameter value.  * Set the Linux value for the OSPlatform parameter. * Set the NFS value for the TargetShareType parameter. * Provide the UseNetworkCredentials parameter. * Set the $creds variable as the NetworkCredentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Creating Target Location Settings for Veeam Agent Backup Policy (Backup Repository)

|  |  |
| --- | --- |
| This example shows how to create target location settings for the backup policy that Veeam Agent job applies to the protected computers. The job will save the backups to the backup repository managed by the Veeam backup server.  |  | | --- | | $repository = Get-VBRBackupRepository -Name "Default Backup Repository"  New-VBRComputerDestinationOptions -OSPlatform Windows -BackupRepository $repository -BackupServerName "Repository 01" |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the New-VBRComputerDestinationOptions cmdlet. Set the Windows option for the OSPlatform parameter. Set the $repository variable as the BackupRepository parameter value. Specify the BackupServerName parameter value. |

Related Commands

[Get-VBRBackupRepository](get-vbrbackuprepository.md)

Page updated 5/6/2024

Page content applies to build 13.0.1.1071
