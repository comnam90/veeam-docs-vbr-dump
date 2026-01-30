---
title: "New-VBRSureBackupTestScript"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrsurebackuptestscript.html"
last_updated: "4/30/2024"
product_version: "13.0.1.1071"
---

# New-VBRSureBackupTestScript


Short Description

Defines recovery verification scripts for VMs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Defines a recovery verification script for custom VM roles.

|  |
| --- |
| New-VBRSureBackupTestScript -Name <string> -Path <string> -Argument <string>  [<CommonParameters>] |

* Defines a recovery verification script for predefined VM roles.

|  |
| --- |
| New-VBRSureBackupTestScript -PredefinedApplication <VBRSureBackupApplication> {DNSServer | DomainController | GlobalCatalog | MailServer | SQLServer | WebServer | VBO}  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRSureBackupTestScript object that defines recovery verification scripts for VMs that are added to application groups and to jobs that are linked to SureBackup jobs. Veeam Backup & Replication will run this script to verify that the VM that has been assigned the specific role has up and running applications for this role.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name for a script. The cmdlet will define a script with the specified name. | String | True | Named | False |
| Path | Specifies a path to a custom script. The cmdlet will use this path to access the script. | String | True | Named | False |
| Argument | Specifies an IP address and the port number. The cmdlet will use this IP address and port to access the VM. | String | True | Named | False |
| PredefinedApplication | Specifies a script for predefined roles. The cmdlet will run the script to verify applications inside VMs. You can specify the script for either of the following roles:   * DNSServer * DomainController * GlobalCatalog * MailServer * SQLServer * WebServer * VBO | VBRSureBackupApplication | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSureBackupTestScript object that defines recovery verification scripts for VMs that are added to application groups and to jobs that are linked to SureBackup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Recovery Verification Script for Custom VM Roles

|  |  |
| --- | --- |
| This command defines the ScriptVerification verification script for custom VM roles. The script will be defined with the following settings:   * The script is located at the C:\scripts\pre-script.bat path. * Veeam Backup & Replication will use the 192.0.2.5 IP and the 53 port to access the VM.     |  | | --- | | New-VBRSureBackupTestScript -Name "ScriptVerification" -Path "C:\scripts\script.bat" -Argument "192.0.2.5 53" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Recovery Verification Script for Predefined VM Roles

|  |  |
| --- | --- |
| This command defines a verification script for the DNS Server VM role. Veeam Backup & Replication will run the script to verify that the VM with the DNS Server role has up and running applications for this role.  |  | | --- | | New-VBRSureBackupTestScript -PredefinedApplication DNSServer | |


