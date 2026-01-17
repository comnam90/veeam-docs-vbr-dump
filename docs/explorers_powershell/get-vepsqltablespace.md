---
title: "Get-VEPSQLTablespace"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vepsqltablespace.html"
last_updated: "1/30/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns tablespaces for a backed-up PostgreSQL instance.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEPSQLTablespace [-Instance] <VEPSQLInstance> [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of tablespaces for a backed-up PostgreSQL instance.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Instance | Specifies a PostgreSQL instance. The cmdlet will return an array of tablespaces for the specified instance. | Accepts the [VEPSQLInstance](vepsqlinstance.md) object. To get this object, run the [Get-VEPSQLInstance](get-vepsqlinstance.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEPSQLTableSpace](vepsqltablespace.md)[] array that contains tablespaces for the specified instance.

Example

Getting Tablespaces of PostgreSQL Instance

This example shows how to get an array of tablespaces for a backed-up PostgreSQL instance.

|  |
| --- |
| $session = Get-VEPSQLRestoreSession  $instance = Get-VEPSQLInstance -Session $session[0] -DataDirectory /var/lib/pgsql/13/data  Get-VEPSQLTablespace -Instance $instance |

Perform the following steps:

1. Run the [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of active restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.

1. Run the [Get-VEPSQLInstance](get-vepsqlinstance.md) cmdlet. Set the $session variable as the Session parameter value. Specify the DataDirectory parameter value. Save the result to the $instance variable.
2. Run the Get-VEPSQLTablespace cmdlet. Set the $instance variable as the Instance parameter value.

Related Commands

* [Get-VEPSQLRestoreSession](get-vepsqlrestoresession.md)
* [Get-VEPSQLInstance](get-vepsqlinstance.md)

Page updated 1/30/2025

Page content applies to build 13.0.1.1071
