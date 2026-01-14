---
title: "New-VBRAmazonEC2ProxyAppliance"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbramazonec2proxyappliance.html"
last_updated: "1/23/2024"
product_version: "13.0.1.1071"
---

# New-VBRAmazonEC2ProxyAppliance

In this article

Short Description

Defines settings for Amazon EC2 helper appliances.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRAmazonEC2ProxyAppliance -InstanceType <VBRAmazonEC2InstanceType> -Subnet <VBRAmazonEC2Subnet> -SecurityGroup <VBRAmazonEC2SecurityGroup> -RedirectorPort <int>  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRAmazonEC2ProxyAppliance object. This object contains settings for Amazon EC2 helper appliances.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| InstanceType | Specifies a Amazon EC2 instance type. The cmdlet will set the CPU and memory settings for a Amazon EC2 instance according to this instance type. | Accepts the [VBRAmazonEC2InstanceType](vbramazonec2instancetype.md) object. To get this object, run the [Get-VBRAmazonEC2InstanceType](get-vbramazonec2instancetype.md) cmdlet. | True | Named | False |
| Subnet | Specifies the Amazon VPC subnet. | Accepts the [VBRAmazonEC2Subnet](vbramazonec2subnet.md) object. To get this object, run the [Get-VBRAmazonEC2Subnet](get-vbramazonec2subnet.md) cmdlet. | True | Named | False |
| SecurityGroup | Specifies the Amazon EC2 security group. | Accepts the [VBRAmazonEC2SecurityGroup](vbramazonec2securitygroup.md) object. To get this object, run the [Get-VBRAmazonEC2SecurityGroup](get-vbramazonec2securitygroup.md) cmdlet. | True | Named | False |
| RedirectorPort | Specifies the redirection port number. Veeam Backup & Replication will use this port to connect to the proxy appliance.  Default: 443 | Int | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAmazonEC2ProxyAppliance object that contains settings of Amazon EC2 helper appliances.

Examples

Defining Settings for AmazonEC2 Help Appliance

This example shows how to define settings for the AmazonEC2 helper appliance.

|  |
| --- |
| $account = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c"  $region = Get-VBRAmazonEC2Region -Account $account -RegionType Global -Name "ap-northeast-1"  $instance = Get-VBRAmazonEC2InstanceType -Region $region  $vpc = Get-VBRAmazonEC2VPC -Region $region  $sgroup = Get-VBRAmazonEC2SecurityGroup -VPC $vpc  $subnet = Get-VBRAmazonEC2Subnet -VPC $vpc -AvailabilityZone "eu-west-1a"  New-VBRAmazonEC2ProxyAppliance -InstanceType $instance -Subnet $subnet -SecurityGroup $sgroup -RedirectorPort 443 |

Perform the following steps:

1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable.
2. Run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. Set the $account variable as the Account parameter value. Set the Global value as the RegionType parameter value. Specify the Name parameter value. Save the result to the $region variable.
3. Run the [Get-VBRAmazonEC2InstanceType](get-vbramazonec2instancetype.md) cmdlet. Set the $region variable as the Region parameter value. Save the result to the $instance variable.
4. Run the [Get-VBRAmazonEC2VPC](get-vbramazonec2vpc.md) cmdlet. Set the $region variable as the Region parameter value. Save the result to the $vpc variable.
5. Run the [Get-VBRAmazonEC2SecurityGroup](get-vbramazonec2securitygroup.md) cmdlet. Set the $vpc variable as the VPC parameter value. Save the result to the $sgroup variable.
6. Run the [Get-VBRAmazonEC2Subnet](get-vbramazonec2subnet.md) cmdlet. Set the $vpc variable as the VPC parameter value. Specify the AvailabilityZone parameter value. Save the result to the $subnet variable.
7. Run the New-VBRAmazonEC2ProxyAppliance cmdlet. Specify the following settings:

* Set the $instance variable as the InstanceType parameter value.
* Set the $subnet variable as the Subnet parameter value.
* Set the $sgroup variable as the SecurityGroup parameter value.
* Specify the RedirectorPort parameter value.

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Get-VBRAmazonEC2Region](get-vbramazonec2region.md)
* [Get-VBRAmazonEC2InstanceType](get-vbramazonec2instancetype.md)
* [Get-VBRAmazonEC2VPC](get-vbramazonec2vpc.md)
* [Get-VBRAmazonEC2SecurityGroup](get-vbramazonec2securitygroup.md)
* [Get-VBRAmazonEC2Subnet](get-vbramazonec2subnet.md)

Page updated 1/23/2024

Page content applies to build 13.0.1.1071
