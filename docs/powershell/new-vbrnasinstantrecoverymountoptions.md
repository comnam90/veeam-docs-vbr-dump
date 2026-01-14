---
title: "New-VBRNASInstantRecoveryMountOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrnasinstantrecoverymountoptions.html"
last_updated: "9/4/2024"
product_version: "13.0.1.1071"
---

# New-VBRNASInstantRecoveryMountOptions

In this article

Short Description

Creates a mapping configuration for instant restore of file backups.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create a mapping configuration with an automatically selected mount server to be used for instant restore of file backups.

|  |
| --- |
| New-VBRNASInstantRecoveryMountOptions -Automatic  [<CommonParameters>] |

* Create a mapping configuration for which you can specify a host with the mount service to be used for instant restore of file backups.

|  |
| --- |
| New-VBRNASInstantRecoveryMountOptions -RestorePoint <VBRUnstructuredBackupRestorePoint[]> -MountServer <CHost[]>  [<CommonParameters>] |

Detailed Description

This cmdlet creates a mapping configuration for instant restore of file backups.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Automatic | Defines that the cmdlet will create a mapping configuration with automatically selecting a mount server to be used for instant restore of file backups. | SwitchParameter | True | Named | False |
| RestorePoint | Specifies an array of restore points. The cmdlet will create a mapping configuration for instant restore to the specified restore points. | Accepts the VBRUnstructuredBackupRestorePoint[] object. To get this object, run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| MountServer | Specifies the target mount server. The cmdlet will create a mapping configuration with a specific host with the mount service to be used for instant restore of file backups. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASInstantRecoveryMountOptions object that defines settings of the set of the mount options for instant restore of file share backups.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Automatic Mount Options for Instant Restore of File Share Backup

|  |  |
| --- | --- |
| This command creates a set of automatic mount options for instant restore of file share backups.  |  | | --- | | $automaticMapping = New-VBRNASInstantRecoveryMountOptions -Automatic | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Manual Mount Options for Instant Restore of File Share Backup

|  |  |
| --- | --- |
| This example shows how to create a set of manually configured mount options for instant restore of file share backups.  |  | | --- | | $backup = Get-VBRUnstructuredBackup -Name "Daily SMB1 Backup"  $nasBackupPoint = Get-VBRUnstructuredBackupRestorePoint -NASBackup $backup  $manualMapping = New-VBRNASInstantRecoveryMountOptions -RestorePoint $nasBackupPoint[0] -MountServer "172.17.20.3" |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Set the $backup variable as the NASBackup parameter value. Save the result to the $nasBackupPoint variable. 3. Run the New-VBRNASInstantRecoveryMountOptions cmdlet. Specify the following parameters:  * Specify the first value from the array returned to the $nasBackupPoint variable as the RestorePoint parameter. * Specify the MountServer parameter value. * Save the result to the $manualMapping variable. |

Related Commands

* [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md)
* [Get-VBRNASBackupRestorePoint](get-vbrnasbackuprestorepoint.md)

Page updated 9/4/2024

Page content applies to build 13.0.1.1071
