---
title: "Get-VBRAmazonEC2VM"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbramazonec2vm.html"
last_updated: "5/3/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAmazonEC2VM


Short Description

Returns Amazon EC2 instances.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAmazonEC2VM -Region <VBRAmazonEC2Region>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the Amazon EC2 instances.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Region | Specifies AWS Regions in which you want to deploy Veeam Agent on cloud machines. | Accepts the VBRAmazonEC2Region object. To create this object, run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAmazonEC2VM](vbramazonec2vm.md)

Examples

Getting all Amazon EC2 Instances Available in Specific AWS Region

This example shows how to get all Amazon EC2 instances available in the Global AWS Region.

|  |
| --- |
| $account = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c"  $region = Get-VBRAmazonEC2Region -Account $account -RegionType Global -Name "eu-west-3"  $EC2 = Get-VBRAmazonEC2VM -Region $region |

Perform the following steps:

1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable.
2. Run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. Set the $account variable as the Account parameter. Set the Global value as the RegionType parameter value. Specify the Name parameter value. Save the result to the $region variable.
3. Run the Get-VBRAmazonEC2VM cmdlet. Set the $region variable as the Region parameter. Save the result to the $EC2 variable.

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Get-VBRAmazonEC2Region](get-vbramazonec2region.md)


