---
title: "Set-VBRLinuxFileRestoreHelperHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrlinuxfilerestorehelperhost.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Set-VBRLinuxFileRestoreHelperHost

In this article

Short Description

Modifies temporary Linux helper host specifications.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify the connectivity options using credentials that already exist in Veeam Backup & Replication.

|  |
| --- |
| Set-VBRLinuxFileRestoreHelperHost [-Credentials <CCredentials>] [-Force] -HelperHost <VBRLinuxFileRestoreHelperHost> [-SSHFingerprint <string>]  [<CommonParameters>] |

* Modify the connectivity options by specifying each SSH option separately.

|  |
| --- |
| Set-VBRLinuxFileRestoreHelperHost [-Force] -HelperHost <VBRLinuxFileRestoreHelperHost> [-SSHAddToSudoers] [-SSHElevateToRoot] [-SSHFailoverToSu] [-SSHFingerprint <string>] -SSHPassword <string> [-SSHPort <int>] [-SSHRootPassword <string>] -SSHUser <string>  [<CommonParameters>] |

Detailed Description

This cmdlet modifies temporary Linux helper host specifications.

Note that the cmdlet creates a copy of the HelperHost you provide in a command. To use the new helper host, you must assign it to a variable.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Credentials | Specifies the credentials you want to use for authenticating with the Linux server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will modify temporary Linux helper host specification without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| HelperHost | Specifies the temporary Linux helper host. | Accepts the VBRLinuxFileRestoreHelperHost object. To get this object, run the [New-VBRLinuxFileRestoreHelperHost](new-vbrlinuxfilerestorehelperhost.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| SSHAddToSudoers | Defines that the user account is added to sudoers file.  Default: False. | SwitchParameter | False | Named | False |
| SSHElevateToRoot | Defines that non-root users are provided with the root account privileges.  Default: False. | SwitchParameter | False | Named | False |
| SSHFailoverToSu | Defines that Veeam Backup & Replication will use the su command if the sudo command fails.  Default: False. | SwitchParameter | False | Named | False |
| SSHFingerPrint | Specifies the SSH host fingerprint. | String | False | Named | False |
| SSHPassword | Specifies the password you want to use for authenticating with the Linux server. | String | True | Named | False |
| SSHPort | Specifies the SSH port for connection to the Linux server.  Default: 22. | Int32 | False | Named | False |
| SSHRootPassword | Specifies the root password used for authentication. | String | False | Named | False |
| SSHUser | Specifies the user name you want to use for authenticating with the Linux server. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRLinuxFileRestoreHelperHost object that contains settings for a temporary Linux helper host specifications.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Connectivity Options Using Existing Credentials

|  |  |
| --- | --- |
| This example shows how to modify the connectivity options using the credentials that already exist in Veeam Backup & Replication.  |  | | --- | | $cred1 = Get-VBRCredentials -Name "root"  $cred2 = Get-VBRCredentials -Name "Linux Admin"  $hh1 = New-VBRLinuxFileRestoreHelperHost -Force -Name "154.19.90.152" -Credentials $cred1  $hh2 = Set-VBRLinuxFileRestoreHelperHost -HelperHost $hh1 -Credentials $cred2 |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $cred1 variable. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $cred2 variable. 3. Run the [New-VBRLinuxFileRestoreHelperHost](new-vbrlinuxfilerestorehelperhost.md) cmdlet. Provide the Force parameter. Specify the Name parameter value. Set the $cred1 variable as the Credentials parameter value. Save the result to the $hh1 variable. 4. Run the Set-VBRLinuxFileRestoreHelperHost cmdlet. Set the $hh1 variable as the HelperHost parameter value. Set the $cred2 variable as the Credentials parameter value. Save the result to the $hh2 variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Connectivity Options by Specifying SSH Options

|  |  |
| --- | --- |
| This example shows how to modify the connectivity options by specifying each SSH option separately.  |  | | --- | | $cred1 = Get-VBRCredentials -Name "root"  $hh1 = New-VBRLinuxFileRestoreHelperHost -Force -Name "Linux User" -Credentials $cred1  $hh2 = Set-VBRLinuxFileRestoreHelperHost -HelperHost $hh1 -SSHUser LinuxUser -SSHPassword P@ssw0rd -SSHElevateToRoot |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $cred1 variable. 2. Run the [New-VBRLinuxFileRestoreHelperHost](new-vbrlinuxfilerestorehelperhost.md) cmdlet. Provide the Force parameter. Specify the Name parameter value. Set the $cred1 variable as the Credentials parameter value. Save the result to the $hh1 variable. 3. Run the Set-VBRLinuxFileRestoreHelperHost cmdlet.  Specify the following settings:  * Set the $hh1 variable as the HelperHost parameter value. * Specify the SSHUser parameter value. * Specify the SSHPassword parameter value. * Provide the SSHElevateToRoot parameter.   Save the result to the $hh2 variable. |

Related Commands

* [Get-VBRCredentials](get-vbrcredentials.md)
* [New-VBRLinuxFileRestoreHelperHost](new-vbrlinuxfilerestorehelperhost.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
