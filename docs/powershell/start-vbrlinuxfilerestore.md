---
title: "Start-VBRLinuxFileRestore"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrlinuxfilerestore.html"
last_updated: "7/30/2025"
product_version: "13.0.1.1071"
---

# Start-VBRLinuxFileRestore

In this article

Short Description

Starts a restore session of Linux-based or Unix-based guest OS files.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Start a restore session of Linux-based or Unix-based guest OS files using the VMware platform.

|  |
| --- |
| Start-VBRLinuxFileRestore -RestorePoint <COib> [-Reason <String>] -Server <CHost> [-ResourcePool <CViResourcePoolItem>] [-NetworkInfo <IVBRServerNetworkInfo>] [-IP <IPAddress>] [-NetworkMask <String>] [-Gateway <IPAddress>] [-PreferredDNSServer <IPAddress>] [-AlternateDNSServer <IPAddress>] [-IPv6 <IPAddress>] [-IPv6PrefixLength <Int32>] [-IPv6Gateway <IPAddress>] [-IPv6PreferredDNSServer <IPAddress>] [-IPv6AlternateDNSServer <IPAddress>] [-FromNSS] [-EnableFTP] [-ShareCredentials <CCredentials>]  [<CommonParameters>] |

* Start a restore session of Linux-based or Unix-based guest OS files using the Hyper-V platform.

|  |
| --- |
| Start-VBRLinuxFileRestore -RestorePoint <COib> [-Reason <String>] -Server <CHost> [-NetworkInfo <IVBRServerNetworkInfo>] [-IP <IPAddress>] [-NetworkMask <String>] [-Gateway <IPAddress>] [-PreferredDNSServer <IPAddress>] [-AlternateDNSServer <IPAddress>] [-IPv6 <IPAddress>] [-IPv6PrefixLength <Int32>] [-IPv6Gateway <IPAddress>] [-IPv6PreferredDNSServer <IPAddress>] [-IPv6AlternateDNSServer <IPAddress>] [-VLanId <Int32>] [-EnableFTP] [-ShareCredentials <CCredentials>]  [<CommonParameters>] |

* Start a restore session of Linux-based or Unix-based guest OS files using an existing Linux-based machine as a helper host.

|  |
| --- |
| Start-VBRLinuxFileRestore -RestorePoint <COib> [-Reason <string>] -MountServer <CHost> [-ShareCredentials <CCredentials>]  [<CommonParameters>] |

* Start a restore session of Linux-based or Unix-based guest OS files using the original server as a helper host.

|  |
| --- |
| Start-VBRLinuxFileRestore -RestorePoint <COib> [-Reason <String>] [-Credentials <CCredentials>] [-ShareCredentials <CCredentials>] -MountToOriginalHost  [<CommonParameters>] |

* Start a restore session using a Linux-based machine as a temporary helper host.

|  |
| --- |
| Start-VBRLinuxFileRestore -RestorePoint <COib> [-Reason <String>] -HelperHost <VBRLinuxFileRestoreHelperHost> [-ShareCredentials <CCredentials>]  [<CommonParameters>] |

* Start a restore session using a Linux-based machine as a temporary helper appliance.

|  |
| --- |
| Start-VBRLinuxFileRestore -RestorePoint <COib> -ApplianceOptions <VBRFileRestoreLinuxHelperApplianceOptions> [-Reason <String>] [-ShareCredentials <CCredentials>] -ApplianceOptions <VBRFileRestoreLinuxHelperApplianceOptions>  [<CommonParameters>] |

Detailed Description

This cmdlet mounts disks from a backup or replica to the helper host or helper appliance. After that you can restore VM guest OS files from file systems supported by Linux-based and Unix-based OSes:

1. Run the [Get-VBRLinuxGuestItem](get-vbrlinuxguestitem.md) cmdlet to get details on the files and folders that are available for restore.
2. Run the [Start-VBRLinuxGuestItemRestore](start-vbrlinuxguestitemrestore.md) cmdlet to restore the necessary files and folders.

|  |
| --- |
| Note |
| Consider the following:   * If you plan to restore OS files using an existing Linux-based machine as a helper host, you must first add this machine to the backup infrastructure. Run the [Add-VBRLinux](add-vbrlinux.md) cmdlet to add the necessary machine. * After you restore the necessary files, you must stop the restore session. Run the [Stop-VBRLinuxFileRestore](stop-vbrlinuxfilerestore.md) cmdlet to stop the session.   After you stop the session, Veeam Backup & Replication unmounts disks from the helper host or helper appliance. If you use the helper appliance, Veeam Backup & Replication unregisters the helper appliance from the ESXi or Microsoft Hyper-V host.   * This method supports recovery of files and folders only. Recovery of other file system objects such as pipes is not supported. |

