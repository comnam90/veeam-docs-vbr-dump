---
title: "Unpublish-VESQLDatabase"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/unpublish-vesqldatabase.html"
last_updated: "3/12/2025"
product_version: "13.0.1.1071"
---

# Unpublish-VESQLDatabase


Short Description

Unpublishes Microsoft SQL Server databases from the target server.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Unpublish-VESQLDatabase [-Databases] <VESQLPublishedDatabase[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>] |

Detailed Description

This cmdlet unpublishes Microsoft SQL Server databases from the target machine with Microsoft SQL Server.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Databases | Specifies the published Microsoft SQL Server databases. The cmdlet will unpublish these databases from the target server. | Accepts the [VESQLPublishedDatabase](vesqlpublisheddatabase.md)[] object. To get this object, run the [Get-VESQLPublishedDatabase](get-vesqlpublisheddatabase.md) cmdlet. | True | 0 | True (ByValue) |
| Force | Defines that cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | Named | False | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue. | SwitchParameter | Named | False | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Unpublishing Microsoft SQL Database

This example shows how to unpublish a Microsoft SQL database.

|  |
| --- |
| $session = Get-VESQLRestoreSession  $database = Get-VESQLPublishedDatabase -Session $session[0] -Name "New SQL Database"  Unpublish-VESQLDatabase -Databases $database |

Perform the following steps:

1. Run the [Get-VESQLRestoreSession](get-vesqlrestoresession.md) cmdlet. Save the result to the $session variable.

The cmdlet will return an array of restore sessions. Note the ordinal number of the necessary restore session. In our example, it is the first restore session in the array.

1. Run the [Get-VESQLPublishedDatabase](get-vesqlpublisheddatabase.md) cmdlet. Set the $session variable as the Session parameter value and select the necessary restore session. Specify the Name parameter value. Save the result to the $database variable.
2. Run the Unpublish-VESQLDatabase cmdlet. Set the $database variable as the Databases parameter value.

Related Commands

* [Get-VESQLRestoreSession](get-vesqlrestoresession.md)
* [Get-VESQLPublishedDatabase](get-vesqlpublisheddatabase.md)


