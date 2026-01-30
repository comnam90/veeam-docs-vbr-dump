---
title: "Set-VBRLocation"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrlocation.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Set-VBRLocation


Short Description

Modifies geographic locations in Veeam Backup & Replication.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRLocation -Location <VBRLocation> -Name <string> [-PassThru]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of a geographic location created in Veeam Backup & Replication.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Location | Specifies the location you want to modify. | Accepts the VBRLocation object. To get this object, run the [Get-VBRLocation](get-vbrlocation.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the name you want to assign to the location.  The maximum length of the location name is 255 characters. | String | True | Named | True (ByProperty Name) |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRLocation object that contains the geographic location.

Examples

Changing Geographic Location Name

This example shows how to change the geographic location name.

|  |
| --- |
| $location = Get-VBRLocation -Name "ABC North"  Set-VBRLocation -Location $location -Name "Central" |

Perform the following steps:

1. Run the [Get-VBRLocation](get-vbrlocation.md) cmdlet. Specify the Name parameter value. Save the result to the $location variable.
2. Run the Set-VBRLocation cmdlet. Set the $location variable as the Location parameter value. Specify the Name parameter value.

Related Commands

[Get-VBRLocation](get-vbrlocation.md)


