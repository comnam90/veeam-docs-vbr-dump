---
title: "Get-VBRPhysicalHost"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrphysicalhost.html"
last_updated: "12/18/2023"
product_version: "13.0.1.1071"
---

# Get-VBRPhysicalHost


Short Description

Returns managed servers added to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRPhysicalHost [-UpdateRequired]  [<CommonParameters>] |

Detailed Description

This cmdlet returns managed servers that are added to the backup infrastructure. The cmdlet will return the following types of managed servers:

* VMware vSphere servers
* Microsoft Hyper-V servers
* Microsoft SMB3 servers
* Microsoft Windows servers
* Azure proxy

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| UpdateRequired | Defines that the cmdlet will return only the managed servers, which require an upgrade of the components. If you do not provide this parameter, the cmdlet will return all managed servers added to the backup infrastructure. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRPhysicalHost object that contains managed servers added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Managed Servers

|  |  |
| --- | --- |
| This command returns all managed servers added to the backup infrastructure.  |  | | --- | | Get-VBRPhysicalHost | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Managed Servers that Require Upgrade

|  |  |
| --- | --- |
| This command returns all managed servers that require an upgrade of the components.  |  | | --- | | Get-VBRPhysicalHost -UpdateRequired | |


