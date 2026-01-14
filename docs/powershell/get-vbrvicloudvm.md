---
title: "Get-VBRViCloudVM"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvicloudvm.html"
last_updated: "4/29/2024"
product_version: "13.0.1.1071"
---

# Get-VBRViCloudVM

In this article

Short Description

Returns VMs available in cloud hosts allocated by cloud resources.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Return all VMs available in cloud hosts allocated by cloud resources.

|  |
| --- |
| Get-VBRViCloudVM -Server <VBRCloudServer>  [<CommonParameters>] |

* Return VMs available in cloud hosts using a specific VM name.

|  |
| --- |
| Get-VBRViCloudVM -Server <VBRCloudServer> -Name <String[]>  [<CommonParameters>] |

* Return VMs available in cloud hosts using a specific VM ID.

|  |
| --- |
| Get-VBRViCloudVM -Server <VBRCloudServer> -Id <String[]>  [<CommonParameters>] |

Detailed Description

Returns VMs available in cloud hosts that are allocated to you by your cloud resources.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies cloud hosts. The cmdlet will return VMs available in these hosts. | Accepts the [VBRCloudServer](vbrcloudserver.md) object. To create this object, run the [Get-VBRCloudServer](get-vbrcloudserver.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Name | Specifies an array of VM names. The cmdlet will return VMs with these names. | String[] | True | Named | False |
| Id | Specifies an array of IDs for VMs. The cmdlet will return VMs with these IDs. | String[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRViCloudVM object that contains VMs available in cloud hosts that are allocated to you by your cloud resources.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all VMs Available in Cloud Host

|  |  |
| --- | --- |
| This example shows how to get all VMs available in the cloud host.  |  | | --- | | $cloudserver = Get-VBRCloudServer  Get-VBRViCloudVM -Server $cloudserver |  Perform the following steps:   1. Run the [Get-VBRCloudServer](get-vbrcloudserver.md) cmdlet. Save the result to the $cloudserver variable. 2. Run the Get-VBRViCloudVM cmdlet. Set the $cloudserver variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting VMs Available in Cloud Host by Names

|  |  |
| --- | --- |
| This example shows how to get the srv50, srv59, srv45 VMs available in cloud hosts.  |  | | --- | | $cloudserver = Get-VBRCloudServer  Get-VBRViCloudVM -Server $cloudserver -Name "srv50", "srv59", "srv45" |  Perform the following steps:   1. Run the [Get-VBRCloudServer](get-vbrcloudserver.md) cmdlet. Save the result to the $cloudserver variable.  1. Run the Get-VBRViCloudVM cmdlet. Set the $cloudserver variable as the Server parameter value. Specify the Name parameter values. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting VMs Available in Cloud Host by ID

|  |  |
| --- | --- |
| This example shows how to get the "4ddb76ea-c11f-4c93-9147-06facf7c2186","d3cff5ea-58f0-4fbd-8f58-87896e755dc5 VMs available in cloud hosts.  |  | | --- | | $cloudserver = Get-VBRCloudServer  Get-VBRViCloudVM -Server $cloudserver -Id "4ddb76ea-c11f-4c93-9147-06facf7c2186", "d3cff5ea-58f0-4fbd-8f58-87896e755dc5" |  Perform the following steps:   1. Run the [Get-VBRCloudServer](get-vbrcloudserver.md) cmdlet. Save the result to the $cloudserver variable.  1. Run the Get-VBRViCloudVM cmdlet. Set the $cloudserver variable as the Server parameter value. Specify the Id parameter values. |

Related Commands

[Get-VBRCloudServer](get-vbrcloudserver.md)

Page updated 4/29/2024

Page content applies to build 13.0.1.1071
