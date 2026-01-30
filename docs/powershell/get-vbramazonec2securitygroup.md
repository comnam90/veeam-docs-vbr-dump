---
title: "Get-VBRAmazonEC2SecurityGroup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbramazonec2securitygroup.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAmazonEC2SecurityGroup


Short Description

Returns an array of AmazonEC2 security groups.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAmazonEC2SecurityGroup -VPC <VBRAmazonEC2VPC> [-Name <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of Amazon EC2 security groups that are configured for the specified Amazon VPC.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| VPC | Specifies an Amazon VPC. | Accepts the [VBRAmazonEC2VPC](vbramazonec2vpc.md) object. To get this object, run the [Get-VBRAmazonEC2VPC](get-vbramazonec2vpc.md) cmdlet. | True | Named | False |
| Name | Specifies the name of the security group. The cmdlet will return the security group with this name. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAmazonEC2SecurityGroup](vbramazonec2securitygroup.md)

Examples

Getting Amazon EC2 Security Groups for Selected VCP

This example shows how to get an array of Amazon EC2 security groups that are configured for selected Amazon VCP.

|  |
| --- |
| $account = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c"  $region = Get-VBRAmazonEC2Region -Account $account -RegionType Global -Name "eu-west-3"  $vpc = Get-VBRAmazonEC2VPC -Region $region  Get-VBRAmazonEC2SecurityGroup -VPC $vpc |

Perform the following steps:

1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable.
2. Run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. Set the $account variable as the Account parameter value. Set the Global value as the RegionType parameter value. Specify the Name parameter value. Save the result to the $region variable.
3. Run the [Get-VBRAmazonEC2VPC](get-vbramazonec2vpc.md) cmdlet. Set the $region variable as the Region parameter value. Save the result to the $vpc variable.
4. Run the Get-VBRAmazonEC2SecurityGroup cmdlet. Set the $vpc variable as the VPC parameter value.

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Get-VBRAmazonEC2Region](get-vbramazonec2region.md)
* [Get-VBRAmazonEC2VPC](get-vbramazonec2vpc.md)


