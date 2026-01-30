---
title: "Get-VBRCloudHardwarePlan"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudhardwareplan.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCloudHardwarePlan


Short Description

Returns existing hardware plans.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a VCP license.

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all existing hardware plans.

|  |
| --- |
| Get-VBRCloudHardwarePlan  [<CommonParameters>] |

* Get hardware plans by name or by platform.

|  |
| --- |
| Get-VBRCloudHardwarePlan [-Name <string[]>] [-Platform <VBRPlatform> {VMWare | HyperV}]  [<CommonParameters>] |

* Get hardware plans by ID.

|  |
| --- |
| Get-VBRCloudHardwarePlan -Id <guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns existing hardware plans.

You can get the list of all hardware plans or search for instances directly by name, virtuallization platform or ID.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of the hardware plan names you want to get. | String[] | False | Named | True (ByValue, |
| Platform | Specifies the platform of the hardware plan:   * VMWare * HyperV * vCD * LinuxPhysical * WindowsPhysical * Tape * CustomPlatform | VBRPlatform | False | Named | True (ByProperty Name) |
| ID | Specifies the array of the IDs of the [VBRViCloudHardwarePlan](vbrvicloudhardwareplan.md) or [VBRHvCloudHardwarePlan](vbrhvcloudhardwareplan.md) object you want to get. | Accepts GUID[] or string[]. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Objects

* [VBRHvCloudHardwarePlan](vbrhvcloudhardwareplan.md)
* [VBRViCloudHardwarePlan](vbrvicloudhardwareplan.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Hardware Plans

|  |  |
| --- | --- |
| This command returns all existing hardware plans.  |  | | --- | | Get-VBRCloudHardwarePlan | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All VMware Hardware Plans

|  |  |
| --- | --- |
| This command returns all VMware hardware plans.  |  | | --- | | Get-VBRCloudHardwarePlan -Platform VMWare | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting All Hyper-V Hardware Plans

|  |  |
| --- | --- |
| This command returns all Hyper-V hardware plans.  |  | | --- | | Get-VBRCloudHardwarePlan -Platform HyperV | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Hardware Plan by Name

|  |  |
| --- | --- |
| This command returns a hardware plan named VMware Silver.  |  | | --- | | Get-VBRCloudHardwarePlan -Name "VMware Silver" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Getting Hardware Plan by Platform and Name

|  |  |
| --- | --- |
| This command returns a Hyper-V hardware plan named Hyper-V Silver.  |  | | --- | | Get-VBRCloudHardwarePlan -Name "Hyper-V Silver" -Platform HyperV | |


