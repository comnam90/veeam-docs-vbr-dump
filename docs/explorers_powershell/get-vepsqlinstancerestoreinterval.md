---
title: "Get-VEPSQLInstanceRestoreInterval"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vepsqlinstancerestoreinterval.html"
last_updated: "2/4/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns details on the available restore period for a backed-up PostgreSQL instance.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEPSQLInstanceRestoreInterval [-Instance] <VEPSQLInstance> [<CommonParameters>] |

Detailed Description

This cmdlet returns details on available restore period for a backed-up PostgreSQL instance.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Instance | Specifies a backed-up PostgreSQL instance. The cmdlet will return information on the available restore period for the specified instance. | Accepts the [VEPSQLInstance](vepsqlinstance.md) object. To get this object, run the [Get-VEPSQLInstance](get-vepsqlinstance.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEPSQLDatabaseRestoreInterval](vepsqldatabaserestoreinterval.md) object that contains details on available restore period for the specified PostgreSQL instance.

Example

Getting Restore Period for PostgreSQL Instance

This example shows how to get details on an available restore period for the PostgreSQL instance.

|  |
| --- |
| $session = Get-VEPSQLRestoreSession  $instance = Get-VEPSQLInstance -Session $session[0] -DataDirectory /var/lib/pgsql/13/data  Get-VEPSQLInstanceRestoreInterval -Instance $instance |

Perform the following steps:

1. Run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. Save the result to the $session variable.
2. Run the [Get-VEPSQLInstance](get-vepsqlinstance.md) cmdlet. Set the $session variable as the Session parameter value. Specify the DataDirectory parameter value. Save the result to the $instance variable.
3. Run the Get-VEPSQLInstanceRestoreInterval cmdlet. Set the $instance variable as the Instance parameter value.

Related Commands

* [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md)
* [Get-VEPSQLInstance](get-vepsqlinstance.md)

Page updated 2/4/2025

Page content applies to build 13.0.1.1071
