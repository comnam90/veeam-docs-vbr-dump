---
title: "Get-VBRFreeAgentInstanceConsumptionStatus"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrfreeagentinstanceconsumptionstatus.html"
last_updated: "2/5/2024"
product_version: "13.0.1.1071"
---

# Get-VBRFreeAgentInstanceConsumptionStatus


Short Description

Returns a state of the instance consumption by non-licensed Veeam Agents.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRFreeAgentInstanceConsumptionStatus  [<CommonParameters>] |

Detailed Description

This cmdlet returns a state of the instance consumption by non-licensed Veeam Agents.

* False - indicates that the instance consumption by non-licensed Veeam Agents option is disabled.
* True - indicates that the instance consumption by non-licensed Veeam Agents option is enabled.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Example

Getting State of Instance Consumption

This command returns a state of the instance consumption by non-licensed Veeam Agents.

|  |
| --- |
| Get-VBRFreeAgentInstanceConsumptionStatus  False |


