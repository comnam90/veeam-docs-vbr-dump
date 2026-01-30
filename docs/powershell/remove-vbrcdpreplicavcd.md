---
title: "Remove-VBRCDPReplica"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrcdpreplicavcd.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRCDPReplica


Short Description

Removes a CDP replica from the configuration database or disk.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRCDPReplica -Replica <VBRCDPReplicaBase> [-FromDisk] [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a CDP replica including CDP replicas created by CDP policies including Cloud Director CDP policies, CDP policies, cloud CDP policies and so on.

You can remove the replica according to the following scenarios:

* From the configuration. Veeam Backup & Replication removes records about the replicas from the configuration database, stops showing the replicas in Veeam Backup & Replication console and also stops synchronizing their state with the state of the original workload. However, the actual replicas remain on hosts.
* From the disk. Veeam Backup & Replication removes the replicas not only from the Veeam Backup & Replication console and configuration database, but also from the host storage.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Replica | Specifies the replica that you want to remove. | Accepts the VBRCDPReplicaBase object. To create this object, run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| FromDisk | Defines that the cmdlet will remove the replica from the disk.  Note: If you do not provide this parameter, the cmdlet will remove the replica from the configuration. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will remove a replica showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing CDP Replica from Backup Infrastructure

This examples shows how to remove the Win05 CDP replica from a backup infrastructure. The cmdlet will permanently remove a CDP replica from a disk.

|  |
| --- |
| $replica = Get-VBRCDPReplica -Name "Win05"  Remove-VBRCDPReplica -Replica $replica -FromDisk |

Perform the following steps:

1. Run the [Get-VBRCDPReplica](get-vbrcdpreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable.
2. Run the Remove-VBRCDPReplica cmdlet. Set the $replica variable as the Replica parameter. Provide the FromDisk parameter.

Related Commands

[Get-VBRCDPReplica](get-vbrcdpreplica.md)


