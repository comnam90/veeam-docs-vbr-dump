---
title: "Set-VBRStorageLatencyControlOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrstoragelatencycontroloptions.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Set-VBRStorageLatencyControlOptions

In this article

Short Description

Modifies storage latency control settings on the production datastores.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRStorageLatencyControlOptions [-LatencyLimitMs <int>] [-ThrottlingIOLimitMs <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies storage latency control settings on the production datastores.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| LatencyLimitMs | Specifies the I/O latency limit at which Veeam Backup & Replication will not assign new tasks that are targeted at the datastore.  Default: 20 ms. | Int | False | Named | False |
| ThrottlingIOLimitMs | Specifies the I/O latency speed limit. When Veeam Backup & Replication reaches this limit, it will decrease the speed at which it either gets data from a datastore or writes data to it.  Default: 30 ms. | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRLatencyControlOptions object that contains settings of the storage latency control on the production datastores.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying I/O Latency Tasks Limit

|  |  |
| --- | --- |
| This command sets the I/O latency limit of new tasks that are targeted at the datastore to 50 ms.  |  | | --- | | Set-VBRStorageLatencyControlOptions -LatencyLimitMs 50 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying I/O Latency Speed Limit

|  |  |
| --- | --- |
| This command sets the I/O latency speed limit to 40 ms.  |  | | --- | | Set-VBRStorageLatencyControlOptions -ThrottlingIOLimitMs 40 | |

Page updated 4/24/2024

Page content applies to build 13.0.1.1071
