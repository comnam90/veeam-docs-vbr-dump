---
title: "unpublish-veordatabase"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/unpublish-veordatabase.html"
last_updated: "1/7/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Unpublishes Oracle databases from the target server.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Unpublish-VEORDatabase [-Databases] <VEORPublishedDatabase[]> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet unpublishes Oracle databases from the target server.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Databases | Specifies the Oracle databases that the cmdlet will unpublish from the target Oracle server. | Accepts the [VEORPublishedDatabase](veorpublisheddatabase.md)[] object. To get this object, run the [Get-VEORPublishedDatabase](get-veorpublisheddatabase.md) cmdlet. | True | 0 | True |
| Force | Defines that the cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Unpublishing Oracle Databases

This example shows how to unpublish Oracle databases.

|  |
| --- |
| $session = Get-VEORRestoreSession  $databases = Get-VEORPublishedDatabase -Session $session[0]  Unpublish-VEORDatabase -Databases $databases |

Perform the following steps:

1. Run the [Get-VEORRestoreSession](get-veorrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.

1. Run the [Get-VEORPublishedDatabase](get-veorpublisheddatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Save the result to the $databases variable.
2. Run the Unpublish-VEORDatabase cmdlet. Set the $databases variable as the Databases parameter value.

Related Commands

* [Get-VEORRestoreSession](get-veorrestoresession.md)
* [Get-VEORPublishedDatabase](get-veorpublisheddatabase.md)

Page updated 1/7/2025

Page content applies to build 13.0.1.1071
