---
title: "Get-VEPSQLInstancePublish"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vepsqlinstancepublish.html"
last_updated: "7/11/2025"
product_version: "13.0.1.1071"
---

# Get-VEPSQLInstancePublish


Short Description

Returns active publishing sessions for backed-up PostgreSQL instances.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEPSQLInstancePublish [[-InstanceName] <String>] [<CommonParameters>] |

Detailed Description

This cmdlet returns information about the publishing process for backed-up PostgreSQL instances.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstanceName | Specifies the name of the published PostgreSQL instance. The cmdlet will return information about the publishing process performed for the specified instance. | String | False | 0 | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEPSQLInstancePublish](vepsqlinstancepublish.md)[] array that contains information about the publishing process of PostgreSQL instances.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Published PostgreSQL Instances

|  |  |
| --- | --- |
| This command returns a list of all published PostgreSQL instances. Save the result to the $publish variable to be able to use it with other cmdlets.  |  | | --- | | $publish = Get-VEPSQLInstancePublish | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Published PostgreSQL Instance with Specific Name

|  |  |
| --- | --- |
| This command returns a specific published instance. Save the result to the $publish variable to be able to use it with other cmdlets.  |  | | --- | | $publish = Get-VEPSQLInstancePublish -InstanceName "rhel01:5433" | |


