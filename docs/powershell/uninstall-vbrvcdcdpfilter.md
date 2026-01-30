---
title: "Uninstall-VBRvCDCDPFilter"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/uninstall-vbrvcdcdpfilter.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Uninstall-VBRvCDCDPFilter


Short Description

Removes Veeam I/O filter from organization VDCs.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Uninstall-VBRvCDCDPFilter -OrganizationVdc <CVcdOrganizationVdcItem[]> [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes Veeam I/O filter from organization VDCs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| OrganizationVdc | Specifies an array of organization VDCs from which you want to uninstall Veeam I/O filters. | Accepts the CVcdOrganizationVdcItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will uninstall the I/O filter on VDC organizations without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CBaseSession object that defines session settings.

Examples

Uninstalling Veeam I/O Filters on Organization VDCs

This example shows how to uninstall Veeam I/O filter from organization VDCs.

|  |
| --- |
| $server = Get-VBRServer -Name "Cloud Server"  $organization = Find-VBRvCloudEntity -Server $server -OrganizationVdc  Uninstall-VBRvCDCDPFilter -OrganizationVdc $organization[2] |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Specify the Server and OrganizationVdc parameters values. Save the result to the $organization variable.
3. Run the Uninstall-VBRvCDCDPFilter cmdlet. Set the $organization[2] variable as the OrganizationVdc parameter value.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRvCloudEntity](find-vbrvcloudentity.md)


