---
title: "Get-VBRCommand"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcommand.html"
last_updated: "8/1/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCommand


Short Description

Returns Veeam PowerShell module cmdlets.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Look for all Veeam cmdlets.

|  |
| --- |
| Get-VBRCommand [-V95] [-V90] [-V80] [-V100] [-V100] [-V120] [-V130]  [<CommonParameters>] |

* Look for Veeam cmdlets by name of the cmdlet.

|  |
| --- |
| Get-VBRCommand [[-Name] <String[]>] [-V80] [-V90] [-V95] [-V100] [-V110] [-V120] [-V130]  [<CommonParameters>] |

* Look for Veeam cmdlets by verb or noun the cmdlet uses.

|  |
| --- |
| Get-VBRCommand [-Verb <String[]>] [-Noun <String[]>] [-V80] [-V90] [-V95] [-V100] [-V110] [-V120] [-V130]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the list of available Veeam PowerShell cmdlets.

If you run this cmdlet without parameters, it will return the list of all Veeam cmdlets in the current session.

|  |
| --- |
| ![Get-VBRCommand](images/icon_note.webp) Note: |
| This cmdlet is available only for sessions started from Veeam Backup & Replication main menu. |

Parameters

| Parameter | Description | Required | Position | Accept | Accept Wildcard Characters |
| --- | --- | --- | --- | --- | --- |
| V95 | Defines that the cmdlet will return cmdlets added in version 9.5 of Veeam Backup & Replication. | False | Named | False | False |
| V90 | Defines that the cmdlet will return cmdlets added in version 9.0 of Veeam Backup & Replication. | False | Named | False | False |
| V80 | Defines that the cmdlet will return cmdlets added in version 8.0 of Veeam Backup & Replication. | False | Named | False | False |
| V100 | Defines that the cmdlet will return cmdlets added in version 10 of Veeam Backup & Replication. | False | Named | False | False |
| V110 | Defines that the cmdlet will return cmdlets added in version 11 of Veeam Backup & Replication. | False | Named | False | False |
| V120 | Defines that the cmdlet will return cmdlets added in version 12 of Veeam Backup & Replication. | False | Named | False | False |
| V130 | Defines that the cmdlet will return cmdlets added in version 13 of Veeam Backup & Replication. | False | Named | False | False |
| Name | Specifies the name of the command. Lists the commands that match the specified name or regular name patterns. | False | 1 | True (ByValue, ByProperty Name) | True |
| Noun | Specifies the noun. Lists the commands using the specified noun name. | False | Named | True (ByProperty Name) | True |
| Verb | Specifies the command verb. Lists the commands using the specified verb name. | False | Named | True (ByProperty Name) | True |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Cmdlets that Perform Remove Operations

|  |  |
| --- | --- |
| This command returns the list of Veeam cmdlets that perform remove operations.  |  | | --- | | Get-VBRCommand Remove\* | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cmdlets by Names

|  |  |
| --- | --- |
| This command returns Veeam cmdlets with names containing "Zip".  |  | | --- | | Get-VBRCommand -Name \*Zip\* | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Cmdlets Starting with Specific Verbs

|  |  |
| --- | --- |
| This command returns Veeam cmdlets with verbs "Get" and "Set".  |  | | --- | | Get-VBRCommand -Verb Get, Set | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Cmdlets with Specific Nouns in Names

|  |  |
| --- | --- |
| This command returns Veeam cmdlets with nouns containing "Job" and "Zip".  |  | | --- | | Get-VBRCommand -Noun \*Job\*, \*Zip\* | |


