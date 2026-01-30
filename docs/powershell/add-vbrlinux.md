---
title: "Add-VBRLinux"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrlinux.html"
last_updated: "12/1/2025"
product_version: "13.0.1.1071"
---

# Add-VBRLinux


Short Description

Adds a Linux server to the backup infrastructure.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Add a Linux host using credentials for authentication.

|  |
| --- |
| Add-VBRLinux -Name <string> -Credentials <CCredentials> [-Description <string>] [-SSHPort <int>] [-SSHFingerprint <String>] [-Package <VBRLinuxPackage[]>] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Add a Linux host using the Username/Password for authentication.

|  |
| --- |
| Add-VBRLinux -Name <string> -SSHUser <string> -SSHPassword <string> [-Description <string>] [-SSHPort <int>] [-SSHElevateToRoot] [-SSHAddToSudoers] [-SSHFailoverToSu] [-SSHRootPassword <string>] [-SSHTempCredentials] [-SSHFingerprint <String>] [-Package <VBRLinuxPackage[]>] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Add a Linux host using a certificate for authentication.

|  |
| --- |
| Add-VBRLinux -Name <String> [-Description <String>] [-UseCertificate] [-ForceDeployerFingerprint] [-HandshakeCode <String>] [-Package <VBRLinuxPackage[]>] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet adds a Linux server to the backup infrastructure.

|  |
| --- |
| Note |
| Consider the following:   * A Linux host that you want to add to the backup infrastructure must have SSH connection enabled. * If you plan to use non-persistent Veeam Data Movers, you must install Perl on a Linux host that you want to add to the backup infrastructure. * A Linux host that you add as a temporary helper appliance is not displayed in the Veeam Backup & Replication UI. Use this host to perform Linux-based or Unix-based guest OS files restore with the [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) cmdlet. Veeam Backup & Replication will delete this helper appliance after you run the [Stop-VBRLinuxFileRestore](stop-vbrlinuxfilerestore.md) cmdlet to complete the guest OS file restore. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the DNS name or IP address of the Linux server. | String | True | 1 | False |
| SSHUser | Specifies the user name you want to use for authenticating with the Linux server.  Note: To add a Linux host using an SSH key fingerprint, provide the Confirm parameter. | String | True | 2 | False |
| SSHPassword | Specifies the password you want to use for authenticating with the Linux server.  Note: To add a Linux host using an SSH key fingerprint, provide the Confirm parameter. | String | True | 3 | False |
| Credentials | Specifies the credentials you want to use for authenticating with the Linux server. | Accepts the CCredentials object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.1) cmdlet. | True | Named | False |
| SSHPort | Specifies the SSH port for connection to the Linux server.  Default: 22 | Int | False | Named | False |
| SSHElevateToRoot | Defines that non-root users are provided with the root account privileges.  Default: False. | SwitchParameter | False | Named | False |
| SSHAddToSudoers | Defines that the user account is added to sudoers file.  Default: (if the ElevateToRoot parameter is set to False) False. | SwitchParameter | False | Named | False |
| SSHFailoverToSu | Defines that Veeam Backup & Replication will use the su command if the sudo command fails.  Default: False. | SwitchParameter | False | Named | False |
| SSHRootPassword | Specifies the root password used for authentication. | String | False | Named | False |
| SSHTempCredentials | To add a Linux server that will be used as a hardened repository.  Defines that the cmdlet will use single-use credentials to access a Linux server.  Default: False. | SwitchParameter | False | Named | False |
| UseCertificate | Defines if certificate-based authentication is used. | SwitchParameter | True | Named | False |
| Description | Specifies the description of the Linux server. | String | False | Named | False |
| SSHFingerprint | Specifies SSH host fingerprint. | String | False | Named | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue. | SwitchParameter | False | Named | False |
| Package | Specifies the optional Linux component to be installed.  Note: If you omit this parameter, all available Linux components will be installed. To add a Linux host without installing any optional components, provide an empty array for this parameter. | Accepts the VBRLinuxPackage[] object. To get this object, run the [Get-VBRLinuxPackage](get-vbrlinuxpackage.md) cmdlet. | False | Named | False |
| HandshakeCode | Specifies the handshake code used to pair with the server.  The first time a server is paired, the code is 000000. If you pair the server again, the code must be generated in the JeOS Host Management Console. | String | False | Named | False |
| ForceDeployerFingerprint | Defines if the fingerprint confirmation dialog is skipped when a host is added using certificate-based authentication | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CHost object that contains settings of a Linux server added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Linux Host Using Credentials for Authentication

