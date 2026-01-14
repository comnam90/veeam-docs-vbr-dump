---
title: "Get-VBRAmazonEC2Subnet"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbramazonec2subnet.html"
last_updated: "2/20/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAmazonEC2Subnet

In this article

Short Description

Returns an array of Amazon VPC subnets.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get an Amazon VPC subnet by the sunbnet IP range.

|  |
| --- |
| Get-VBRAmazonEC2Subnet -VPC <VBRAmazonEC2VPC> -Name <string>  [<CommonParameters>] |

* Get an Amazon EC2 subnet by the Availability Zone in which the subnet resides.

|  |
| --- |
| Get-VBRAmazonEC2Subnet -VPC <VBRAmazonEC2VPC> [-AvailabilityZone <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of subnets that are available in the selected Amazon VPC.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| VPC | Specifies the Amazon VPC. | Accepts the VBRAmazonEC2VPC object. To get this object, run the [Get-VBRAmazonEC2VPC](get-vbramazonec2vpc.md) cmdlet. | True | Named | False |
| Name | Specifies the IP range. The cmdlet will return the Amazon VPC subnet with this IP range. | String | True | Named | False |
| AvailabilityZone | Specifies the Availability Zone.  The cmdlet will return the Amazon VPC subnet that resides in the specified Availability Zone. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAmazonEC2Subnet](vbramazonec2subnet.md)

Examples

Getting Amazon VPC Subnet by Availability Zone

This example shows how to get the Amazon VPC subnet by geographic location and the associated Availability Zone.

|  |
| --- |
| $account = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c"  $region = Get-VBRAmazonEC2Region -Account $account -RegionType Global -Name "ap-northeast-1"  $vpc = Get-VBRAmazonEC2VPC -Region $region  Get-VBRAmazonEC2Subnet -VPC $vpc -AvailabilityZone "eu-west-1a" |

Perform the following steps:

1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable.
2. Run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. Set the $account variable as the Account parameter value. Set the Global value as the RegionType parameter value. Specify the Name parameter value. Save the result to the $region variable.
3. Run the [Get-VBRAmazonEC2VPC](get-vbramazonec2vpc.md) cmdlet. Set the $region variable as the Region parameter value. Save the result to the $vpc variable.
4. Run the Get-VBRAmazonEC2Subnet cmdlet. Set the $vpc variable as the VCP parameter value. Specify the AvailabilityZone parameter value.

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Get-VBRAmazonEC2Region](get-vbramazonec2region.md)
* [Get-VBRAmazonEC2VPC](get-vbramazonec2vpc.md)

Page updated 2/20/2024

Page content applies to build 13.0.1.1071
