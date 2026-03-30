---
title: "Get-VEORIRDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veorirdatabase.html"
last_updated: "3/26/2026"
product_version: "13.0.1.2067"
---

# Get-VEORIRDatabase


Short Description

Returns Oracle databases that are published within an instant recovery session.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEORIRDatabase [-DatabaseName <String>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backed-up Oracle databases that are published within an instant recovery session.

After you get published Oracle databases within an instant recovery session, you can perform the following operations with these databases:

* [Switch-VEORIRDatabase](switch-veorirdatabase.md)
* [Set-VEORIRDatabase](set-veorirdatabase.md)
* [Stop-VEORInstantRecovery](stop-veorinstantrecovery.md)

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| DatabaseName | Specifies the name of the Oracle database that the cmdlet will return. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEORIRDatabase](veorirdatabase.md)[] array that contains Oracle databases that are published within an instant recovery session.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Published Oracle Databases Within Instant Recovery Session

|  |  |
| --- | --- |
| This command returns a list of all published Oracle databases within an instant recovery session. Save the result to the $IRDatabase variable to be able to use it with other cmdlets.  |  | | --- | | $IRDatabase = Get-VEORIRDatabase | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Oracle Databases with Specific Name Published Within Instant Recovery Session

|  |  |
| --- | --- |
| This command returns the specified Oracle database published within an instant recovery session. Save the result to the $IRDatabase variable to be able to use it with other cmdlets.  |  | | --- | | $IRDatabase = Get-VEORIRDatabase -DatabaseName "orcl1.tech.local" | |


