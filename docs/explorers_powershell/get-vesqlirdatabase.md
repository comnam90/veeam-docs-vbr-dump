---
title: "Get-VESQLIRDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vesqlirdatabase.html"
last_updated: "7/11/2025"
product_version: "13.0.1.1071"
---

# Get-VESQLIRDatabase


Short Description

Returns Microsoft SQL Server databases that are published within an instant recovery session.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VESQLIRDatabase [[-DatabaseName] <String>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backed-up Microsoft SQL Server databases that are published within an instant recovery session.

After you get the published Microsoft SQL Server databases within an instant recovery session, you can perform the following operations with these databases:

* [Switch-VESQLIRDatabase](switch-vesqlirdatabase.md)
* [Set-VESQLIRDatabase](set-vesqlirdatabase.md)
* [Stop-VESQLInstantRecovery](stop-vesqlinstantrecovery.md)

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| DatabaseName | Specifies a Microsoft SQL Server database name. The cmdlet will return an array of databases with the specified name. | String | False | 0 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VESQLIRDatabase](vesqlirdatabase.md)[] array that contains Microsoft SQL Server databases that are published within an instant recovery session.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Microsoft SQL Server Databases Published Within Instant Recovery Session

|  |  |
| --- | --- |
| This command returns a list of all published Microsoft SQL Server databases within an instant recovery session. Save the result to the $IRDatabase variable to be able to use it with other cmdlets.  |  | | --- | | $IRDatabase = Get-VESQLIRDatabase | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Microsoft SQL Server Databases with Specific Name Published Within Instant Recovery Session

|  |  |
| --- | --- |
| This command returns all Microsoft SQL Server databases with the specified name published within an instant recovery session. Save the result to the $IRDatabase variable to be able to use it with other cmdlets.  |  | | --- | | $IRDatabase = Get-VESQLIRDatabase -DatabaseName "db1" | |


