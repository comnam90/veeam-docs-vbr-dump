---
title: "Stop-VEPSQLInstanceInstantRecovery"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vepsqlinstanceinstantrecovery.html"
last_updated: "7/11/2025"
product_version: "13.0.1.1071"
---

# Stop-VEPSQLInstanceInstantRecovery


Short Description

Stops an active instant recovery session for a PostgreSQL instance.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VEPSQLInstanceInstantRecovery [-Instance] <VEPSQLInstanceInstantRecovery> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet stops an active instant recovery session for a PostgreSQL instance.

|  |
| --- |
| Note |
| Instant recovery sessions will not stop automatically if you close the PowerShell console. To stop the instant recovery session, you must run the Stop-VEPSQLInstanceInstantRecovery cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Instance | Specifies a PostgreSQL instance. The cmdlet will stop the instant recovery session of this instance. | Accepts the [VEPSQLInstanceInstantRecovery](vepsqlinstanceinstantrecovery.md) object. To get this object, run the [Get-VEPSQLInstanceInstantRecovery](get-vepsqlinstanceinstantrecovery.md) cmdlet. | True | 0 | True (ByValue) |
| Force | Defines that the cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Instant Recovery Session for Specific PostgreSQL Instance

This example shows how to stop an instant recovery session of the rhel01:5433 instance.

|  |
| --- |
| $IRInstance = Get-VEPSQLInstanceInstantRecovery -InstanceName "rhel01:5433"  Stop-VEPSQLInstanceInstantRecovery -Instance $IRInstance |

Perform the following steps:

1. Run the [Get-VEPSQLInstanceInstantRecovery](get-vepsqlinstanceinstantrecovery.md) cmdlet. Specify the InstanceName parameter value. Save the result to the $IRInstance variable.
2. Run the Stop-VEPSQLInstanceInstantRecovery cmdlet. Set the $IRInstance variable as the Instance parameter value.

Related Commands

* [Get-VEPSQLInstanceInstantRecovery](get-vepsqlinstanceinstantrecovery.md)
* [Start-VEPSQLInstanceInstantRecovery](start-vepsqlinstanceinstantrecovery.md)