|  |  |
| --- | --- |
| This example shows how add a Linux host using credentials for authentication.  |  | | --- | | $Administrator = Get-Credential  Add-VBRLinux -Name "LinRepository" -Credentials $Administrator |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.1) cmdlet. Save the result to the $Administrator variable. 2. Run the Add-VBRLinux cmdlet. Specify the Name parameter value. Set the $Administrator variable as the Credentials parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Linux Host Using Username/Password for Authentication

|  |  |
| --- | --- |
| This command adds the 198.51.100.2 Linux server.  |  | | --- | | Add-VBRLinux -Name "198.51.100.2" -SSHUser "Administrator" -SSHPassword "qwerty" -Description "Linux host 01" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Adding Linux Host Using Certificate for Authentication With No Fingerprint Confirmation

|  |  |
| --- | --- |
| This command adds the 198.51.100.2 Linux server. A certificate is used for authentication and the fingerprint confirmation dialogue is skipped.  |  | | --- | | Add-VBRLinux -Name "198.51.100.2" -UseCertificate -HandshakeCode "000000" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Adding Linux Server Using SSH Key Fingerprint

|  |  |
| --- | --- |
| This example shows how to add the 198.51.100.5 Linux server using an SSH key fingerprint. The cmdlet adds the Linux server with the following settings:   * The SSH port is set to 22. * The Confirm parameter is provided to verify the connection with the SSH key fingerprint.   |  | | --- | | Add-VBRLinux -Name "198.51.100.5" -SSHUser "Administrator" -SSHPassword "qwerty" -SSHFingerprint “9XREolvZA+LrXbblZ1nMAKLhTLFEYi3fHs+1+6F2Dak” -SSHPort 22 -Confirm  Confirm | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Adding Linux Host With Specific Linux Component Using Credentials for Authentication

|  |  |
| --- | --- |
| This example shows how add a Linux host with specific optional components using credentials for authentication.  |  | | --- | | $Administrator = Get-Credential  $linuxpackage = Get-VBRLinuxPackage  Add-VBRLinux -Name "LinRepository" -Credentials $Administrator -Package $linuxpackage |  Perform the following steps:   1. Run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.1) cmdlet. Save the result to the $Administrator variable. 2. Run the [Get-VBRLinuxPackage](get-vbrlinuxpackage.md) cmdlet. Save the result to the $linuxpackage variable. 3. Run the Add-VBRLinux cmdlet. Specify the Name parameter value. Set the $Administrator variable as the Credentials parameter value and set the $linuxpackage variable as the Package parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 6. Adding Linux Host With No Optional Linux Components Installed

|  |  |
| --- | --- |
| This example shows how add a Linux host without any optional Linux components installed.  |  | | --- | | $creds = Get-VBRCredentials -Name 'linux.creds'  Add-VBRLinux -Name "linuxHost" -Credentials $creds -Package @() |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $creds variable. 2. Run the Add-VBRLinux cmdlet. Specify the Name parameter value. Set the $creds variable as the Credentials parameter value. Provide an empty array for the Package parameter. |

Related Commands

* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRLinuxPackage](get-vbrlinuxpackage.md)
* [Get-VBRServer](get-vbrserver.md)
* [Remove-VBRServer](remove-vbrserver.md)


