---
title: "Update-VBRNasBackupPath (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/update-vbrnasbackuppath.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Update-VBRNasBackupPath (obsolete)

In this article

Short Description

Updates the file path to the source file share.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Update-VBRUnstructuredBackupPath](update-vbrunstructuredbackuppath.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Update the path to the existing source CIFS or NFS file share or root server protected by a file backup job.

|  |
| --- |
| Update-VBRNasBackupPath -Backup <VBRNASBackup> -SourceNASServer <VBRNASServer> -TargetNASServer <VBRNASServer> [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Update the name of the root server to one that does not exist in the Veeam Backup & Replication database.

|  |
| --- |
| Update-VBRNasBackupPath -Backup <VBRNASBackup> -SourceRootNASServerName <String> -TargetRootNASServer <VBRNASServer> [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Update the SAN host or SAN volume name.

|  |
| --- |
| Update-VBRNasBackupPath -Backup <VBRNASBackup> -SourceSANEntity <VBRSANEntity> -TargetSANEntity <VBRSANEntity> [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Update the name of the SAN host to a one not added to the Veeam Backup & Replication infrastructure.

|  |
| --- |
| Update-VBRNasBackupPath -Backup <VBRNASBackup> -SourceSANHostName <String> -TargetSANHost <VBRSANEntity> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet updates the file path to the source file share.

|  |
| --- |
| Important |
| To correctly update the source file share path for a file backup job that has a configured secondary target, refer to the [Updating Source File Share Path for Backup Jobs with Secondary Target](https://helpcenter.veeam.com/docs/backup/vsphere/update_source_share_path.html?ver=120) section in the Veeam Backup & Replication User Guide. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies a file share backup. The cmdlet will update the path to the source file share for this backup. | Accepts the VBRNASBackup object. To get this object, run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| SourceNASServer | Specifies the file share server. The cmdlet will update this path/file share/server name to a new one. | Accepts the VBRNASServer object. To get this object, run the [Get-VBRNASServer](get-vbrnasserver.md) cmdlet. | True | Named | False |
| SourceRootNASServerName | Specifies a new name of of the root server. The cmdlet will add this name to a configuration database. | String | True | Named | False |
| SourceSANEntity | Specifies the enterprise NAS system or its volume where the file shares reside. The cmdlet will update the path to this NAS system to a new path. | Accepts the VBRSANEntity object. To create this object, run the [Get-NetAppHost](get-netapphost.md) cmdlet. | True | Named | False |
| SourceSANHostName | Specifies the name of the SAN host object to be changed in the backup. | String | True | Named | False |
| TargetNASServer | Specifies the file share server. The cmdlet will update the file share path/name/server name to this one. | Accepts the VBRNASServer object. To get this object, run the [Get-VBRNASServer](get-vbrnasserver.md) cmdlet. | True | Named | False |
| TargetRootNASServer | Specifies the file share server. The cmdlet will update the root server name to this one. | Accepts the VBRNASServer object. To get this object, run the [Get-VBRNASServer](get-vbrnasserver.md) cmdlet. | True | Named | False |
| TargetSANEntity | Specifies the enterprise NAS system or its volume where the file share will reside. The cmdlet will use this NAS system entity as a new one when updating the backup information. | Accepts the VBRSANEntity object. To create this object, run the [Get-NetAppHost](get-netapphost.md) cmdlet. | True | Named | False |
| TargetSANHost | Specifies the enterprise NAS system or its volume where the file share will reside. The cmdlet will use this NAS system entity as a new one when updating the backup information. | Accepts the VBRSANEntity object. To create this object, run the [Get-NetAppHost](get-netapphost.md) cmdlet. | True | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASBackup object that defines results of updating the paths to the protected file share.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Updating Path to Existing Source File Share Protected by a File Backup Job

|  |  |
| --- | --- |
| This example shows how to update the path to the existing source SMB or NFS file share or root server protected by a file backup job.  |  | | --- | | $nasbackup = Get-VBRNASBackup -Name "File Backup Job 1"  $sourceserver = Get-VBRNASServer -Backup $nasbackup  $targetserver = Get-VBRNASServer -Name "\\WinSRV2049\Documents"  Update-VBRNasBackupPath -Backup $nasbackup -SourceNASServer $sourceserver -TargetNASServer $targetserver |  Perform the following steps:   1. Run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $nasbackup variable. 2. Run the [Get-VBRNASServer](get-vbrnasserver.md) cmdlet. Set the $nasbackup variable as the Backup parameter value. Save the result to the $sourceserver variable. 3. Run the [Get-VBRNASServer](get-vbrnasserver.md) cmdlet. Specify the Name parameter value. Save the result to the $targetserver variable. 4. Run the Update-VBRNasBackupPath cmdlet. Specify the following settings:  * Set the $nasbackup variable as the Backup parameter value. * Set the $sourceserver variable as the SourceNASServer parameter value. * Set the $targetserver variable as the TargetNASServer parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Updating Name of Root File Share Server

|  |  |
| --- | --- |
| This example shows how to update the name of the root server to the name that does not exist in the Veeam Backup & Replication database.  |  | | --- | | $nasbackup = Get-VBRNASBackup -Name "File Backup Job 1"  $targetserver = Get-VBRNASServer -Name "\\WinSRV2049\Reports"  Update-VBRNasBackupPath -Backup $nasbackup -SourceRootNASServerName "\\WinSRV2049\Root" -TargetRootNASServer $targetserver |  Perform the following steps:   1. Run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $nasbackup variable. 2. Run the [Get-VBRNASServer](get-vbrnasserver.md) cmdlet. Specify the Name parameter value. Save the result to the $targetserver variable. 3. Run the Update-VBRNasBackupPath cmdlet. Specify the following settings:  * Set the $nasbackup variable as the Backup parameter value. * Specify the SourceRootNASServerName parameter value. * Set the $targetserver variable as the TargetNASServer parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Updating SAN Host

|  |  |
| --- | --- |
| This example shows how to update the SAN host.  |  | | --- | | $nasbackup = Get-VBRNASBackup -Name "File Backup Job 1"  $sourcenetapp = Get-NetAppHost -Name "pdc-ontap-1"  $targetnetapp = Get-NetAppHost -Name "pdc-ontap-3"  Update-VBRNasBackupPath -Backup $nasbackup -SourceSANEntity $sourcenetapp -TargetSANEntity $targetnetapp |  Perform the following steps:   1. Run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $nasbackup variable. 2. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter value. Save the result to the $sourcenetapp variable. 3. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter value. Save the result to the $targetnetapp variable. 4. Run the Update-VBRNasBackupPath cmdlet. Specify the following settings:  * Set the $nasbackup variable as the Backup parameter value. * Set the $sourcenetapp variable as the SourceSANEntity parameter value. * Set the $targetnetapp variable as the TargetSANEntity parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Updating SAN Host Name

|  |  |
| --- | --- |
| This example shows how to update the name of the SAN host. The cmdlet will change the SAN hpst name from pdc-ontap-3 to pdc-ontap-5.  |  | | --- | | $nasbackup = Get-VBRNASBackup -Name "File Backup Job 1"  $targetnetapp = Get-NetAppHost -Name "pdc-ontap-3"  Update-VBRNasBackupPath -Backup $nasbackup -SourceSANHostName "pdc-ontap-5" -TargetSANHost $targetnetapp |  Perform the following steps:   1. Run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $nasbackup variable. 2. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter value. Save the result to the $targetnetapp variable. 3. Run the Update-VBRNasBackupPath cmdlet. Specify the following settings:  * Set the $nasbackup variable as the Backup parameter value.  * Specify the SourceSANHostName parameter value.  * Set the $targetnetapp variable as the TargetSANHost parameter value. |

Related Commands

* [Get-VBRNASBackup](get-vbrnasbackup.md)
* [Get-VBRNASServer](get-vbrnasserver.md)

Page updated 1/6/2025

Page content applies to build 13.0.1.1071
