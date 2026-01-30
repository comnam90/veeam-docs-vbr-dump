---
title: "Update-VBRServerComponent"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/update-vbrservercomponent.html"
last_updated: "1/29/2024"
product_version: "13.0.1.1071"
---

# Update-VBRServerComponent


Short Description

Upgrades all components on managed servers.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Update-VBRServerComponent [-Component <VBRPhysicalHost[]>] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet upgrades all components on managed servers that are added to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Component | Specifies an array of managed servers. The cmlet will upgrade all components on these servers. | Accepts the VBRPhysicalHost[] object. To get this object, run the [Get-VBRPhysicalHost](get-vbrphysicalhost.md) cmdlet. | False | Named | True (ByValue, |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Upgrading all Servers Added to Backup Infrastructure

|  |  |
| --- | --- |
| This command upgrades all managed servers that are added to the backup infrastructure.  |  | | --- | | Update-VBRServerComponent | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Upgrading Servers that Require Update

|  |  |
| --- | --- |
| This example shows how to upgrade only those managed servers whose components require update.  |  | | --- | | $servers = Get-VBRPhysicalHost -UpdateRequired  Update-VBRServerComponent -Component $servers |  Perform the following steps:   1. Run the [Get-VBRPhysicalHost](get-vbrphysicalhost.md) cmdlet. Provide the UpdateRequired parameter. Save the result to the $servers variable. 2. Run the Update-VBRServerComponent cmdlet. Set the $servers variable as the Component parameter value. |

Related Commands

[Get-VBRPhysicalHost](get-vbrphysicalhost.md)


