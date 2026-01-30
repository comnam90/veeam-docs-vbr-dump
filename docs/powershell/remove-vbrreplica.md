---
title: "Remove-VBRReplica"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrreplica.html"
last_updated: "7/1/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRReplica


Short Description

Removes replica objects and replicated VMs.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRReplica [-Backup] <CBackup[]> [-FromDisk] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes replica objects and replicated VMs.

You can use the following options:

* Remove from console. When you remove replica from the Veeam console, you will not delete the VM but only stop managing it by Veeam Backup & Replication. When replica is created, Veeam Backup & Replication maintains it in sync with the original VM by running the replication job. When you delete a replica from your managing console, it is no longer synchronized. The replica VM stays on target host.
* Remove from disk. With this option, the replica objects and replica VM are removed from database and from target host. This removal is complete and non-reversible.

To stop synchronizing a replica without deleting it from the console, you need to disable or delete the corresponding replication job. Run the [Disable-VBRJob](disable-vbrjob.md) or [Remove-VBRJob](remove-vbrjob.md) cmdlet.

This cmdlet removes all VMs in the replication job. To remove individual VMs, run the [Remove-VBRRestorePoint](remove-vbrrestorepoint.md) cmdlet.

|  |
| --- |
| ![Remove-VBRReplica](images/icon_note.webp) Note: |
| When you remove a replica from Veeam Backup & Replication console, you can not bring it back by means of PowerShell. Use replica seeding option in UI to restore a removed replica. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies the array of replica objects you want to remove. | Accepts the CBackup[] object. To create this object, run the [Get-VBRReplica](get-vbrreplica.md) cmdlet. | True | 1 | True (ByValue, |
| FromDisk | Defines that the replica object and replicated VM will be permanently removed from disk. Otherwise, you only exclude the replica from processing by Veeam Backup & Replication. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Replicas from Console

|  |  |
| --- | --- |
| This example shows how to remove replicas from Veeam Backup & Replication.  |  | | --- | | $replica = Get-VBRReplica -Name "DC\_replica01", "DC\_replica02"  Remove-VBRReplica -Backup $replica |  Perform the following steps:   1. Run the [Get-VBRReplica](get-vbrreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable. 2. Run the Remove-VBRReplica cmdlet. Set the $replica variable as the Backup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Replicas from Disk

|  |  |
| --- | --- |
| This example shows how to remove replicas from disk.  |  | | --- | | $replica = Get-VBRReplica -Name "DC\_replica01", "DC\_replica02"  Remove-VBRReplica -Backup $replica -FromDisk |  Perform the following steps:   1. Run the [Get-VBRReplica](get-vbrreplica.md) cmdlet. Specify the Name parameter value. Save the result to the $replica variable. 2. Run the Remove-VBRReplica cmdlet. Set the $replica variable as the Backup parameter value. Provide the FromDisk parameter. |

Related Commands

[Get-VBRReplica](get-vbrreplica.md)


