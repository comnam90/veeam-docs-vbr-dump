---
title: "Start-VBRHighAvailabilityClusterSwitchover"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrhighavailabilityclusterswitchover.html"
last_updated: "10/20/2025"
product_version: "13.0.1.1071"
---

# Start-VBRHighAvailabilityClusterSwitchover


Short Description

Starts switchover of an HA cluster.

Applies to

Product Edition: Premium

Syntax

|  |
| --- |
| Start-VBRHighAvailabilityClusterSwitchover [-RunAsync] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet starts switchover of an HA cluster. During switchover, Veeam Backup & Replication will assign the role of the primary node to the secondary node and will start the reverse replication from a new primary node to the former primary node.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will start switchover of a HA cluster without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Starting Switchover of HA cluster

This command starts switchover of the HA cluster.

|  |
| --- |
| Start-VBRHighAvailabilityClusterSwitchover -RunAsync |


