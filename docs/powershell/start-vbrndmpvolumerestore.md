---
title: "Start-VBRNDMPVolumeRestore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrndmpvolumerestore.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Start-VBRNDMPVolumeRestore


Short Description

Restores data from tape to an NDMP server.

Applies to

Product Edition: Enterprise

Syntax

This cmdlet provides parameter sets that allow you to:

* Restore to original NDMP server.

|  |
| --- |
| Start-VBRNDMPVolumeRestore -RestorePoint <VBRNDMPVolumeRestorePoint> -ToOriginalLocation [-RunAsync]  [<CommonParameters>] |

* Restore to another NDMP server.

|  |
| --- |
| Start-VBRNDMPVolumeRestore -RestorePoint <VBRNDMPVolumeRestorePoint> -Server <VBRNDMPServer> -Path <String> [-PreserveFolderHierarchy] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet restores data from the tape device to an NDMP server.

|  |
| --- |
| ![Start-VBRNDMPVolumeRestore](images/icon_note.webp) Note: |
| You can restore entire volumes only. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point to which you want to restore the selected volume. | Accepts the [VBRNDMPVolumeRestorePoint](vbrndmpvolumerestorepoint.md) object. To get this object, run the [Get-VBRNDMPVolumeRestorePoint](get-vbrndmpvolumerestorepoint.md) cmdlet. | True | Named | False |
| ToOriginalLocation | Defines that the cmdlet will start the restore to the original NDMP server. | SwitchParameter | True | Named | False |
| Server | For restore to another location.  Specifies the target NDMP server. Veeam Backup & Replication will restore the volumes to that server. | Accepts the [VBRNDMPServer](vbrndmpserver.md) object. To get this object, run the [Get-VBRNDMPServer](get-vbrndmpserver.md) cmdlet. | True | Named | False |
| Path | For restore to another location.  Specifies the path to the volume on the target NDMP server. Veeam Backup & Replication will restore the data to that volume. | String | True | Named | False |
| PreserveFolderHierarchy | For restore to another location.  Defines that Veeam Backup & Replication will preserve folder hierarchy. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CRestoreSession object that contains the restore session details.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Data from Tape to Original NDMP Server [Using Variable]

|  |  |
| --- | --- |
| This example shows how to restore data from tape to an original NDMP server.  |  | | --- | | $volume = Get-VBRNDMPVolume -Name "/svm-cifs/Exhcange\_vol"  $restorepoint = Get-VBRNDMPVolumeRestorePoint -Volume $volume  Start-VBRNDMPVolumeRestore -RestorePoint $restorepoint -ToOriginalLocation |  Perform the following steps:   1. Run the [Get-VBRNDMPVolume](get-vbrndmpvolume.md) cmdlet. Specify the Name parameter value. Save the result to the $volume variable. 2. Run the Get-VBRNDMPVolumeRestorePoint cmdlet. Set the $volume variable as the Volume parameter value. Save the result to the $restorepoint variable. 3. Run the Start-VBRNDMPVolumeRestore cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Provide the ToOriginalLocation parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Data from Tape to Another NDMP Server [Using Variable]

|  |  |
| --- | --- |
| This example shows how to restore data from tape to another NDMP server named NetApp.tech.local.  |  | | --- | | $volume = Get-VBRNDMPVolume -Name "/svm-cifs/Exhcange\_vol"  $restorepoint = Get-VBRNDMPVolumeRestorePoint -Volume $volume  $ndmpserver = Get-VBRNDMPServer -Name "NetApp.tech.local"  Start-VBRNDMPVolumeRestore -RestorePoint $restorepoint -Server $ndmpserver -Path "/svm-cifs/ks\_tapes" |  Perform the following steps:   1. Run the [Get-VBRNDMPVolume](get-vbrndmpvolume.md) cmdlet. Specify the Name parameter value. Save the result to the $volume variable. 2. Run the [Get-VBRNDMPVolumeRestorePoint](get-vbrndmpvolumerestorepoint.md) cmdlet. Set the $volume variable as the Volume parameter value. Save the result to the $restorepoint variable. 3. Run the [Get-VBRNDMPServer](get-vbrndmpserver.md) cmdlet. Specify the Name parameter value. Save the result to the $ndmpserver variable. 4. Run the Start-VBRNDMPVolumeRestore cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $ndmpserver variable as the Server parameter value. Specify the Path parameter value. |

Related Commands

* [Get-VBRNDMPVolume](get-vbrndmpvolume.md)
* [Get-VBRNDMPVolumeRestorePoint](get-vbrndmpvolumerestorepoint.md)
* [Get-VBRNDMPServer](get-vbrndmpserver.md)


