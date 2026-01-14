---
title: "stop-vesqlinstantrecovery"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-vesqlinstantrecovery.html"
last_updated: "12/20/2024"
product_version: "13.0.1.1071"
---


In this article

Short Description

Stops an active instant recovery session for a Microsoft SQL Server database.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VESQLInstantRecovery [-Database] <VESQLIRDatabase> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet stops an active instant recovery session for a backed-up Microsoft SQL Server.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a Microsoft SQL Server database. The cmdlet will stop the instant recovery session of this database. | Accepts the [VESQLIRDatabase](vesqlirdatabase.md) object. To get this object, run the [Get-VESQLIRDatabase](get-vesqlirdatabase.md) cmdlet. | True | 0 | True (ByValue) |
| Force | Defines that the cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Instant Recovery Session of a Microsoft SQL Server Database

This example shows how to stop an instant recovery session of the monthly\_db database.

|  |
| --- |
| $IRDatabase = Get-VESQLIRDatabase -DatabaseName "monthly\_db"  Stop-VESQLInstantRecovery -Database $IRDatabase |

Perform the following steps:

1. Run the [Get-VESQLIRDatabase](get-vesqlirdatabase.md) cmdlet. Specify the DatabaseName parameter value. Save the result to the $IRDatabase variable.
2. Run the Stop-VESQLInstantRecovery cmdlet. Set the $IRDatabase variable as the Database parameter value.

Related Commands

[Get-VESQLIRDatabase](get-vesqlirdatabase.md)

Page updated 12/20/2024

Page content applies to build 13.0.1.1071
