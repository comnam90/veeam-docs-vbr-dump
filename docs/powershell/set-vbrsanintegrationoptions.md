---
title: "Set-VBRSanIntegrationOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrsanintegrationoptions.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# Set-VBRSanIntegrationOptions

In this article

Short Description

Modifies storage integration settings for the Veeam Agent backup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRSanIntegrationOptions -SanIntegrationOptions <VBRSanIntegrationOptions> [-EnableSanSnapshots] [-Proxy <VBRComputerFileProxyServer[]>] [-EnableSanProxyAutodetect] [-EnableFailoverFromSan]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies storage integration settings for the Veeam Agent backup job.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SanIntegrationOptions | Specifies the set of storage integration settings which Veeam Backup & Replication will modify. | Accepts the VBRSanIntegrationOptions object. To get this object, run the [New-VBRSanIntegrationOptions](new-vbrsanintegrationoptions.md) cmdlet. | True | Named | False |
| EnableSanSnapshots | Enables the option to create Veeam Agent backups from native storage snapshots.  Default: False. | SwitchParameter | False | Named | False |
| Proxy | Specifies the server which will act as a general-purpose backup proxy.  If not specified, the SanProxyAutodetectEnabled option must have the True value. | Accepts the VBRComputerFileProxyServer object. To get this object, run the [Get-VBRComputerFileProxyServer](get-vbrcomputerfileproxyserver.md) cmdlet. | False | Named | False |
| EnableSanProxyAutodetect | Enables the option to use all backup proxies that are added to your Veeam Backup & Replication environment. | SwitchParameter | False | Named | False |
| EnableFailoverFromSan | Enables the option for Veeam Backup & Replication to failover to a backup operation with a software VSS provider.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSanIntegrationOptions object that contains storage integration settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Replacing General-purpose Backup Proxy

|  |  |
| --- | --- |
| This command shows how to replace a general-purpose backup proxy. Veeam Backup & Replication will create Veeam Agent backups from the storage snapshots using a new general-purpose backup proxy.  |  | | --- | | $job = Get-VBRComputerBackupJob -Name "Daily Backup"  $currentSanIntOpt = $job.SanIntegrationOptions  $proxy = Get-VBRComputerFileProxyServer -Name "File Proxy 02"  Set-VBRSanIntegrationOptions -SanIntegrationOptions $currentSanIntOpt -Proxy $proxy |  Perform the following steps:   1. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.  1. Get the current storage integration settings of the Veeam Agent backup job. Use the VBRSanIntegrationOptions parameter of the $job variable. Save it to the $currentSanIntOpt variable.  1. Run the [Get-VBRComputerFileProxyServer](get-vbrcomputerfileproxyserver.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable.  1. Run the Set-VBRSanIntegrationOptions cmdlet. Set the $currentSanIntOpt variable as the SanIntegrationOptions parameter value. Set the $proxy variable as the Proxy parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Disabling Storage Integration for Veeam Agent Backup Job

|  |  |
| --- | --- |
| This example shows how to disable storage integration for the Veeam Agent backup job. Veeam Backup & Replication will create Veeam Agent backups using a software VSS provider.    |  | | --- | | $job = Get-VBRComputerBackupJob -Name "Daily Backup"  $currentSanIntOpt = $job.SanIntegrationOptions  $NewSanIntOpt = Set-VBRSanIntegrationOptions -SanIntegrationOptions $currentSanIntOpt -EnableSanSnapshots:$false  Set-VBRComputerBackupJob -Job $job -SanIntegrationOptions $NewSanIntOpt |  Perform the following steps:   1. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.  1. Get the current storage integration settings of the Veeam Agent backup job. Use the VBRSanIntegrationOptions parameter of the $job variable. Save it to the $currentSanIntOpt variable. 2. Run the Set-VBRSanIntegrationOptions cmdlet. Set the $currentSanIntOpt variable as the SanIntegrationOptions parameter value. Specify the EnableSanSnapshots parameter value. Save the result to the $NewSanIntOpt variable. 3. Run the [Set-VBRComputerBackupJob](set-vbrcomputerbackupjob.md) cmdlet. Specify the $job variable as the Job parameter value. Set the $NewSanIntOpt variable as the SanIntegrationOptions parameter value. |

Related Commands

* [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md)
* [Get-VBRComputerFileProxyServer](get-vbrcomputerfileproxyserver.md)
* [Set-VBRComputerBackupJob](set-vbrcomputerbackupjob.md)

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
