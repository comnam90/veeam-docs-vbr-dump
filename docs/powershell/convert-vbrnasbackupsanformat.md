---
title: "Convert-VBRNASBackupSANFormat"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/convert-vbrnasbackupsanformat.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Convert-VBRNASBackupSANFormat

In this article

Short Description

Converts backups created for SMB or NFS file shares residing on an enterprise NAS system into the format of a NAS filer share on the same storage system.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Convert SMB or NFS file shares by getting file shares by the backup that protects them.

|  |
| --- |
| Convert-VBRNASBackupSANFormat -Backup <VBRNASBackup> -Server <VBRNASServer[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Convert SMB or NFS file shares by getting file shares by the enterprise NAS system on which they are residing.

|  |
| --- |
| Convert-VBRNASBackupSANFormat -Backup <VBRNASBackup> -SANEntity <VBRSANEntity[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

The cmdlet converts backups created for SMB or NFS file shares residing on an enterprise NAS system into the format of a NAS filer share. Use this cmdlet as the first step when replacing simple SMB or NFS shares with the NAS filer share residing on the same storage system. To locate the original file share, specify the name of the backup created for it and either the name of the file share or SAN entity (for example, storage system volume) where the file share resides.

Note that running the Convert-VBRNASBackupSANFormat cmdlet is a single step in the procedure of converting backups from SMB or NFS shares to NAS filer shares.

You can also convert backups created with backup copy jobs to continue the old backup chain. That is also a complex procedure.

For more information, see [Converting Backups from SMB or NFS Shares to NAS Filer Shares](https://helpcenter.veeam.com/docs/vbr/userguide/convert_nas_shares_into_san.html?ver=13) in the Veeam Backup & Replication User Guide.

|  |
| --- |
| Important |
| If you convert backups and map them to a file backup job with backup copy, during the next job run, Veeam Backup & Replication will perform an active full backup for the backup copy. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies a file share backup. The cmdlet will convert this backup from SMB or NFS format into NAS filer format. | Accepts the VBRNASBackup object. To get this object, run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. | True | Named | True |
| Server | Specifies the file share server. The cmdlet will convert backups protecting an array of these file share servers. | Accepts the VBRNASServer[] object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | False |
| SANEntity | Specifies the enterprise NAS system or its volume where the file shares reside. The cmdlet will convert backups protecting an array of file shares residing on this NAS system. | Accepts the VBRSANEntity[] object. To create this object, run the [Get-NetAppHost](get-netapphost.md), [Get-ThinkSystemHost](get-thinksystemhost.md), [Get-VBRIsilonHost](get-vbrisilonhost.md) or [Get-VBRNutanixHost](get-vbrnutanixhost.md) cmdlet. | True | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASBackup object that defines results of converting the backups of SMB or NFS file share into the format that supports NAS filer shares.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Converting SMB or NFS File Shares by Backups that Protect Them

|  |  |
| --- | --- |
| The example shows how to convert the Daily SMB1 Backup file shares that reside on an enterprise NAS system into a NAS filer share on the same storage. The cmdlet will find the backup on the certain file share by the backup name.  |  | | --- | | $nasBackup = Get-VBRUnstructuredBackup -Name "Daily SMB1 Backup"  $nasServer = Get-VBRUnstructuredServer -Name "\\WinSRV2020\Documents"  Convert-VBRNASBackupSANFormat -Backup $nasBackup -Server $nasServer |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $nasBackup variable. 2. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $nasServer variable. 3. Run the Convert-VBRNASBackupSANFormat cmdlet. Set the $nasBackup variable as the Backup parameter value. Set the $nasServer variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Converting SMB or NFS File Shares by Enterprise NAS System on Which They Reside

|  |  |
| --- | --- |
| The example shows how to convert the File Backup Job 1 file shares that reside on an enterprise NAS system into a NAS filer share on the same storage. The cmdlet will find the backup on the NAS filer by the backup name.  |  | | --- | | $nasbackup = Get-VBRUnstructuredBackup -Name "File Backup Job 1"  $netapp = Get-NetAppHost -Name "pdc-ontap-1"  $netapp\_filer = Get-VBRUnstructuredServer -SANEntity $netapp  Convert-VBRNASBackupSANFormat -Backup $nasbackup -Server $netapp\_filer |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $nasbackup variable.  1. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter value. Save the result to the $netapp variable.  1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Set the $netapp variable as the SANEntity parameter value. Save the result to the $netapp\_filer variable.  1. Run the Convert-VBRNASBackupSANFormat cmdlet. Set the $nasBackup variable as the Backup parameter value. Set the $netapp\_filer variable as the Server parameter value. |

Related Commands

* [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md)
* [Get-NetAppHost](get-netapphost.md)
* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
