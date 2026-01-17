---
title: "Get-VEPSQLInstanceRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vepsqlinstancerestore.html"
last_updated: "1/30/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns information about the restore process for backed-up PostgreSQL instances.

Applies to

Veeam Backup & Replication

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEPSQLInstanceRestore [[-InstanceName] <String>] [<CommonParameters>] |

Detailed Description

This cmdlet returns information about the restore process for a backed-up PostgreSQL instance.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstanceName | Specifies the name of the restored PostgreSQL instance. The cmdlet will return information about the restore process performed for the specified instance. | String | False | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEPSQLInstanceRestore](vepsqlinstancerestore.md)[] array that contains information about the restore process of PostgreSQL instances.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All PostgreSQL Restore Processes

|  |  |
| --- | --- |
| This command returns a list of all active PostgreSQL restore processes. Save the result to the $restore variable to be able to use it with other cmdlets.  |  | | --- | | $restore = Get-VEPSQLInstanceRestore | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting PostgreSQL Restore Processes for Specific Instance

|  |  |
| --- | --- |
| This command returns all active restore processes for a specific PostgreSQL instance. Save the result to the $restore variable to be able to use it with other cmdlets.  |  | | --- | | $restore = Get-VEPSQLInstanceRestore -InstanceName "rhel01:5433" | |

Page updated 1/30/2025

Page content applies to build 13.0.1.1071