|  |
| --- |
| Tip |
| To start a restore session for a CDP replica, use the [Start-VBRCDPLinuxFileRestore](start-vbrcdplinuxfilerestore.md) cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point to start a restore session. You will be able to use the session to perform operations with VM guest OS files. | Accepts the COib object. To create this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | True (ByValue, |
| HelperHost | Specifies the temporary Linux helper host. | Accepts the VBRLinuxFileRestoreHelperHost object. To get this object, run the [New-VBRLinuxFileRestoreHelperHost](new-vbrlinuxfilerestorehelperhost.md) cmdlet. | True | Named | False |
| ApplianceOptions | Specifies configuration settings for a temporary helper appliance. | Accepts the VBRLinuxFileRestoreHelperHost object. To get this object, run the [New-VBRFileRestoreLinuxHelperApplianceOptions](new-vbrfilerestorelinuxhelperapplianceoptions.md) cmdlet. | True | Named | False |
| Server | Specifies the ESXi or Microsoft Hyper-V host on which the helper appliance must be registered.  Note: If you specify a host for the Novell file system proxy appliance, make sure that it can run VMs with 64-bit guest OSes. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | True (ByProperty Name) |
| ResourcePool | To start a restore session using the VMware platform.  Specifies the resource pool to which the helper appliance must be placed. | Accepts the CViResourcePoolItem object. To get this object, run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. | False | Named | True (ByProperty Name) |
| MountServer | Specifies an existing Linux-based machine. The cmdlet will mount disks from a backup or replica to this machine and will use it as a helper host. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| MountToOriginalHost | Specifies whether to mount disks to the original server and use it as a helper host.  Default: False.  Note: You can set this parameter to $true only if the Server and MountServer parameters are not specified. | SwitchParameter | False | Named | True (ByProperty Name) |
| Reason | Specifies the reason for starting restore.  The information you provide will be saved in the session history so that you can reference it later. | String | False | Named | False |
| NetworkInfo | Specifies the network settings for the helper appliance.  Note:   * The helper appliance must be placed in the same network where the backup server resides. * If you do not provide this parameter, the cmdlet will apply the VM network settings for the helper appliance. | Accepts the IVBRServerNetworkInfo[] object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| IP | Specifies the IPv4 address that you want to assign to the helper appliance.  Note: The helper appliance must be placed in the same network where the backup server resides. | IPAddress | False | Named | False |
| NetworkMask | For the IP parameter specified.  Specifies the network mask that you want to assign to the helper appliance.  Note: The helper appliance must be placed in the same network where the backup server resides. | String | False | Named | False |
| PreferredDNSServer | Specifies the IPv4 address of the DNS server in the network where the helper appliance resides. | IPAddress | False | Named | False |
| AlternateDNSServer | Specifies the IPv4 address of the alternate DNS server in the network where the helper appliance resides. | IPAddress | False | Named | False |
| Gateway | Specifies the IPv4 address of the default gateway in the network where the helper appliance resides. | IPAddress | False | Named | False |
| IPv6 | Specifies the IPv6 address that you want to assign to the helper appliance.  Note: The helper appliance must be placed in the same network where the backup server resides. | IPAddress | False | Named | False |
| IPv6PrefixLength | For the IPv6 addresses specified.  Specifies the length of the IPv6 prefix. | Int32 | False | Named | False |
| IPv6PreferredDNSServer | Specifies the IPv6 address of the DNS server in the network where the helper appliance resides. | IPAddress | False | Named | False |
| IPv6AlternateDNSServer | Specifies the IPv6 address of the alternate DNS server in the network where the appliance resides. | IPAddress | False | Named | False |
| IPv6Gateway | Specifies the IPv6 address of the default gateway in the network where the appliance resides. | IPAddress | False | Named | False |
| VLanId | To start a restore session using the Hyper-V platform.  Specifies the VLAN ID where the helper appliance must reside. | Int | False | Named | False |
| FromNSS | Defines that the cmdlet will start a restore session of a VM guest OS using the Novell Storage Services file system.  If you provide this parameter, the cmdlet will deploy a specific appliance that supports the Novell Storage Services file system.  Default: False. | SwitchParameter | False | Named | False |
| EnableFTP | Enables the FTP access to the restored file system.  If you provide this parameter, users will be able to access the helper appliance over FTP, browse the file system of the restored VM and download necessary files on their own.  Default: False. | SwitchParameter | False | Named | False |
| ShareCredentials | Specifies the credentials to authenticate against a backup repository where the backup from which you restore is stored.  Note: This parameter is required if you restore files using a helper appliance from a backup imported from an SMB share. This applies if the server where the share is located and the share itself is not added to the backup infrastructure. | Accepts the CCredentials object. To create this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| Credentials | Specifies the credentials to authenticate against the original Linux-based machine that will be used as a helper host.  Note: This parameter can be used only when MountToOriginalHost is true. | Accepts the CCredentials object. To create this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRLinuxFlrObject object that contains settings of a restore session of VM guest OS files from file systems supported by Linux-based and Unix-based OSes.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Restore Session of Linux or Unix-Based Guest OS Files Using VMware

|  |  |
| --- | --- |
| This example shows how to start a restore session of Linux or Unix-based guest OS files of the UbuntuSrv VM. The cmdlet will register a helper appliance on the ESXi01 host in the Servers resource pool.  |  | | --- | | $backup = Get-VBRBackup -Name "UbuntuSrv"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $server = Get-VBRServer -Name "ESXi01"  $resourcepool = Find-VBRViResourcePool -Server $server -Name "Servers"  $session = Start-VBRLinuxFileRestore -RestorePoint $restorepoint -Server $server -ResourcePool $resourcepool |  Perform the following steps:   1. Get the restore point:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. * Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable.  1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the result to the $resourcepool variable. 3. Run the Start-VBRLinuxFileRestore cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Set the $server variable as the Server parameter value. * Set the $resourcepool variable as the ResourcePool parameter value. * Save the result to the $session variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting Restore Session of Linux or Unix-Based Guest OS Files Using Hyper-V

|  |  |
| --- | --- |
| This example shows how to start a restore session of Linux or Unix-based guest OS files of the UbuntuSrv VM. The cmdlet will register a helper appliance on the HV05 Hyper-V host.  |  | | --- | | $backup = Get-VBRBackup -Name "UbuntuSrv"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $server = Get-VBRServer -Name "HV05"  $session = Start-VBRLinuxFileRestore -RestorePoint $restorepoint -Server $server |  Perform the following steps:   1. Get the restore point:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. * Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable.  1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Start-VBRLinuxFileRestore cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $server variable as the Server parameter value. Save the result to the $session variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Starting Restore Session of Linux or Unix-Based Guest OS Files Using Existing Linux Machine as Helper Host

|  |  |
| --- | --- |
| This example shows how to start a restore of Linux or Unix-based guest OS files of the UbuntuSrv VM. The cmdlet will use the LinSrv05 machine as a helper host.  |  | | --- | | $backup = Get-VBRBackup -Name "UbuntuSrv"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $server = Get-VBRServer -Name "LinSrv05"  $session = Start-VBRLinuxFileRestore -RestorePoint $restorepoint -MountServer $server |  Perform the following steps:   1. Get the restore point:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. * Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable.  1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Start-VBRLinuxFileRestore cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $server variable as the MountServer parameter value. Save the result to the $session variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Starting Restore Session of Linux or Unix-Based Guest OS Files Using Original Server

|  |  |
| --- | --- |
| This example shows how to start a restore of Linux or Unix-based guest OS files of the UbuntuSrv VM. The cmdlet will use the original VM as a helper appliance.  |  | | --- | | $backup = Get-VBRBackup -Name "UbuntuSrv"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $credentials = Get-VBRCredentials -Name "root"  $session = Start-VBRLinuxFileRestore -RestorePoint $restorepoint -Credentials $credentials -MountToOriginal |  Perform the following steps:   1. Get the restore point:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. * Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable.  1. Run [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $credentials variable. 2. Run the Start-VBRLinuxFileRestore cmdlet.  * Set the $restorepoint variable as the RestorePoint parameter value. * Set the $credentials variable as the Credentials parameter value. * Specify the MountToOriginal parameter. * Save the result to the $session variable. |

Related Commands

* [Get-VBRBackup](get-vbrrestorepoint.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViResourcePool](find-vbrviresourcepool.md)

Page updated 7/30/2025

Page content applies to build 13.0.1.1071
