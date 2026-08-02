---
title: "Stop-VEADItemRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-veaditemrestore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Stop-VEADItemRestore


Short Description

Stops the restore process for an Active Directory object or container.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VEADItemRestore [-Restore] <VeadRestore> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet stops an active restore process for an Active Directory object or container.

|  |
| --- |
| Note |
| Restore processes will not stop automatically if you close the PowerShell console. To stop a restore process before it completes, you must run the Stop-VEADItemRestore cmdlet. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Restore | Specifies the restore process for an Active Directory object or container. The cmdlet will stop this restore process. | Accepts the [VEADRestore](veadrestore.md) object. To get this object, run the [Get-VEADItemRestore](get-veaditemrestore.md) cmdlet. | True | 0 | True (ByValue) |
| Force | Defines that the cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Restore Process for Active Directory Object or Container

This example shows how to stop the restore process for an Active Directory object or a container.

|  |
| --- |
| $restore = Get-VEADItemRestore -Server "addc03"  Stop-VEADItemRestore -Restore $restore |

Perform the following steps:

1. Run the [Get-VEADItemRestore](get-veaditemrestore.md) cmdlet. Specify the Server parameter value and save the result to the $restore variable.
2. Run the Stop-VEADItemRestore cmdlet. Set the $restore variable as the Restore parameter value.

Related Commands

* [Start-VEADItemRestore](start-veaditemrestore.md)
* [Get-VEADItemRestore](get-veaditemrestore.md)

Page updated 2026-01-30

