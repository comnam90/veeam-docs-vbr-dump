---
title: "Start-VBRCDPLinuxFileRestore"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrcdplinuxfilerestore.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Start-VBRCDPLinuxFileRestore

In this article

Short Description

Starts a restore session of Linux-based or Unix-based guest OS files from a CDP replica.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Start a restore session of Linux-based or Unix-based guest OS files using an existing Linux-based machine as a helper host.

|  |
| --- |
| Start-VBRCDPLinuxFileRestore -Replica <VBRCDPReplica> [-ToPointInTime <DateTime>] [-LongTermRestorePoint <VBRCDPLongTermRestorePoint>] [-Reason <string>] -MountServer <CHost>  [<CommonParameters>] |

* Start a restore session of Linux-based or Unix-based guest OS files using a temporary helper appliance.

|  |
| --- |
| Start-VBRCDPLinuxFileRestore -Replica <VBRCDPReplica> [-ToPointInTime <DateTime>] [-LongTermRestorePoint <VBRCDPLongTermRestorePoint>] [-Reason <string>] -ApplianceOptions <VBRFileRestoreLinuxHelperApplianceOptions>  [<CommonParameters>] |

* Start a restore session of Linux-based or Unix-based guest OS files using the original server as a helper host.

|  |
| --- |
| Start-VBRCDPLinuxFileRestore -Replica <VBRCDPReplica> [-ToPointInTime <DateTime>] [-LongTermRestorePoint <VBRCDPLongTermRestorePoint>] [-Reason <string>] [-Credentials <CCredentials>] [-MountToOriginalHost]  [<CommonParameters>] |

* Start a restore session using a Linux-based machine as a temporary helper host.

|  |
| --- |
| Start-VBRCDPLinuxFileRestore -Replica <VBRCDPReplica> [-Reason <string>] -HelperHost <VBRLinuxFileRestoreHelperHost>  [<CommonParameters>] |

Detailed Description

This cmdlet starts a restore session of guest OS files for a CDP replica that has Linux-based or Unix-based OS.

|  |
| --- |
| Note |
| Consider the following:   * If you plan to restore OS files using an existing Linux-based machine as a helper host, you must first add this machine to the backup infrastructure. Run the [Add-VBRLinux](add-vbrlinux.md) cmdlet to add the necessary machine. * After you restore the necessary files, you must stop the restore session. Run run the [Stop-VBRLinuxFileRestore](stop-vbrlinuxfilerestore.md) cmdlet to stop the session.   After you stop the session, Veeam Backup & Replication unmounts disks from the helper host or helper appliance. If you use the helper appliance, Veeam Backup & Replication unregisters the helper appliance from the ESXi host.   * This method supports recovery of files and folders only. Recovery of other file system objects such as pipes is not supported. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Replica | Specifies the CDP replica for which you want to restore files. | Accepts the VBRCDPReplica object. To create this object, run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| ToPointInTime | Specifies date and time when a restore point was created. The cmdlet will start the restore session for the short-term restore point created at the specified date and time or will take the nearest restore point. | Accepts the DateTime object. To get this object, run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) or [Get-VBRCDPShortTermRestoreInterval](get-vbrcdpshorttermrestoreinterval.md) cmdlet. | False | Named | False |
| LongTermRestorePoint | Specifies a long-term restore point of a CDP replica. The cmdlet will start the restore session for this restore point. | Accepts the VBRCDPLongTermRestorePoint object. To get this object, run the [Get-VBRCDPLongTermRestorePoint](get-vbrcdplongtermrestorepoint.md) cmdlet. | False | Named | False |
| Reason | Specifies the reason for starting a restore session.  The information you provide will be saved in the session history so that you can reference it later. | String | False | Named | True (ByPropertyName) |
| MountServer | Specifies an existing Linux-based machine. The cmdlet will mount disks from a backup or replica to this machine and will use it as a helper host.  Note: This parameter is required if you do not specify the ApplianceOptions and MountToOriginalHost parameters. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByPropertyName) |
| ApplianceOptions | Specifies configuration options for a temporary helper appliance.  Note: This parameter is required if you do not specify the MountServer and MountToOriginalHost parameters. | Accepts the VBRFileRestoreLinuxHelperApplianceOptions object. To create this object, run the [New-VBRFileRestoreLinuxHelperApplianceOptions](new-vbrfilerestorelinuxhelperapplianceoptions.md) cmdlet. | True | Named | True (ByPropertyName) |
| MountToOriginalHost | Specifies whether to mount disks to the original server and use it as a helper host.  Default: False.  Note: Set this parameter to $true if the Server, MountServer and ApplianceOptions parameters are not specified. | SwitchParameter | True | Named | True (ByPropertyName) |
| Credentials | Specifies the credentials to authenticate against an existing Linux-based machine that you want to use as a helper host.  Note: This parameter can be used only when MountToOriginalHost is true. | Accepts the CCredentials object. To create this object, run the  [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| HelperHost | Specifies the temporary Linux helper host. | Accepts the VBRLinuxFileRestoreHelperHost object. To get this object, run the [New-VBRLinuxFileRestoreHelperHost](new-vbrlinuxfilerestorehelperhost.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the FileRestore object that contains settings of a restore session of Linux-based or Unix-based guest OS files.

Examples

Starting Restore Session of Linux or Unix-Based Guest OS Files Using Existing Linux Machine as Helper Appliance

This example shows how to start a restore of Linux or Unix-based guest OS files of the UbuntuSrv replica. The cmdlet will use the LinSrv05 machine as a helper appliance.

|  |
| --- |
| $replica = Get-VBRCDPReplica -Name "UbuntuSrv"  $restorepoint = Get-VBRCDPLongTermRestorePoint -Replica $replica -Last  $server = Get-VBRServer -Name "LinSrv05"  $creds = Get-VBRCredentials -Name \*Administrator\*  $session = Start-VBRCDPLinuxFileRestore -Replica $replica -LongTermRestorePoint $restorepoint -MountServer $server -Credentials $creds |

Perform the following steps:

1. Get the restore point:

* Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable.
* Run the [Get-VBRCDPLongTermRestorePoint](get-vbrcdplongtermrestorepoint.md) cmdlet. Set the $replica variable as the Replica parameter value. Provide the Last parameter. Save the result to the $restorepoint variable.

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $creds variable.
3. Run the Start-VBRCDPLinuxFileRestore cmdlet:

* Set the $replica variable as the Replica parameter value.
* Set the $restorepoint variable as the LongTermRestorePoint parameter value.
* Set the $server variable as the MountServer parameter value.
* Set the $creds variable as the Credentials parameter value.
* Save the result to the $session variable.

Related Commands

* [Get-VBRCDPReplica](get-vbrcdpreplica.md)
* [Get-VBRCDPLongTermRestorePoint](get-vbrcdplongtermrestorepoint.md)
* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRCredentials](get-vbrcredentials.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
