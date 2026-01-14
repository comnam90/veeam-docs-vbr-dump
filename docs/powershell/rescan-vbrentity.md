---
title: "Rescan-VBREntity"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/rescan-vbrentity.html"
last_updated: "5/20/2024"
product_version: "13.0.1.1071"
---

# Rescan-VBREntity

In this article

Short Description

Rescans backup infrastructure components.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Rescan a selected component.

|  |
| --- |
| Rescan-VBREntity -Entity <Object[]> [-Wait]  [<CommonParameters>] |

* Rescan all items of a selected type.

|  |
| --- |
| Rescan-VBREntity [-AllReplicas] [-AllHosts] [-AllTapeServers] [-AllRepositories] [-AllCloudProviders] [-Wait]  [<CommonParameters>] |

Detailed Description

This cmdlet rescans backup infrastructure components added to Veeam Backup & Replication:

* Hosts and clusters
* Tape servers
* Tape libraries
* Backup repositories
* Cloud providers
* Veeam backup database for new replica restore points
* Protection groups

|  |
| --- |
| Note |
| You cannot rescan a protection group for pre-installed Veeam Agents. To learn more, see the [Protection Group Types](https://helpcenter.veeam.com/docs/backup/agents/protection_groups_types.html?ver=120) section in the Veeam Agent Management Guide. |

* Discovered computers

|  |
| --- |
| Note |
| You cannot rescan a computer added to a protection group for pre-installed Veeam Agents. To learn more, see the [Protection Group Types](https://helpcenter.veeam.com/docs/backup/agents/protection_groups_types.html?ver=120) section in the Veeam Agent Management Guide. |

* Discovered Active Directory objects

You can rescan components, for example, after configuration restore.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Entity | Specifies an array of components you want to rescan. | Accepts the following objects:   * CHost (hosts connected to the backup infrastructure). Run the [Get-VBRServer](get-vbrserver.md) cmdlet to get this object. * [VBRTapeServer](vbrtapeserver.md) (tape servers). Run the [Get-VBRTapeServer](get-vbrtapeserver.md) cmdlet to get this object.  * [VBRTapeLibrary](vbrtapelibrary.md) (tape libraries). Run the [Get-VBRTapeLibrary](get-vbrtapelibrary.md) cmdlet to get this object. * CBackupRepository (backup repositories). Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet to get this object. * [VBRCloudProvider](vbrcloudprovider.md) (cloud providers). Run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet to get this object. * CBackup (only replicas restore points). Run the [Get-VBRReplica](get-vbrreplica.md) cmdlet to get this object. * [VBRProtectionGroup](vbrprotectiongroup.md) (protection groups). Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet to get this object. * [VBRDiscoveredComputer](vbrdiscoveredcomputer.md) (discovered computers). Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet to get this object. * [VBRDiscoveredADEntity](vbrdiscoveredadentity.md) (discovered Active Directory objects that belong to the same protection group).Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet to get this object. | True | Named | True (ByValue) |
| AllReplicas | Defines that the cmdlet will rescan all replicas restore points.  Default: False. | SwitchParameter | False | Named | False |
| AllHosts | Defines that the cmdlet will rescan all managed hosts.  Default: False. | SwitchParameter | False | Named | False |
| AllTapeServers | Defines that the cmdlet will rescan all tape servers.  Default: False. | SwitchParameter | False | Named | False |
| AllRepositories | Defines that the cmdlet will rescan all backup repositories.  Default: False. | SwitchParameter | False | Named | False |
| AllCloudProviders | Defines that the cmdlet will rescan all cloud providers.  Default: False. | SwitchParameter | False | Named | False |
| Wait | Defines that the command waits for the process to complete before accepting more input. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Rescanning all Hosts Managed by Veeam Backup & Replication

|  |  |
| --- | --- |
| This command rescans servers managed by Veeam Backup & Replication.  |  | | --- | | Rescan-VBREntity -AllHosts | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Rescanning Backup Repository

|  |  |
| --- | --- |
| This example shows how to rescan the Win2012Repo backup repository.  |  | | --- | | $repository = Get-VBRBackupRepository -Name "Win2012Repo"  Rescan-VBREntity -Entity $repository |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the Rescan-VBREntity cmdlet. Set the $repository variable as the Entity parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Rescanning Tape Server

|  |  |
| --- | --- |
| This example shows how to rescan the srv01.tech.local tape server.  |  | | --- | | $tapesrv = Get-VBRTapeServer -Name "srv01.tech.local"  Rescan-VBREntity -Entity $tapesrv -Wait |  Perform the following steps:   1. Run the [Get-VBRTapeServer](get-vbrtapeserver.md) cmdlet. Specify the Name parameter value. Save the result to the $tapesrv variable. 2. Run the Rescan-VBREntity cmdlet. Set the $tapesrv variable as the Entity parameter value. Provide the Wait parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Rescanning Replica Restore Points

|  |  |
| --- | --- |
| This example shows how to rescan the 'Webservices' replica restore points.  |  | | --- | | $webservices = Get-VBRReplica -Name "Webservices"  Rescan-VBREntity -Entity $webservices |  Perform the following steps:   1. Run the [Get-VBRReplica](get-vbrreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $webservices variable. 2. Run the Rescan-VBREntity cmdlet. Set the $webservices variable as the Entity parameter value. |

Related Commands

* [Get-VBRTapeServer](get-vbrtapeserver.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRReplica](get-vbrreplica.md)

Page updated 5/20/2024

Page content applies to build 13.0.1.1071
