---
title: "Get-VBRvCDCDPFilter"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvcdcdpfilter.html"
last_updated: "3/4/2024"
product_version: "13.0.1.1071"
---

# Get-VBRvCDCDPFilter


Short Description

Returns a list of Veeam I/O filters installed on an ESXi host.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRvCDCDPFilter -Server <CHost> [-OrganizationVdc <CVcdOrganizationVdcItem[]>] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet returns a list of Veeam I/O filters installed on an ESXi host.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the ESXi host for which you want to get the list of installed I/O filters. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| OrganizationVdc | Specifies an array of organization VDCs for which you want to get the list of installed I/O filters. | Accepts the CVcdOrganizationVdcItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRvCDCDPFilter object that returns a list of Veeam I/O filters installed on an ESXi host.

Examples

Getting List of Veeam I/O Filters Installed on ESXi Host

This example shows how to get a list of Veeam I/O filters installed on an ESXi host.

|  |
| --- |
| $server = Get-VBRServer  Get-VBRvCDCDPFilter -Server $server |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Save the result to the $server variable.
2. Run the Get-VBRvCDCDPFilter cmdlet. Set the $server variable as the Server parameter value.

Related Commands

[Get-VBRServer](get-vbrserver.md)


