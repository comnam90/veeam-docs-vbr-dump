---
title: "Set-VBRDefaultLinuxMountServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrdefaultlinuxmountserver.html"
last_updated: "7/22/2025"
product_version: "13.0.1.1071"
---

# Set-VBRDefaultLinuxMountServer


Short Description

Modifies the default Linux mount server.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Configure the default Linux mount server settings from scratch.

|  |
| --- |
| Set-VBRDefaultLinuxMountServer -MountServer <CHost> -MountFolder <string> [-MountPort <int>] [-EnableVPowerNFS] [-VPowerNFSPort <int>]  [<CommonParameters>] |

* Apply existing mount server settings to the default Linux mount server.

|  |
| --- |
| Set-VBRDefaultLinuxMountServer -Options <VBRRepositoryMountServerOptions>  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the default Linux mount server and its settings.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| MountServer | Specifies the server that you want to use as a default Linux mount server. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| EnableVPowerNFS | Enables the Veeam vPower NFS Service on the default mount server. If you enable this option, Veeam vPower NFS Service will be be able to access the backup repository.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| VPowerNFSPort | Specifies the port that the Veeam vPower NFS Service will use to connect to the target NFS share.  Default: 2049. | Int32 | False | Named | False |
| MountPort | Specifies the port that the Veeam vPower NFS Service will use to mount the vPower NFS datastore to the ESXi host.  Default: 1058. | Int32 | False | Named | False |
| MountFolder | Specifies the folder to keep cache that is created during mount operations. | String | True | Named | False |
| Options | Specifies mount server settings. | Accepts the VBRRepositoryMountServerOptions object. To get this object, run the [New-VBRRepositoryMountServerOptions](new-vbrrepositorymountserveroptions.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRDefaultLinuxMountServer](vbrdefaultlinuxmountserver.md)

Examples

Configuring Default Linux Mount Server

This example shows how to configure the default Linux mount server.

|  |
| --- |
| $linux\_mount = Get-VBRServer -Name "linuxsrv.tech.local"  Set-VBRDefaultLinuxMountServer -MountServer $linux\_mount -MountFolder "/var/lib/veeamdata/veeam/IRCache/" -EnableVPowerNFS |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $linux\_mount variable.
2. Run the Set-VBRDefaultLinuxMountServer cmdlet. Set the $linux\_mount variable as the MountServer parameter value. Specify the MountFolder parameter value. Provide the EnableVPowerNFS parameter.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRRepositoryMountServerOptions](get-vbrrepositorymountserveroptions.md)


