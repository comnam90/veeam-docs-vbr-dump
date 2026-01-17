---
title: "Restart-VEPSQLInstancePublish"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/restart-vepsqlinstancepublish.html"
last_updated: "7/11/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Restarts a failed publishing process for a backed-up PostgreSQL instance.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Restart-VEPSQLInstancePublish [-InstancePublish] <VEPSQLInstancePublish> [<CommonParameters>] |

Detailed Description

This cmdlet restarts a failed publishing process for a backed-up PostgreSQL instance.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstancePublish | Specifies the PostgreSQL instance publishing process. The cmdlet will restart this publishing process. | Accepts the [VEPSQLInstancePublish](vepsqlinstancepublish.md) object. To get this object, run the [Get-VEPSQLInstancePublish](get-vepsqlinstancepublish.md) cmdlet. | True | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Restarting Publishing Process for PostgreSQL Instance

This example shows how to restart a failed publishing process for a PostgreSQL instance.

|  |
| --- |
| $publish = Get-VEPSQLInstancePublish -InstanceName "rhel02:5433"  Restart-VEPSQLInstancePublish -InstancePublish $publish |

Perform the following steps:

1. Run the [Get-VEPSQLInstancePublish](get-vepsqlinstancepublish.md) cmdlet. Specify the InstanceName parameter value and save the result to the $publish variable.
2. Run the Restart-VEPSQLInstancePublish cmdlet. Set the $publish variable as the InstancePublish parameter value.

Related Commands

[Get-VEPSQLInstancePublish](get-vepsqlinstancepublish.md)

Page updated 7/11/2025

Page content applies to build 13.0.1.1071
