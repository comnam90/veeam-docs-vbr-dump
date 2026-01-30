---
title: "Update-VBRUnstructuredBackupPath"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/update-vbrunstructuredbackuppath.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Update-VBRUnstructuredBackupPath


Short Description

Updates the data source for file backups and object storage backups.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Update the data source: a file share, a root server protected by a file backup job or object storage protected by object storage backup job.

|  |
| --- |
| Update-VBRUnstructuredBackupPath -Backup <VBRUnstructuredBackup> -SourceUnstructuredServer <VBRUnstructuredServer> -TargetUnstructuredServer <VBRUnstructuredServer> [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Update the name of the root server with the name that is not added to the Veeam Backup & Replication database.

|  |
| --- |
| Update-VBRUnstructuredBackupPath -Backup <VBRUnstructuredBackup> -SourceRootNASServerName <string> -TargetRootNASServer <VBRNASServer> [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Update the SAN host or SAN volume name.

|  |
| --- |
| Update-VBRUnstructuredBackupPath -Backup <VBRUnstructuredBackup> -SourceSANEntity <VBRSANEntity> -TargetSANEntity <VBRSANEntity> [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Update the name of the SAN host with the name that is not added to the Veeam Backup & Replication database.

|  |
| --- |
| Update-VBRUnstructuredBackupPath -Backup <VBRUnstructuredBackup> -SourceSANHostName <string> -TargetSANHost <VBRSANEntity> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet updates the data source for file backups and object storage backups.

|  |
| --- |
| Important |
| Consider the following:   * To correctly update the source file share path for a file backup job that has a configured secondary target, refer to the [Updating Source File Share Path for Backup Jobs with Secondary Target](https://helpcenter.veeam.com/docs/vbr/userguide/update_source_share_path.html?ver=13) section in the Veeam Backup & Replication User Guide. * To update the data source for object storage backups, the target data source must have the same path as the original data source. For example, if your original data source is "AWS 01" object storage with the "bucket01/Files/reports" location, and you want to change to target data source "AWS 02", it must also have the "bucket01/Files/reports" location. If you want to change the data source and location, run the [New-VBRObjectStorageBackupJobObject](new-vbrobjectstoragebackupjobobject.md) cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies a file share backup or an object storage backup. The cmdlet will update the the data source for these backups. | Accepts the VBRUnstructuredBackup object. To get this object, run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| SourceUnstructuredServer | Specifies data source of file share backup or object storage backup. The cmdlet will update this data source to a new data source. | Accepts the VBRUnstructuredServer object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | False |
| SourceRootNASServerName | Specifies a new name of the root server. The cmdlet will add this name to a configuration database. | String | True | Named | False |
| SourceSANEntity | Specifies the enterprise NAS system or its volume where the file shares reside. The cmdlet will update the path to this NAS system to a new path. | Accepts the VBRSANEntity[] object. To create this object, run the [Get-NetAppHost](get-netapphost.md) cmdlet. | True | Named | False |
| SourceSANHostName | Specifies the name of the SAN host object to be changed in the backup. | String | True | Named | False |
| TargetUnstructuredServer | Specifies new data source of file share backup or object storage backup. The cmdlet will update this data source to this data source. | Accepts the VBRUnstructuredServer object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | False |
| TargetRootNASServer | Specifies the file share server. The cmdlet will update the root server name to this one. | Accepts the VBRNASServer object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | False |
| TargetSANEntity | Specifies the enterprise NAS system or its volume where the file share will reside. The cmdlet will use this NAS system entity as a new one when updating the backup information. | Accepts the VBRSANEntity object. To create this object, run the [Get-NetAppHost](get-netapphost.md) cmdlet. | True | Named | False |
| TargetSANHost | Specifies the enterprise NAS system or its volume where the file share will reside. The cmdlet will use this NAS system entity as a new one when updating the backup information. | Accepts the VBRSANEntity object. To create this object, run the [Get-NetAppHost](get-netapphost.md) cmdlet. | True | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUnstructuredBackup object that defines results of updating the data source to the protected file share or object storage.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Updating Path to Existing Source File Share Protected by a File Backup Job

|  |  |
| --- | --- |
| This example shows how to update the path to the \\WinSRV2049\Documents file share protected by a file backup job.  |  | | --- | | $nasbackup = Get-VBRUnstructuredBackup -Name "File Backup Job 1"  $sourceserver = Get-VBRUnstructuredServer -Backup $nasbackup  $targetserver = Get-VBRUnstructuredServer -Name "\\WinSRV2049\Documents"  Update-VBRUnstructuredBackupPath -Backup $nasbackup -SourceUnstructuredServer $sourceserver -TargetUnstructuredServer $targetserver |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $nasbackup variable. 2. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Set the $nasbackup variable as the Backup parameter value. Save the result to the $sourceserver variable. 3. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $targetserver variable. 4. Run the Update-VBRUnstructuredBackupPath cmdlet. Specify the following settings:  * Set the $nasbackup variable as the Backup parameter value. * Set the $sourceserver variable as the SourceUnstructuredServer parameter value. * Set the $targetserver variable as the TargetUnstructuredServer parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Updating Data Source for Object Storage Backups

|  |  |
| --- | --- |
| This example shows how to update the data source for object storage backups. The cmdlet will change the data source from AWS01to AWS02.  |  | | --- | | $backup = Get-VBRUnstructuredBackup -Name 'update path OS'  $source = Get-VBRUnstructuredServer -Name '1st minio share'  $target = Get-VBRUnstructuredServer -Name "2nd minio share"  Update-VBRUnstructuredBackupPath -Backup $backup -SourceUnstructuredServer $source -TargetUnstructuredServer $target |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.  1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $source variable.  1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $target variable.  1. Run the Update-VBRUnstructuredBackupPath cmdlet. Specify the following settings:  * Set the $backup variable as the Backup parameter value. * Set the $source variable as the SourceUnstructuredServer parameter value. * Set the $target variable as the TargetUnstructuredServer parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Updating Name of Root File Share Server

|  |  |
| --- | --- |
| This example shows how to update the name of the root server to the name that does not exist in the Veeam Backup & Replication database.  |  | | --- | | $nasbackup = Get-VBRUnstructuredBackup -Name "File Backup Job 1"  $targetserver = Get-VBRUnstructuredServer -Name "\\WinSRV2049\Reports"  Update-VBRUnstructuredBackupPath -Backup $nasbackup -SourceRootNASServerName "\\WinSRV2049\Root" -TargetRootNASServer $targetserver |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $nasbackup variable. 2. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $targetserver variable. 3. Run the Update-VBRUnstructuredBackupPath cmdlet. Specify the following settings:  * Set the $nasbackup variable as the Backup parameter value. * Specify the SourceRootNASServerName parameter value. * Set the $targetserver variable as the TargetNASServer parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Updating SAN Host

|  |  |
| --- | --- |
| This example shows how to update the SAN host.  |  | | --- | | $nasbackup = Get-VBRUnstructuredBackup -Name "File Backup Job 1"  $sourcenetapp = Get-NetAppHost -Name "pdc-ontap-1"  $targetnetapp = Get-NetAppHost -Name "pdc-ontap-3"  Update-VBRUnstructuredBackupPath -Backup $nasbackup -SourceSANEntity $sourcenetapp -TargetSANEntity $targetnetapp |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $nasbackup variable. 2. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter value. Save the result to the $sourcenetapp variable. 3. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter value. Save the result to the $targetnetapp variable. 4. Run the Update-VBRUnstructuredBackupPath cmdlet. Specify the following settings:  * Set the $nasbackup variable as the Backup parameter value. * Set the $sourcenetapp variable as the SourceSANEntity parameter value. * Set the $targetnetapp variable as the TargetSANEntity parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Updating SAN Host Name

|  |  |
| --- | --- |
| This example shows how to update the name of the SAN host. The cmdlet will change the SAN host name from pdc-ontap-3 to pdc-ontap-5.  |  | | --- | | $nasbackup = Get-VBRUnstructuredBackup -Name "File Backup Job 1"  $targetnetapp = Get-NetAppHost -Name "pdc-ontap-3"  Update-VBRUnstructuredBackupPath -Backup $nasbackup -SourceSANHostName "pdc-ontap-5" -TargetSANHost $targetnetapp |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $nasbackup variable. 2. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter value. Save the result to the $targetnetapp variable. 3. Run the Update-VBRUnstructuredBackupPath cmdlet. Specify the following settings:  * Set the $nasbackup variable as the Backup parameter value.  * Specify the SourceSANHostName parameter value.  * Set the $targetnetapp variable as the TargetSANHost parameter value. |

Related Commands

* [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md)
* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)


