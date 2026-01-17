---
title: "Stop-VEORInstantRecovery"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-veorinstantrecovery.html"
last_updated: "1/7/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Stops an active instant recovery session for an Oracle database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VEORInstantRecovery [-Database] <VEORIRDatabase> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet stops an active instant recovery session for an Oracle database.

|  |
| --- |
| Note |
| * The cmdlet stops instant recovery sessions initiated in the PowerShell console only. * Instant recovery sessions will not stop automatically if you close the PowerShell console. To stop the instant recovery session, you must run the Stop-VEORInstantRecovery cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies an Oracle database. The cmdlet will stop the instant recovery session of this database. | Accepts the [VEORIRDatabase](veorirdatabase.md) object. To get this object, run the [Get-VEORIRDatabase](get-veorirdatabase.md) cmdlet. | True | 0 | True (ByValue) |
| Force | Defines that the cmdlet will stop the instant recovery session of an Oracle database without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Restore Session of Oracle Database

This example shows how to stop an instant recovery session of an Oracle database.

|  |
| --- |
| $IRDatabase = Get-VEORIRDatabase -DatabaseName "orcl1.tech.local"  Stop-VEORInstantRecovery -Database $IRDatabase |

Perform the following steps:

1. Run the [Get-VEORIRDatabase](get-veorirdatabase.md) cmdlet. Specify the DatabaseName parameter value. Save the result to the $IRDatabase variable.
2. Run the Stop-VEORInstantRecovery cmdlet. Set the $IRDatabase variable as the Database parameter value.

Related Commands

[Get-VEORIRDatabase](get-veorirdatabase.md)

Page updated 1/7/2025

Page content applies to build 13.0.1.1071
