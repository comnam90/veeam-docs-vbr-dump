---
title: "Install-VBRLinuxTransportService"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/install-vbrlinuxtransportservice.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Install-VBRLinuxTransportService


Short Description

Installs Veeam Data Mover for guest processing on Linux VMs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Install-VBRLinuxTransportService -Entity <IVmItem[]> -SSHUser <string> -SSHPassword <string> [-SSHPort <int>] [-SSHElevateToRoot] [-SSHAddToSudoers] [-SSHFailoverToSu] [-SSHRootPassword <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet installs Veeam Data Mover for guest processing on Linux VMs. For more information on Linux distibutives, for which guest processing is supported, see the [Platform Support](https://helpcenter.veeam.com/docs/vbr/userguide/platform_support.html?ver=13) section of Veeam Backup & Replication User Guide.

After you install Veeam Data Mover, Veeam Backup & Replication will use it for guest processing tasks.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Entity | Specifies an array of Linux VMs to which you want to install Veeam Data Mover. | Accepts the IVmItem[] object. To get this object, run the [Find-VBRHvEntity](find-vbrhventity.md),[Find-VBRViEntity](find-vbrvientity.md) or [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlets. | True | Named | True (ByValue, ByPropertyName) |
| SSHUser | Specifies the user name you want to use for authenticating with the Linux VMs. | String | True | Named | False |
| SSHPassword | Specifies the password you want to use for authenticating with the Linux VMs. | String | True | Named | False |
| SSHPort | Specifies the Web service port for connection to the Linux server.  Default: 22. | Int | False | Named | False |
| SSHElevateToRoot | Defines that non-root users are provided with the root account privileges. | SwitchParameter | False | Named | False |
| SSHAddToSudoers | Defines that the user account is added to the sudoers file.  Default: (if the ElevateToRoot parameter is set to False) | SwitchParameter | False | Named | False |
| SSHFailoverToSu | Defines that Veeam Backup & Replication will use the su command if the sudo command fails.  If you do not provide this parameter and sudo fails, Veeam Backup & Replication will not be able to connect to a Linux VMs. | SwitchParameter | False | Named | False |
| SSHRootPassword | Specifies the root password used for authentication. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRLinuxTransportService object that contains Veeam Data Mover settings for guest processing on a Linux VM.

Examples

Installing Veeam Data Mover to Linux VM

This example shows how to install Veeam Data Mover to the Lin2049 Linux VM.

|  |
| --- |
| $linVm = Find-VBRViEntity -Name "Lin2049"  Install-VBRLinuxTransportService -Entity $linVm -SSHUser Administrator -SSHPassword XXXXXXXXXX -SSHElevateToRoot -SSHAddToSudoers -SSHFailoverToSu -SSHRootPassword XXXXXXXXXX |

Perform the following steps:

1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $linsrv variable.
2. Run the Install-VBRLinuxTransportService cmdlet. Specify the following settings:

* Set the $linVm variable as the Entity parameter value.
* Specify the SSHUser parameter value.
* Specify the SSHPassword parameter value.
* Provide the SSHElevateToRoot parameter.
* Provide the SSHAddToSudoers parameter.
* Provide the SSHFailoverToSu parameter.
* Specify the SSHRootPassword parameter value.

Related Commands

* [Find-VBRViEntity](find-vbrvientity.md)
* [Find-VBRHvEntity](find-vbrhventity.md)
* [Find-VBRvCloudEntity](find-vbrvcloudentity.md)


