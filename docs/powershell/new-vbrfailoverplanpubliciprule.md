---
title: "New-VBRFailoverPlanPublicIPRule"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrfailoverplanpubliciprule.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# New-VBRFailoverPlanPublicIPRule

In this article

Short Description

Creates a rule for mapping public IP and ports to the internal IP and ports of the cloud replica VM.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRFailoverPlanPublicIPRule -SourceIp <string> -SourcePort <int32> -TargetIp <string> -TargetPort <int32> [-Description <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a [VBRFailoverPlanPublicIPRule](vbrfailoverplanpubliciprule.md) object. This object contains a rule for mapping public IP and ports to the internal IP and ports of the cloud replica VM. Public IP address is selected from the public IP address pool. Server provider assigns the public IP address pool in tenant's hardware plan.

The object is used then in the [New-VBRCloudFailoverPlanObject](new-vbrcloudfailoverplanobject.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SourceIp | Specifies the public IP address you want to set for the replica VM. Select the public IP address from the IP address pool assigned by service provider in the hardware plan. | String | True | Named | False |
| SourcePort | Specifies the port you want to set for the replica VM. | Int32 | True | Named | False |
| TargetIp | The original internal IP address of the replica VM. | String | True | Named | False |
| TargetPort | The internal port of the replica VM.  The 22 port is reserved and cannot be used. | Int32 | True | Named | False |
| Description | The description of the rule. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRFailoverPlanPublicIPRule](vbrfailoverplanpubliciprule.md)

Examples

Creating Public IP Rule

This command defines settings of a new public IP rule.

|  |
| --- |
| New-VBRFailoverPlanPublicIPRule -SourceIp "45.0.0.2" -SourcePort 8888 -TargetIp "172.16.2.232" -TargetPort 3389 -Description "Public IP for srv03" |

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
