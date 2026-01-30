---
title: "Get-VBRKMSServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrkmsserver.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRKMSServer


Short Description

Returns KMS servers added to the Veeam Backup & Replication console.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get KMS servers by the KMS server ID.

|  |
| --- |
| Get-VBRKMSServer -Id <Guid[]>  [<CommonParameters>] |

* Get KMS servers by the KMS server name.

|  |
| --- |
| Get-VBRKMSServer [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns a Key Management System server (KMS server) added to the Veeam Backup & Replication console.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of IDs for KMS servers. The cmdlet will return KMS servers with these IDs. | Guid[] | True | Named | True (ByPropertyName, ByValue) |
| Name | Specifies an array of names for KMS servers. The cmdlet will return KMS servers with these names. | String[] | False | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRKMSServer](vbrkmsserver.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting KMS Server by ID

|  |  |
| --- | --- |
| This command returns the 8f723f68-82c6-430d-8915-58a0582440a4 and 8f723f68-82c6-430d-8915-58a0582440a4 KMS servers.  |  | | --- | | Get-VBRKMSServer -Id "8f723f68-82c6-430d-8915-58a0582440a4" , "8f723f68-82c6-430d-8915-58a0582440a4" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting KMS Server by Name

|  |  |
| --- | --- |
| This command returns the thales.tech.local KMS server.  |  | | --- | | Get-VBRKMSServer -Name "thales.tech.local" | |


