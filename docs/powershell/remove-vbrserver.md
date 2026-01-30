---
title: "Remove-VBRServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrserver.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRServer


Short Description

Removes hosts from the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRServer -Server <CHost[]> [-SSHUser <String>] [SSHPassword <String>] [-SSHPort <Int32>] [-SSHElevateToRoot] [-SSHFailoverToSu] [-SSHRootPassword <String>] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a host from the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the array of servers you want to remove. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | 0 | True (ByValue, |
| SSHElevateToRoot | Defines that non-root users are provided with the root account privileges.  Default: False. | SwitchParameter | False | Named | False |
| SSHFailoverToSu | Defines that Veeam Backup & Replication will use the su command if the sudo command failes.  If you provide this parameter, Veeam Backup & Replication will failover to the su command if the sudo command fails. Otherwise, if sudo failes Veeam Backup & Replication will not be able to add Linux credentials records.  Default: False. | SwitchParameter | False | Named | False |
| SSHPasword | Specifies the password you want to use for authenticating with the Linux server.  Note: To add a Linux host using an SSH key fingerprint, provide the Confirm parameter. | String | False | Named | False |
| SSHPort | Specifies the Web service port for the connection to the Linux server console. | Int32 | False | Named | False |
| SSHRootPassword | Specifies the root password used for authentication. | String | False | Named | False |
| SSHUser | Specifies the user name you want to use for authenticating with the Linux server.  Note: To add a Linux host using an SSH key fingerprint, provide the Confirm parameter. | String | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Hyper-V Cluster from Backup Infrastructure

|  |  |
| --- | --- |
| This example shows how to remove the Production05 Hyper-V cluster from the backup infrastructure.  |  | | --- | | $server = Get-VBRServer -Type "HvCluster" -Name "Production05"  Remove-VBRServer -Server $server |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Type and the Name parameter values. Save the result to the $server variable. 2. Run the Remove-VBRServer cmdlet. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Virtual Center from Backup Infrastructure

|  |  |
| --- | --- |
| This example shows how to remove the vCenter01 Virtual Center from the backup infrastructure.  |  | | --- | | Get-VBRServer -Type "VC" -Name "vCenter01" | Remove-VBRServer |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Type and the Name parameter values. 2. Pipe the cmdlet output to the Remove-VBRServer cmdlet. |

Related Commands

[Get-VBRServer](get-vbrserver.md)


