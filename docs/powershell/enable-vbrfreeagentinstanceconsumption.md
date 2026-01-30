---
title: "Enable-VBRFreeAgentInstanceConsumption"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrfreeagentinstanceconsumption.html"
last_updated: "5/20/2024"
product_version: "13.0.1.1071"
---

# Enable-VBRFreeAgentInstanceConsumption


Short Description

Enables instance consumption by unlicensed Veeam Agents.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRFreeAgentInstanceConsumption  [<CommonParameters>] |

Detailed Description

This cmdlet enables instance consumption by unlicensed Veeam Agents. This option allows Veeam Agents to create backups to Veeam Backup & Replication.

Run the [Disable-VBRFreeAgentInstanceConsumption](disable-vbrfreeagentinstanceconsumption.md) cmdlet to disable this option.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Enabling Instance Consumption by Veeam Agents

This command enables the instance consumption by unlicensed Veeam Agents.

|  |
| --- |
| Enable-VBRFreeAgentInstanceConsumption |


