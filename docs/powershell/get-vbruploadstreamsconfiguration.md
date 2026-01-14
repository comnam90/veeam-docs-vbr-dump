---
title: "Get-VBRUploadStreamsConfiguration"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbruploadstreamsconfiguration.html"
last_updated: "4/23/2024"
product_version: "13.0.1.1071"
---

# Get-VBRUploadStreamsConfiguration

In this article

Short Description

Returns details on data transfer settings for job sessions.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRUploadStreamsConfiguration  [<CommonParameters>] |

Detailed Description

This cmdlet returns the VBRUploadStreamsConfiguration object. This object contains the following details on data transfer settings for job sessions:

* State: specifies the state of the multithreaded data transfer option. It can be either enabled (True) or disabled (False).
* StreamCount: specifies the number of TCP/IP connections per job session.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRUploadStreamsConfiguration

Examples

Getting Details on Data Transfer Settings

This command returns the following details on data transfer settings for job sessions:

* The multithreaded data transfer option is enabled.
* The number of TCP/IP connections per job is set to five.

|  |
| --- |
| Get-VBRUploadStreamsConfiguration              Enabled                  StreamCount              -------                  -----------                 True                            5 |

Page updated 4/23/2024

Page content applies to build 13.0.1.1071
