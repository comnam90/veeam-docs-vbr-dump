---
title: "Restart-VEPSQLInstanceInstantRecovery"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/restart-vepsqlinstanceinstantrecovery.html"
last_updated: "1/7/2025"
product_version: "13.0.1.1071"
---

# Restart-VEPSQLInstanceInstantRecovery


Short Description

Restarts a failed instant recovery process for a PostgreSQL instance.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Restart-VEPSQLInstanceInstantRecovery [-Instance] <VEPSQLInstanceInstantRecovery> [<CommonParameters>] |

Detailed Description

This cmdlet restarts a failed instant recovery process for a PostgreSQL instance.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Instance | Specifies the PostgreSQL instance with an ongoing instant recovery session. The cmdlet will restart the instant recovery process for this instance. | Accepts the [VEPSQLInstanceInstantRecovery](vepsqlinstanceinstantrecovery.md) object. To get this object, run the [Get-VEPSQLInstanceInstantRecovery](get-vepsqlinstanceinstantrecovery.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Restarting Failed Instant Recovery Process for Specific PostgreSQL Instance

This example shows how to restart an instant recovery session for the rhel01:5433 instance.

|  |
| --- |
| $IRInstance = Get-VEPSQLInstanceInstantRecovery -InstanceName "rhel01:5433"  Restart-VEPSQLInstanceInstantRecovery -Instance $IRInstance |

Perform the following steps:

1. Run the [Get-VEPSQLInstanceInstantRecovery](get-vepsqlinstanceinstantrecovery.md) cmdlet. Specify the InstanceName parameter value. Save the result to the $IRInstance variable.
2. Run the Restart-VEPSQLInstanceInstantRecovery cmdlet. Set the $IRInstance variable as the Instance parameter value.

Related Commands

[Get-VEPSQLInstanceInstantRecovery](get-vepsqlinstanceinstantrecovery.md)


