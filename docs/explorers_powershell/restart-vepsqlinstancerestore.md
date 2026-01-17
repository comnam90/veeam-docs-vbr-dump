---
title: "Restart-VEPSQLInstanceRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/restart-vepsqlinstancerestore.html"
last_updated: "7/11/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Restarts a failed restore process for a backed-up PostgreSQL instance.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Restart-VEPSQLInstanceRestore [-InstanceRestore] <VEPSQLInstanceRestore> [<CommonParameters>] |

Detailed Description

This cmdlet restarts a failed restore process for a PostgreSQL instance.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstanceRestore | Specifies the PostgreSQL instance restore process. The cmdlet will restart this restore process. | Accepts the [VEPSQLInstanceRestore](vepsqlinstancerestore.md) object. To get this object, run the [Get-VEPSQLInstanceRestore](get-vepsqlinstancerestore.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Restarting Failed Restore Process for PostgreSQL Instance

This example shows how to restart a failed restore process for the rhel01:5433 instance.

|  |
| --- |
| $restore = Get-VEPSQLInstanceRestore -InstanceName "rhel01:5433"  Restart-VEPSQLInstanceRestore -InstanceRestore $restore |

Perform the following steps:

1. Run the [Get-VEPSQLInstanceRestore](get-vepsqlinstancerestore.md) cmdlet. Specify the InstanceName parameter value. Save the result to the $restore variable.
2. Run the Restart-VEPSQLInstanceRestore cmdlet. Set the $restore variable as the Instance parameter value.

Related Commands

[Get-VEPSQLInstanceRestore](get-vepsqlinstancerestore.md)

Page updated 7/11/2025

Page content applies to build 13.0.1.1071
