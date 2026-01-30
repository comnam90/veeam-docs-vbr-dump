---
title: "Get-VBRComputerFileProxyServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcomputerfileproxyserver.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# Get-VBRComputerFileProxyServer


Short Description

Returns general-purpose backup proxies added to the Veeam Backup & Replication infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all general-purpose backup proxies added to the Veeam Backup & Replication infrastructure.

|  |
| --- |
| Get-VBRComputerFileProxyServer  [<CommonParameters>] |

* Get general-purpose backup proxies by the proxy name.

|  |
| --- |
| Get-VBRComputerFileProxyServer -Name <string[]>  [<CommonParameters>] |

* Get general-purpose backup proxies by the proxy ID.

|  |
| --- |
| Get-VBRComputerFileProxyServer -Id <guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of general-purpose backup proxies added to your Veeam Backup & Replication infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names of general-purpose backup proxy. The cmdlet will return an array of backup proxies with the specified name. | String | False | Named | False |
| Id | Specifies an array of IDs of general-purpose backup proxy. The cmdlet will return an array of backup proxies with the specified ID. | Guid | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRComputerFileProxyServer object that contains settings of the general-purpose backup proxy added to the Veeam Backup & Replication infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All General-purpose Backup Proxies

|  |  |
| --- | --- |
| This command gets all general-purpose backup proxies that are added to the Veeam Backup & Replication infrastructure. The cmdlet output will contain the following details on general-purpose backup proxies: ID, Description, Server and ConcurrentTaskNumber.  |  | | --- | | Get-VBRComputerFileProxyServer  Id                            Description                   Server                                 ConcurrentTaskNumber  --                            -----------                   ------                                 --------------------  2df7b4a9-e230-4bc7-97a6-db... Created by Veeam Backup & ... Veeam.Backup.Core.Common.C...                             2  5a7c25b9-87cb-41e3-bb1b-81... Created by Powershell at 8... Veeam.Backup.Core.Common.C...                             7 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting General-purpose Backup Proxy by Name

|  |  |
| --- | --- |
| This command gets all general-purpose backup proxies that are added to the Veeam Backup & Replication infrastructure by the backup proxy name. The cmdlet output will contain the following details on backup proxies: ID, Description, Server and ConcurrentTaskNumber.  |  | | --- | | Get-VBRComputerFileProxyServer -Name "File Proxy 01"  Id                            Description                   Server                                 ConcurrentTaskNumber  --                            -----------                   ------                                 --------------------  dbb139cf-4ac1-4a9e-95fa-e9... Created by Powershell at 8... Veeam.Backup.Core.Common.C...                             2 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting General-purpose Backup Proxies by ID

|  |  |
| --- | --- |
| This command gets all general-purpose backup proxies that are added to the Veeam Backup & Replication infrastructure by the backup proxy ID. The cmdlet output will contain the following details on general-purpose backup proxies: ID, Description, Server and ConcurrentTaskNumber.  |  | | --- | | Get-VBRComputerFileProxyServer -Id "02da6898-308d-44ac-b007-94d81576c296"  Id                            Description                   Server                                 ConcurrentTaskNumber  --                            -----------                   ------                                 --------------------  02da6898-308d-44ac-b007-94... Created by Powershell at 8... Veeam.Backup.Core.Common.C...                             2 | |


