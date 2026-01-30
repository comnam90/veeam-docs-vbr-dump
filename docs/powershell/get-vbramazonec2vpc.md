---
title: "Get-VBRAmazonEC2VPC"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbramazonec2vpc.html"
last_updated: "12/13/2023"
product_version: "13.0.1.1071"
---

# Get-VBRAmazonEC2VPC


Short Description

Returns an Amazon VPC.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAmazonEC2VPC -Region <VBRAmazonEC2Region> [-AWSObjectId <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an Amazon VPC.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Region | Specifies an AWS region. The cmdlet will return Amazon VPCs that are configured for this AWS location. | Accepts the VBRAmazonEC2Region object. To get this object, run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. | True | Named | False |
| AWSObjectId | Specifies the internal ID of the Amazon VPC. The cmdlet will return the VPC with this ID. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAmazonEC2VPC](vbramazonec2vpc.md)

Examples

Getting Amazon EC2 VPCs for Specified AWS Region

This example shows how to get Amazon EC2 VPCs that are configured for the specified AWS region.

|  |
| --- |
| $account = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c"  $region = Get-VBRAmazonEC2Region -Account $account -RegionType Global -Name "ap-northeast-1"  Get-VBRAmazonEC2VPC -Region $region |

Perform the following steps:

1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable.
2. Run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. Set the $account variable as the Account parameter value. Set the Global value as the RegionType parameter value. Specify the Name parameter value. Save the result to the $region variable.
3. Run the Get-VBRAmazonEC2VPC cmdlet. Set the $region variable as the Region parameter value.

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Get-VBRAmazonEC2Region](get-vbramazonec2region.md)


