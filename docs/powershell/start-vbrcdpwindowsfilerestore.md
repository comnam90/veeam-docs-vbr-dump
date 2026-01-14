---
title: "Start-VBRCDPWindowsFileRestore"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrcdpwindowsfilerestore.html"
last_updated: "7/30/2025"
product_version: "13.0.1.1071"
---

# Start-VBRCDPWindowsFileRestore

In this article

Short Description

Starts Microsoft Windows guest OS file restore session for a CDP replica.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Start a guest OS file restore session for a short-term restore point.

|  |
| --- |
| Start-VBRCDPWindowsFileRestore -Replica <VBRCDPReplica> [-ToPointInTime <DateTime>] [-Reason <String>] [-Credentials <CCredentials>] [-MountHost <CHost>] [<CommonParameters>] |

* Start a guest OS file restore session for a long-term restore point.

|  |
| --- |
| Start-VBRCDPWindowsFileRestore -Replica <VBRCDPReplica> -LongTermRestorePoint <VBRCDPLongTermRestorePoint> [-Reason <String>] [-Credentials <CCredentials>]  [<CommonParameters>] |

Detailed Description

This cmdlet starts a restore session of guest OS files for a CDP replica that has Microsoft Windows OS.

After you restore the necessary files, you must stop the restore session. After you stop the session, Veeam Backup & Replication will unmount disks from the mount server. Run the [Stop-VBRWindowsFileRestore](stop-vbrwindowsfilerestore.md) cmdlet to stop the restore session.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Replica | Specifies the CDP replica for which you want to restore files. | Accepts the VBRCDPReplica object. To create this object, run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| ToPointInTime | Specifies date and time when a restore point was created. The cmdlet will start the restore session for the short-term restore point created at the specified date and time or will take the nearest restore point.  If you do not specify this parameter and the LongTermRestorePoint parameter, the cmdlet will start the restore session for the latest short-term restore point. | Accepts the DateTime object. To get this object, run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) or [Get-VBRCDPShortTermRestoreInterval](get-vbrcdpshorttermrestoreinterval.md) cmdlet. | False | Named | False |
| LongTermRestorePoint | Specifies a long-term restore point of a CDP replica. The cmdlet will start the restore session for this restore point. | Accepts the VBRCDPLongTermRestorePoint object. To get this object, run the [Get-VBRCDPLongTermRestorePoint](get-vbrcdplongtermrestorepoint.md) cmdlet. | True | Named | False |
| Reason | Specifies the reason for starting a restore session.  The information you provide will be saved in the session history so that you can reference it later. | String | False | Named | False |
| Credentials | Specifies the credentials to authenticate with the backup share folder. | Accepts the CCredentials object. To create this object, run the  [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| MountHost | Specifies the mount server to which machine disks will be mounted. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the FileRestore object that contains settings of a restore session of Windows guest OS files.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Restore Session from a Long-Term Restore Point for CDP Replica

|  |  |
| --- | --- |
| This example shows how to start a restore session for Windows guest OS files of the WinSrv25 CDP replica. The cmdlet will start the session for a long-term restore point.  |  | | --- | | $replica = Get-VBRCDPReplica -Name "WinSrv25"  $restorepoint = Get-VBRCDPLongTermRestorePoint -Replica $replica -Last  $session = Start-VBRCDPWindowsFileRestore -Replica $replica -LongTermRestorePoint $restorepoint |  Perform the following steps:   1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable. 2. Run the [Get-VBRCDPLongTermRestorePoint](get-vbrcdplongtermrestorepoint.md) cmdlet. Set the $replica variable as the Replica parameter value. Provide the Last parameter value. Save the result to the $restorepoint variable. 3. Run the Start-VBRCDPWindowsFileRestore cmdlet. Set the $replica variable as the Replica parameter value. Set the $restorepoint variable as the LongTermRestorePoint parameter value. Save the result to the $session variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting Restore Session from a Short-Term Restore Point for CDP Replica

|  |  |
| --- | --- |
| This example shows how to start a restore session for Windows guest OS files of the WinSrv25 CDP replica. The cmdlet will start the session for a short-term restore point.  |  | | --- | | $replica = Get-VBRCDPReplica -Name "WinSrv25"  $session = Start-VBRCDPWindowsFileRestore -Replica $replica -ToPointInTime "10/28/2023 12:33:39 PM" |  Perform the following steps:   1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable. 2. Run the Start-VBRCDPWindowsFileRestore cmdlet. Set the $replica variable as the Replica parameter value. Specify the ToPointInTime parameter value. Save the result to the $session variable. |

Related Commands

* [Get-VBRCDPReplica](get-vbrcdpreplica.md)
* [Get-VBRCDPShortTermRestoreInterval](get-vbrcdpshorttermrestoreinterval.md)
* [Get-VBRCDPLongTermRestorePoint](get-vbrcdplongtermrestorepoint.md)
* [Get-VBRCredentials](get-vbrcredentials.md)

Page updated 7/30/2025

Page content applies to build 13.0.1.1071
