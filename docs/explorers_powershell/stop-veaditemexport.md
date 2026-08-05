---
title: "Stop-VEADItemExport"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/stop-veaditemexport.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Stop-VEADItemExport


Short Description

Stops the export process for an Active Directory object or container.

Applies to

Veeam Backup & Replication

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VEADItemExport [-Export] <VeadExport> [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet stops an active export process for an Active Directory object or container.

|  |
| --- |
| Note |
| Export processes will not stop automatically if you close the PowerShell console. To stop an export process before it completes, you must run the Stop-VEADItemExport cmdlet. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Export | Specifies the export process for an Active Directory object or container. The cmdlet will stop this export process. | Accepts the [VEADExport](veadexport.md) object. To get this object, run the [Get-VEADItemExport](get-veaditemexport.md) cmdlet. | True | 0 | True (ByValue) |
| Force | Defines that the cmdlet will show no prompt before executing the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About Common Parameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

None.

Example

Stopping Export Process for Active Directory Object or Container

This example shows how to stop the export process for an Active Directory object or a container.

|  |
| --- |
| $export = Get-VEADItemExport -TargetHosts "addc03"  Stop-VEADItemExport -Export $export |

Perform the following steps:

1. Run the [Get-VEADItemExport](get-veaditemexport.md) cmdlet. Specify the TargetHosts parameter value. Save the result to the $export variable.
2. Run the Stop-VEADItemExport cmdlet. Set the $export variable as the Export parameter value.

Related Commands

* [Start-VEADItemExport](start-veaditemexport.md)
* [Get-VEADItemExport](get-veaditemexport.md)

Page updated 2026-04-23

