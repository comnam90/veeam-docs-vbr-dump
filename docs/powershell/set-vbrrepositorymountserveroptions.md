---
title: "Set-VBRRepositoryMountServerOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrrepositorymountserveroptions.html"
last_updated: "7/17/2025"
product_version: "13.0.1.1071"
---

# Set-VBRRepositoryMountServerOptions


Short Description

Modifies settings of a mount server.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRRepositoryMountServerOptions -Options <VBRRepositoryMountServerOptions> [-MountServer <CHost>] [-EnableVPowerNFS] [-VPowerNFSPort <int>] [-MountPort <int>] [-MountFolder <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of a mount server that you can assign to a backup repository and use for restore operations.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies settings of a mount server that you want to modify. | Accepts the VBRRepositoryMountServerOptions object. To get this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | True | Named | False |
| MountServer | Specifies a server that you want to use as a mount server. The cmdlet will apply settings to this server.  Note: If you do not specify this parameter, the cmdlet will apply settings to the backup server. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| EnableVPowerNFS | Enables the Veeam vPower NFS Service on the mount server. If you enable this option, Veeam vPower NFS Service will be be able to access the backup repository.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| VPowerNFSPort | Specifies the port that the Veeam vPower NFS Service will use to connect to the target NFS share.  Default: 2049. | Int | False | Named | False |
| MountPort | Specifies the port that the Veeam vPower NFS Service will use to mount the vPower NFS datastore to the ESXi host.  Default: 1058. | Int | False | Named | False |
| MountFolder | Specifies a folder to keep cache that is created during mount operations. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRRepositoryMountServerOptions](vbrrepositorymountserveroptions.md)

Examples

Modifying Cache Folder Settings for Mount Server

This example shows how to specify a new cache folder for the WinSrv2047 mount server. The mount server will keep cache in the C:\Backup\Veeam\IRCache\ folder instead of the default C:\ProgramData\Veeam\Backup\IRCache\ folder.

|  |
| --- |
| $server = Get-VBRServer -Name "WinSrv2047"  $mountoptions = New-VBRRepositoryMountServerOptions -MountServer $server -EnableVPowerNFS -MountFolder "C:\ProgramData\Veeam\Backup\IRCache\"  Set-VBRRepositoryMountServerOptions -Options $mountoptions -MountFolder "C:\Backup\Veeam\IRCache\" |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. Specify the MountServer, EnableVPowerNFS and MountFolder parameters. Save the result to the $mountoptions variable.
3. Run the Set-VBRRepositoryMountServerOptions cmdlet. Set the $mountoptions variable as the Options parameter value. Specify the MountFolder parameter value.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md)


