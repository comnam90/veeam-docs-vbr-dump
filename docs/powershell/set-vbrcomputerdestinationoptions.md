---
title: "Set-VBRComputerDestinationOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcomputerdestinationoptions.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Set-VBRComputerDestinationOptions

In this article

Short Description

Modifies the target location for Veeam Agent backup policies.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Store backups in the following locations:

* on a removable storage device attached to the protected computer.
* on a local drive of the protected computer.

|  |
| --- |
| Set-VBRComputerDestinationOptions -Options <VBRComputerDestinationOptions> -LocalPath <string>  [<CommonParameters>] |

* Store backups in a network shared folder.

|  |
| --- |
| Set-VBRComputerDestinationOptions -Options <VBRComputerDestinationOptions> [-NetworkFolderPath <string>] [-TargetShareType <VBRDestinationTargetShareType> {Smb | Nfs}] [-UseNetworkCredentials] [-NetworkCredentials <CCredentials>]  [<CommonParameters>] |

* Store backups in a backup repository managed by the Veeam backup server.

|  |
| --- |
| Set-VBRComputerDestinationOptions -Options <VBRComputerDestinationOptions> [-BackupServerName <string>] [-BackupRepository <CBackupRepository>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the target location settings for the backup policy that Veeam Agent job applies to the protected computers.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the target location settings that you want to modify. | Accepts the VBRComputerDestinationOptions object. To get this object, run the [New-VBRComputerDestinationOptions](new-vbrcomputerdestinationoptions.md) cmdlet. | True | Named | True (ByValue) |
| LocalPath | Use this parameter if you want to keep backups on the following target locations:   * On a removable storage device attached to a protected computer. * On a local drive of a protected computer. | String | True | Named | False |
| NetworkFolderPath | Use this option if you want to keep backups in a network shared folder. | String | False | Named | False |
| BackupRepository | Use this option if you want to save a backup on either of the following types of a backup repository:   * Backup repository managed by the Veeam backup server. * Veeam Cloud Connect repository. Note: Cloud repositories added from Cloud Director tenant are not supported. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| TargetShareType | Specifies the protocol that you will use to keep backups on shared folders.   * SMB * NFS   Note: The NFS protocol type does not work for Windows computers. | VBRDestinationTargetShareType | False | Named | False |
| UseNetworkCredentials | Defines that the network shared folder requires authentication. | SwitchParameter | False | Named | False |
| NetworkCredentials | Specifies the credentials which Veeam Agent will use to authenticate to the network shared folder. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| BackupServerName | Specifies the DNS name or an external IP address of the Veeam backup server that manages the target backup repository.  Note: You can use only the Veeam backup server where the Veeam Agent backup job is configured. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerDestinationOptions object that contains the target location settings for the backup policy.

Examples

Modifying Target Location Settings for Veeam Agent Backup Policy

This example shows how to modify target location settings for the backup policy that Veeam Agent job applies to the protected computers. The job will save the backups to the backup repository managed by the Veeam backup server.

|  |
| --- |
| $job = Get-VBRComputerBackupJob -Name "WinPolicy"  $destination = $job.DestinationOptions  $repository = Get-VBRBackupRepository -Name "Repository"  Set-VBRComputerDestinationOptions -Options $destination -BackupRepository $repository |

Perform the following steps:

1. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Get the DestinationOptions property of the $job variable. Save the result to the $destination variable.
3. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.
4. Run the Set-VBRComputerDestinationOptions cmdlet. Set the $destination variable as the Options parameter value. Set the $repository variable as the BackupRepository parameter value.

Related Commands

* [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)

Page updated 4/24/2024

Page content applies to build 13.0.1.1071
