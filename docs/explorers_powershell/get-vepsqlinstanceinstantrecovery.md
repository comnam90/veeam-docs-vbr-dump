---
title: "Get-VEPSQLInstanceInstantRecovery"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vepsqlinstanceinstantrecovery.html"
last_updated: "7/11/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns PostgreSQL instances that are published within an instant recovery session.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEPSQLInstanceInstantRecovery [[-InstanceName] <String>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of PostgreSQL instances that are published within an instant recovery session.

After you get published PostgreSQL instances within an instant recovery session, you can perform the following operations with these instances:

* [Switch-VEPSQLInstanceInstantRecovery](switch-vepsqlinstanceinstantrecovery.md)
* [Set-VEPSQLInstanceInstantRecovery](set-vepsqlinstanceinstantrecovery.md)
* [Stop-VEPSQLInstanceInstantRecovery](stop-vepsqlinstanceinstantrecovery.md)
* [Restart-VEPSQLInstanceInstantRecovery](restart-vepsqlinstanceinstantrecovery.md)

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstanceName | Specifies a name of a PostgreSQL instance. The cmdlet will return an array of instances with the specified name. | String | False | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEPSQLInstanceInstantRecovery](vepsqlinstanceinstantrecovery.md)[] array that contains PostgreSQL instances that are published within an instant recovery session.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Published PostgreSQL Instances Within Instant Recovery Session

|  |  |
| --- | --- |
| This command returns a list of all published PostgreSQL instances within an instant recovery session. Save the result to the $IRInstance variable to be able to use it with other cmdlets.  |  | | --- | | $IRInstance = Get-VEPSQLInstanceInstantRecovery | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting PostgreSQL Instance with Specific Name Published Within Instant Recovery Session

|  |  |
| --- | --- |
| This command returns all PostgreSQL instances with the specified name published within an instant recovery session. Save the result to the $IRInstance variable to be able to use it with other cmdlets.  |  | | --- | | $IRInstance = Get-VEPSQLInstanceInstantRecovery -InstanceName "rhel01:5433" | |

Page updated 7/11/2025

Page content applies to build 13.0.1.1071
