---
title: "Switch-VEORIRDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/switch-veorirdatabase.html"
last_updated: "1/7/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Performs switchover of an Oracle database published within an instant recovery session.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Switch-VEORIRDatabase [-Database] <VEORIRDatabase> [<CommonParameters>] |

Detailed Description

This cmdlet performs a manual switchover of an Oracle database published within an instant recovery session. You can perform a switchover after all database files are copied to the target server and the cache file is synchronized. For more information on the switchover options, see the [Switchover](https://helpcenter.veeam.com/docs/vbr/userguide/veor_switchover.html?ver=13) section of the Veeam Explorers User Guide.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Database | Specifies a published Oracle database that the cmdlet will switchover. | Accepts the [VEORIRDatabase](veorirdatabase.md) object. To get this object, run the [Get-VEORIRDatabase](get-veorirdatabase.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Starting Switchover of Oracle Database

This example shows how to perform a manual switchover of the orcl1.tech.local database.

|  |
| --- |
| $IRDatabase = Get-VEORIRDatabase -DatabaseName "orcl1.tech.local"  Switch-VEORIRDatabase -Database $IRDatabase |

Perform the following steps:

1. Run the [Get-VEORIRDatabase](get-veorirdatabase.md) cmdlet. Specify the DatabaseName parameter value. Save the result to the $IRDatabase variable.
2. Run the Switch-VEORIRDatabase cmdlet. Set the $IRDatabase variable as the Database parameter value.

Related Commands

[Get-VEORIRDatabase](get-veorirdatabase.md)

Page updated 1/7/2025

Page content applies to build 13.0.1.1071
