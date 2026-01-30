---
title: "Get-VBRAmazonEC2InstanceType"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbramazonec2instancetype.html"
last_updated: "12/13/2023"
product_version: "13.0.1.1071"
---

# Get-VBRAmazonEC2InstanceType


Short Description

Returns an array of Amazon EC2 instances.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAmazonEC2InstanceType -Region <VBRAmazonEC2Region> [-Name <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of Amazon EC2 instance types that are available for the specified AWS region. It also returns the information about the memory and the CPU available for each instance type.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Region | Specifies an AWS region. The cmdlet will return an array of Amazon EC2 instance types that are available for the specified AWS region. | Accepts the [VBRAmazonEC2Region](vbramazonec2region.md) object. To get this object, run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. | True | Named | False |
| Name | Specifies the name of the Amazon EC2 instance type. The cmdlet will return the instance type with this name. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAmazonEC2InstanceType](vbramazonec2instancetype.md)

Examples

Getting All Instance Types from Specified AWS Region

This example shows how to get an array of all instance types from the specified AWS region. The cmdlet will return all instance types from the ap-northeast-1 AWS region.

|  |
| --- |
| $account = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c"  $region = Get-VBRAmazonEC2Region -Account $account -RegionType Global -Name "ap-northeast-1"  Get-VBRAmazonEC2InstanceType -Region $region |

Perform the following steps:

1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable.
2. Run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. Set the $account variable as the Account parameter value. Set the Global value as the RegionType parameter value. Specify the Name parameter value. Save the result to the $region variable.
3. Run the Get-VBRAmazonEC2InstanceType cmdlet. Set the $region variable as the Region parameter value.

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Get-VBRAmazonEC2Region](get-vbramazonec2region.md)


