---
title: "stop-vepsqlinstancerestore"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vepsqlinstancerestore.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Stops the restore process for a backed-up PostgreSQL instance.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VEPSQLInstanceRestore [-InstanceRestore] <VEPSQLInstanceRestore> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet stops an active restore process started for a PostgreSQL instance.

|  |
| --- |
| Note |
| Restore processes will not stop automatically if you close the PowerShell console. To stop a restore process, you must run the Stop-VEPSQLInstanceRestore cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstanceRestore | Specifies the PostgreSQL instance restore process. The cmdlet will stop this restore process. | Accepts the [VEPSQLInstanceRestore](vepsqlinstancerestore.md) object. To get this object, run the [Get-VEPSQLInstanceRestore](get-vepsqlinstancerestore.md) cmdlet. | True | 0 | True (ByValue) |
| Force | Defines that the cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Restore Process for PostgreSQL Instance

This example shows how to stop the restore process for a PostgreSQL instance.

|  |
| --- |
| $restore = Get-VEPSQLInstanceRestore -InstanceName "rhel01:5433"  Stop-VEPSQLInstanceRestore -InstanceRestore $restore |

Perform the following steps:

1. Run the [Get-VEPSQLInstanceRestore](get-vepsqlinstancerestore.md) cmdlet. Specify the InstanceName parameter value and save the result to the $restore variable.
2. Run the Stop-VEPSQLInstanceRestore cmdlet. Set the $restore variable as the InstanceRestore parameter value.

Related Commands

[Get-VEPSQLInstanceRestore](get-vepsqlinstancerestore.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
