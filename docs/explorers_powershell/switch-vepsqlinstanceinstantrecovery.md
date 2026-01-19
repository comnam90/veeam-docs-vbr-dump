---
title: "Switch-VEPSQLInstanceInstantRecovery"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/switch-vepsqlinstanceinstantrecovery.html"
last_updated: "3/12/2025"
product_version: "13.0.1.1071"
---

# Switch-VEPSQLInstanceInstantRecovery


Short Description

Performs switchover of a published PostgreSQL instance.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Switch-VEPSQLInstanceInstantRecovery [-Instance] <VEPSQLInstanceInstantRecovery> [<CommonParameters>] |

Detailed Description

This cmdlet performs a manual switchover of a PostgreSQL instance published within an instant recovery session. You can perform a switchover after all database files are copied to the target server and the cache file is synchronized. For more information on the switchover options, see the [Switchover](https://helpcenter.veeam.com/docs/vbr/userguide/vep_ir_switchover.html?ver=13) section of the Veeam Explorers User Guide.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Instance | Specifies a PostgreSQL instance. The cmdlet will switchover this instance. | Accepts the [VEPSQLInstanceInstantRecovery](vepsqlinstanceinstantrecovery.md) object. To get this object, run the [Get-VEPSQLInstanceInstantRecovery](get-vepsqlinstanceinstantrecovery.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Starting Switchover of Published PostgreSQL Instance

This example shows how to perform a manual switchover of the rhel01:5433 instance.

|  |
| --- |
| $IRInstance = Get-VEPSQLInstanceInstantRecovery -InstanceName "rhel01:5433"  Switch-VEPSQLInstanceInstantRecovery -Instance $IRInstance |

Perform the following steps:

1. Run the [Get-VEPSQLInstanceInstantRecovery](get-vepsqlinstanceinstantrecovery.md) cmdlet. Specify the InstanceName parameter value. Save the result to the $IRInstance variable.
2. Run the Switch-VEPSQLInstanceInstantRecovery cmdlet. Set the $IRInstance variable as the Instance parameter value.

Related Commands

[Get-VEPSQLInstanceInstantRecovery](get-vepsqlinstanceinstantrecovery.md)


