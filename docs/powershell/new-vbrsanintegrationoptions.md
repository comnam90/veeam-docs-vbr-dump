---
title: "New-VBRSanIntegrationOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrsanintegrationoptions.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# New-VBRSanIntegrationOptions

In this article

Short Description

Defines storage integration settings for the Veeam Agent backup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRSanIntegrationOptions [-OsPlatform {Windows | Linux | Mac | Unix}] [-EnableSanSnapshots] [-Proxy <VBRComputerFileProxyServer[]>] [-EnableFailoverFromSan]  [<CommonParameters>] |

Detailed Description

This cmdlet defines Veeam Agent integration settings of the storage system. You can run this cmdlet to allow Veeam Backup & Replication to create Veeam Agent backups from the storage native snapshots.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| OsPlatform | Specifies the OS of protected computers. The cmdlet will define Veeam Agent integration settings of the storage system for these types of computers:   * Windows: for Windows computers. * Linux: for Linux computers. * Mac: for macOS computers. * Unix: for Unix computers.   Default: Windows.  Note: Veeam Agent integration settings of the storage system are not supported for Linux and macOS computers in current version of Veeam PowerShell. | VBRAgentType | False | Named | False |
| EnableSanSnapshots | Enables the option to create Veeam Agent backups from native storage snapshots.  Default: False. | SwitchParameter | False | Named | False |
| Proxy | Specifies the server which will act as a general-purpose backup proxy.  If not specified, Veeam Backup & Replication will select suitable general-purpose backup proxies from your Veeam Backup & Replication environment. | Accepts the VBRComputerFileProxyServer object. To get this object, run the [Get-VBRComputerFileProxyServer](get-vbrcomputerfileproxyserver.md)cmdlet. | False | Named | False |
| EnableFailoverFromSan | Enables the option for Veeam Backup & Replication to failover to a backup operation with a software VSS provider.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |

Output Object

The cmdlet returns the VBRSanIntegrationOptions object that contains storage integration settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Veeam Agent Integration Settings with Automatic General-purpose Backup Proxy Selection

|  |  |
| --- | --- |
| This command defines integration settings for the Veeam Agent backup job and allow Veeam Backup & Replication to select suitable backup proxies for data transfer.  |  | | --- | | New-VBRSanIntegrationOptions -EnableSanSnapshots | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Veeam Agent Integration Settings with Specific General-purpose Backup Proxy

|  |  |
| --- | --- |
| This example shows how to define integration settings and specify a backup proxy server for data transfer. Veeam Backup & Replication will create Veeam Agent backups from the storage snapshots using the specified backup proxy.  |  | | --- | | $proxy = Get-VBRComputerFileProxyServer -Name "File Proxy 01"  New-VBRSanIntegrationOptions -Proxy $proxy -EnableSanSnapshots |  Perform the following steps:   1. Run the [Get-VBRComputerFileProxyServer](get-vbrcomputerfileproxyserver.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable. 2. Run the New-VBRSanIntegrationOptions cmdlet. Set the $proxy variable as the Proxy parameter value. Provide the EnableSanSnapshots parameter. |

Related Commands

[Get-VBRComputerFileProxyServer](get-vbrcomputerfileproxyserver.md)

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
