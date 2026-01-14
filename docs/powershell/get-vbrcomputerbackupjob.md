---
title: "Get-VBRComputerBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcomputerbackupjob.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# Get-VBRComputerBackupJob

In this article

Short Description

Returns Veeam Agent backup jobs and Veeam Agent backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get Veeam Agent backup jobs and Veeam Agent backup policies by their name.

|  |
| --- |
| Get-VBRComputerBackupJob [-Name <String[]>] [-Mode <VBRComputerBackupJobMode> {ManagedByAgent | ManagedByBackupServer}]  [<CommonParameters>] |

* Get Veeam Agent backup jobs and Veeam Agent backup policies by their ID.

|  |
| --- |
| Get-VBRComputerBackupJob [-Id <Guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of Veeam Agent backup jobs and Veeam Agent backup policies.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of IDs for Veeam Agent backup jobs or a Veeam Agent backup policies. | Guid[] | False | Named | False |
| Name | Specifies an array of names for Veeam Agent backup jobs or a Veeam Agent backup policies. | String[] | False | Named | False |
| Mode | Specifies the Veeam Agent backup job mode. You can specify either of the following backup job modes:   * ManagedByAgent: use this option to get the backup policy. * ManagedByBackupServer: use this option to get a Veeam Agent backup job. | VBRComputerBackupJobMode | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerBackupJob[] object that contains settings of Veeam Agent backup jobs and Veeam Agent backup policies.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Veeam Agent Backup Jobs

|  |  |
| --- | --- |
| This command returns an array of all Veeam Agent backup jobs and Veeam Agent backup policies that are added to Veeam Backup & Replication.  |  | | --- | | Get-VBRComputerBackupJob | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Veeam Agent Backup Job by Name

|  |  |
| --- | --- |
| This command returns the Agent Job 05 Veeam Agent backup job.  |  | | --- | | Get-VBRComputerBackupJob -Name "Agent Job 05" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Veeam Agent Backup Policy

|  |  |
| --- | --- |
| This command returns an array of Veeam Agent backup policies.  |  | | --- | | Get-VBRComputerBackupJob -Mode ManagedByAgent | |

Page updated 3/6/2024

Page content applies to build 13.0.1.1071
