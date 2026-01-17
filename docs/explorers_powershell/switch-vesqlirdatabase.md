---
title: "Switch-VESQLIRDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/switch-vesqlirdatabase.html"
last_updated: "12/20/2024"
product_version: "13.0.1.1071"
---

# Switch-VESQLIRDatabase


Short Description

Performs switchover of a Microsoft SQL Server database published within an instant recovery session.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Switch-VESQLIRDatabase [-Database] <VESQLIRDatabase> [<CommonParameters>] |

Detailed Description

This cmdlet performs a manual switchover of a Microsoft SQL Server database published within an instant recovery session. You can perform a switchover after all database files are copied to the target server and the cache file is synchronized. For more information on the switchover option, see the [Switchover](https://helpcenter.veeam.com/docs/vbr/userguide/vesql_switchover.html?ver=13) section of the Veeam Explorers User Guide.

Run the [New-VESQLIRSwitchOverOptions](new-vesqlirswitchoveroptions.md) cmdlet to define the switchover option settings.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a Microsoft SQL Server database. The cmdlet will switchover this database. | Accepts the [VESQLIRDatabase](vesqlirdatabase.md) object. To get this object, run the [Get-VESQLIRDatabase](get-vesqlirdatabase.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Starting Manual Switchover of Published Microsoft SQL Server Database

This example shows how to perform a manual switchover of the fiscal database.

|  |
| --- |
| $IRDatabase = Get-VESQLIRDatabase -DatabaseName "fiscal"  Switch-VESQLIRDatabase -Database $IRDatabase |

Perform the following steps:

1. Run the [Get-VESQLIRDatabase](get-vesqlirdatabase.md) cmdlet. Specify the DatabaseName parameter value. Save the result to the $IRDatabase variable.
2. Run the Switch-VESQLIRDatabase cmdlet. Set the $IRDatabase variable as the Database parameter value.

Related Commands

[Get-VESQLIRDatabase](get-vesqlirdatabase.md)


