---
title: "Get-VBRYARARule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbryararule.html"
last_updated: "12/5/2024"
product_version: "13.0.1.1071"
---

# Get-VBRYARARule


Short Description

Returns YARA rules.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRYARARule  [<CommonParameters>] |

Detailed Description

This cmdlet returns YARA rules. By default, they are located in the C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules folder.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRYARARule](vbryararule.md)

Examples

Getting YARA Rules

This command returns YARA rules. By default, they are located in the C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules folder.

|  |
| --- |
| Get-VBRYARARule |


