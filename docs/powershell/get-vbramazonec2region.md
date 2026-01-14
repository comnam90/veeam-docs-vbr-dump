---
title: "Get-VBRAmazonEC2Region"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbramazonec2region.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAmazonEC2Region

In this article

Short Description

Returns AWS Regions and datacenters.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAmazonEC2Region -Account <VBRAmazonAccount> -RegionType <VBRAmazonRegionType> {Global | Government | China} [-Name <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of AWS Regions and datacenters.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies AWS credentials records. Veeam Backup & Replication will use these credentials to connect to the AWS account. | Accepts the VBRAmazonAccount object. To get this object, run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. | True | Named | False |
| RegionType | Specifies the AWS Regions type:   * Global * Government * China   Veeam Backup & Replication will get an array of Amazon EC2 Regions based on the specified type. | VBRAmazonRegionType | True | Named | False |
| Name | Specifies the AWS datacenter. The cmdlet will return the datacenter with the specified name. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAmazonEC2Region](vbramazonec2region.md)

Examples

Getting All AWS Regions by Region Type

This example shows how to get an array of all AWS Regions for the Global region type.

|  |
| --- |
| $account = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c"  Get-VBRAmazonEC2Region -Account $account -RegionType Global -Name "eu-west-3" |

Perform the following steps:

1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable.
2. Run the Get-VBRAmazonEC2Region cmdlet. Set the $account variable as the Account parameter value. Set the Global value as the RegionType parameter value. Specify the Name parameter value.

Related Commands

[Get-VBRAmazonAccount](get-vbramazonaccount.md)

Page updated 2/28/2024

Page content applies to build 13.0.1.1071
