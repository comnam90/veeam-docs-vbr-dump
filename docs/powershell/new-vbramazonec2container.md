---
title: "New-VBRAmazonEC2Container"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbramazonec2container.html"
last_updated: "10/15/2025"
product_version: "13.0.1.1071"
---

# New-VBRAmazonEC2Container


Short Description

Defines a scope of Amazon EC2 instances, EC2 tags or AWS datacenters for a protection group.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRAmazonEC2Container -Region <VBRAmazonEC2Region> -Entity <Object[]> [-ExcludeEntities] [-ExcludedEntity <Object[]>] [-AutoAssignIAMRole]  [<CommonParameters>] |

Detailed Description

This cmdlet defines the [VBRAmazonEC2Container](vbramazonec2container.md) object. This object contains a scope of Amazon EC2 instances, EC2 tags or AWS datacenters.

Use this object to create a protection group with the [Add-VBRProtectionGroup](add-vbrprotectiongroup.md) cmdlet. After you create a protection group, Veeam Backup & Replication will deploy Veeam Agent on EC2 instances added to the scope of the protection group.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Region | Specifies AWS Regions in which you want to deploy Veeam Agent on cloud machines. | Accepts the VBRAmazonEC2Region object. To create this object, run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Entity | Specifies an array of the following entities that the cmdlet will add to a scope of a protection group:   * EC2 instances. * EC2 tags. * AWS datacenters. | Accepts the Object[] object. To get this object, run the following  cmdlets:   * [Get-VBRAmazonEC2VM](get-vbramazonec2vm.md) * [New-VBRAmazonEC2Tag](new-vbramazonec2tag.md) * [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) | True | Named | True (ByValue, ByPropertyName) |
| ExcludeEntities | Defines that the cmdlet will exclude the following entities from a scope of a protection group:   * EC2 instances. * EC2 tags. * AWS datacenters.   Provide the ExcludedEntity parameter to specify the excluded entities. | SwitchParameter | False | Named | True (ByPropertyName, ByValue) |
| ExcludedEntity | Specifies an array of the following entities that the cmdlet will exclude from a scope of a protection group:   * EC2 instances. * EC2 tags. * AWS datacenters. | Accepts the Object[] object. To get this object, run the following  cmdlets:   * [Get-VBRAmazonEC2VM](get-vbramazonec2vm.md) * [New-VBRAmazonEC2Tag](new-vbramazonec2tag.md) * [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) | False | Named | True (ByValue, ByPropertyName) |
| AutoAssignIAMRole | Defines that the cmdlet will automatically set the IAM role with the AmazonSSMManagedInstanceCore policy to the EC2 instances that you want to back up.  If you do not provide this parameter, you will have to set the IAM role manually. | SwitchParameter | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAmazonEC2Container](vbramazonec2container.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Scope of Amazon EC2 Instances for Protection Group

|  |  |
| --- | --- |
| This example shows how to define the scope of Amazon EC2 instances to add them to a protection group.  |  | | --- | | $AWSaccount = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c"  $AWSregion = Get-VBRAmazonEC2Region -Account $AWSaccount -RegionType Global -Name "eu-central-1"  $instances = Get-VBRAmazonEC2VM -Region $AWSregion  $container = New-VBRAmazonEC2Container -Region $AWSregion -Entity $instances |  Perform the following steps:   1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $AWSaccount variable. 2. Run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. Set the $AWSaccount variable as the Account parameter value. Set the Global value as the RegionType parameter value. Specify the Name parameter value. Save the result to the $AWSregion variable. 3. Run the [Get-VBRAmazonEC2VM](get-vbramazonec2vm.md) cmdlet. Set the $AWSregion variable as the Region parameter value. Save the result to the $instances variable. 4. Run the New-VBRAmazonEC2Container cmdlet. Set the $AWSregion variable as the Region parameter value. Set the $instances variable as the Entity parameter value. Save the result to the $container variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Scope of AWS Datacenters for Protection Group

|  |  |
| --- | --- |
| This example shows how to define the scope of Amazon EC2 datacenters to add them to a protection group.  |  | | --- | | $AWSaccount = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c"  $datacenter = Get-VBRAmazonEC2Region -Account $AWSaccount -RegionType Global -Name "eu-central-1"  $container = New-VBRAmazonEC2Container -Region $AWSregion -Entity $datacenter |  Perform the following steps:   1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $AWSaccount variable. 2. Run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. Set the $AWSaccount variable as the Account parameter value. Set the Global value as the RegionType parameter value. Specify the Name parameter value. Save the result to the $datacenter variable. 3. Run the New-VBRAmazonEC2Container cmdlet. Set the $AWSregion variable as the Region parameter value. Set the $datacenter variable as the Entity parameter value. Save the result to the $container variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Defining Scope of AWS Tags for Protection Group

|  |  |
| --- | --- |
| This example shows how to define the to define the scope of Amazon EC2 tags to add them to a protection group.  |  | | --- | | $AWSaccount = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c"  $AWSregion = Get-VBRAmazonEC2Region -Account $AWSaccount -RegionType Global -Name "eu-central-1"  $tag = New-VBRAmazonEC2Tag -Key "owner" -Value "vat"  $container = New-VBRAmazonEC2Container -Region $AWSregion -Entity $tag |  Perform the following steps:   1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $AWSaccount variable. 2. Run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. Set the $AWSaccount variable as the Account parameter value. Set the Global value as the RegionType parameter value. Specify the Name parameter value. Save the result to the $AWSregion variable. 3. Run the [New-VBRAmazonEC2Tag](new-vbramazonec2tag.md) cmdlet. Specify the Key and the Value parameter values. Save the result to the $tag variable. 4. Run the New-VBRAmazonEC2Container cmdlet. Set the $AWSregion variable as the Region parameter value. Set the $tag variable as the Entity parameter value. Save the result to the $container variable. |

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Get-VBRAmazonEC2Region](get-vbramazonec2region.md)
* [Get-VBRAmazonEC2VM](get-vbramazonec2vm.md)


