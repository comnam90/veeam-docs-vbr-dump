---
title: "Get-VBRNASProxyServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnasproxyserver.html"
last_updated: "1/19/2024"
product_version: "13.0.1.1071"
---

# Get-VBRNASProxyServer

In this article

Short Description

Returns file backup proxy servers added to the Veeam Backup & Replication infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all file backup proxy servers added to the Veeam Backup & Replication infrastructure.

|  |
| --- |
| Get-VBRNASProxyServer  [<CommonParameters>] |

* Get file backup proxy servers by the backup proxy server name.

|  |
| --- |
| Get-VBRNASProxyServer -Name <string[]>  [<CommonParameters>] |

* Get file backup proxy servers by the backup proxy server ID.

|  |
| --- |
| Get-VBRNASProxyServer -Id <guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of file backup proxy servers added to the Veeam Backup & Replication infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names of a file backup proxy server. The cmdlet will return an array of these servers with the specified name. | String[] | True | Named | False |
| Id | Specifies an array of IDs of file backup proxy server. The cmdlet will return an array of these servers with the specified ID. | Guid[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNASProxyServer](vbrnasproxyserver.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All File Backup Proxy Servers

|  |  |
| --- | --- |
| This command gets all file backup proxy servers that are added to the Veeam Backup & Replication infrastructure. The cmdlet output will contain the following details on file backup proxy servers: ID, Description, Server and ConcurrentTaskNumber.  |  | | --- | | Get-VBRNASProxyServer  Id                            Description                   Server                                 ConcurrentTaskNumber  --                            -----------                   ------                                 --------------------  2df7b4a9-e230-4bc7-97a6-db... Created by Veeam Backup & ... Veeam.Backup.Core.Common.C...                             2  5a7c25b9-87cb-41e3-bb1b-81... Created by Powershell at 8... Veeam.Backup.Core.Common.C...                             7 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting File Backup Proxy Server by Name

|  |  |
| --- | --- |
| This command gets all file backup proxy servers that are added to the Veeam Backup & Replication infrastructure by the backup proxy server name. The cmdlet output will contain the following details on file backup proxy servers: ID, Description, Server and ConcurrentTaskNumber.  |  | | --- | | Get-VBRNASProxyServer -Name "File Backup Proxy 09"  Id                            Description                   Server                                 ConcurrentTaskNumber  --                            -----------                   ------                                 --------------------  dbb139cf-4ac1-4a9e-95fa-e9... Created by Powershell at 8... Veeam.Backup.Core.Common.C...                             2 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting File Backup Proxy Server by ID

|  |  |
| --- | --- |
| This command gets all file backup proxy servers that are added to the Veeam Backup & Replication infrastructure by the backup proxy server ID. The cmdlet output will contain the following details on file backup proxy servers: ID, Description, Server and ConcurrentTaskNumber.  |  | | --- | | Get-VBRNASProxyServer -Id "02da6898-308d-44ac-b007-94d81576c296"  Id                            Description                   Server                                 ConcurrentTaskNumber  --                            -----------                   ------                                 --------------------  02da6898-308d-44ac-b007-94... Created by Powershell at 8... Veeam.Backup.Core.Common.C...                             2 | |

Page updated 1/19/2024

Page content applies to build 13.0.1.1071
