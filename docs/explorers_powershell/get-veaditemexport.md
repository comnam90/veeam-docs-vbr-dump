---
title: "Get-VEADItemExport"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-veaditemexport.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Get-VEADItemExport


Short Description

Returns information about the export process for Active Directory objects and containers.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEADItemExport [-TargetHosts <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns information about the export process for Active Directory objects and containers.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| TargetHosts | Specifies the target hosts to which the objects or containers are exported.  This parameter accepts wildcard characters. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEADExport](veadexport.md)[] array that contains information about the export process of Active Directory objects or containers.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Export Processes for Active Directory Items

|  |  |
| --- | --- |
| This command returns a list of all ongoing export processes for Active Directory items. Save the result to the $export variable to be able to use it with other cmdlets.  |  | | --- | | $export = Get-VEADItemExport | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Export Processes for Active Directory Items Exported to Specific Server

|  |  |
| --- | --- |
| This command returns all active export processes that use "srv85" as a target server. Save the result to the $export variable to be able to use it with other cmdlets.  |  | | --- | | $export = Get-VEADItemExport -TargetHosts "srv85" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Export Processes for Active Directory Items Exported to Target Servers that Begin with Certain String

|  |  |
| --- | --- |
| This command returns all active export processes that use target servers whose DNS names begin with "srv". Save the result to the $export variable to be able to use it with other cmdlets.  |  | | --- | | $export = Get-VEADItemExport -TargetHosts "srv\*" | |

Page updated 2026-02-06

