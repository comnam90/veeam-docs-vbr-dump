---
title: "New-VBRRepositoryMountServerOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrrepositorymountserveroptions.html"
last_updated: "7/17/2025"
product_version: "13.0.1.1071"
---

# New-VBRRepositoryMountServerOptions

In this article

Short Description

Defines settings of a mount server.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRRepositoryMountServerOptions [-MountServer <CHost>] [-EnableVPowerNFS] [-VPowerNFSPort <int>] [-MountPort <int>] [-MountFolder <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRRepositoryMountServerOptions](vbrrepositorymountserveroptions.md) object. This object contains settings of a mount server that you can assign to a backup repository and use for restore operations.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| MountServer | Specifies a server that you want to use as a mount server. The cmdlet will apply settings to this server.  Note: If you do not specify this parameter, the cmdlet will apply settings to the backup server. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| EnableVPowerNFS | Enables the Veeam vPower NFS Service on the mount server. If you enable this option, Veeam vPower NFS Service will be able to access the backup repository.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| VPowerNFSPort | Specifies the port that the Veeam vPower NFS Service will use to connect to the target NFS share.  Default: 2049. | Int | False | Named | False |
| MountPort | Specifies the port that the Veeam vPower NFS Service will use to mount the vPower NFS datastore to the ESXi host.  Default: 1058. | Int | False | Named | False |
| MountFolder | Specifies a folder to keep cache that is created during mount operations. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRRepositoryMountServerOptions](vbrrepositorymountserveroptions.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Settings for Default Mount Server

|  |  |
| --- | --- |
| This command defines settings for a backup server that Veeam Backup & Replication will use as the mount server. Save the result to a variable to use with other cmdlets.  |  | | --- | | $mountoptions = New-VBRRepositoryMountServerOptions -EnableVPowerNFS -MountFolder "C:\ProgramData\Veeam\Backup\IRCache\" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Settings for Specific Mount Server

|  |  |
| --- | --- |
| This example shows how to define settings for the WinSrv2047 mount server.  |  | | --- | | $server = Get-VBRServer -Name "WinSrv2047"  $mountoptions = New-VBRRepositoryMountServerOptions -MountServer $server -EnableVPowerNFS -MountFolder "C:\ProgramData\Veeam\Backup\IRCache\" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the New-VBRRepositoryMountServerOptions cmdlet. Set the $server variable as the MountServer parameter value. Provide the EnableVPowerNFS parameter. Specify the MountFolder parameter value.   Save the result to the $mountoptions variable to use with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Disabling Veeam PowerNFS Settings for Specific Mount Server

|  |  |
| --- | --- |
| This example shows how to define settings for the WinSrv2047 mount server. The Veeam PowerNFS option will be disabled.  |  | | --- | | $server = Get-VBRServer -Name "WinSrv2047"  $mountoptions = New-VBRRepositoryMountServerOptions -MountServer $server -EnableVPowerNFS:$false -MountFolder "C:\ProgramData\Veeam\Backup\IRCache\" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.  1. Run the New-VBRRepositoryMountServerOptions cmdlet. Set the $server variable as the MountServer parameter value. Provide the :$false value for the EnableVPowerNFS parameter. Specify the MountFolder parameter value.   Save the result to the $mountoptions variable to use with other cmdlets. |

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 7/17/2025

Page content applies to build 13.0.1.1071
