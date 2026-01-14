---
title: "New-VBRHvReplicaReIpIPv6Rule"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrhvreplicareipipv6rule.html"
last_updated: "7/18/2024"
product_version: "13.0.1.1071"
---

# New-VBRHvReplicaReIpIPv6Rule

In this article

Short Description

Creates a new Hyper-V replica re-IPv6 rule.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRHvReplicaReIpIPv6Rule [-SourceIp <String>] [-SourcePrefix <String>] [-TargetIp <String>] [-TargetPrefix <String>] [-TargetGateway <String>] [-PreferredDns <String>] [-AlternateDNS <String>] [-Description <String>] [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRHvReplicaReIpIPv6Rule](vbrhvreplicareipipv6rule.md) object. This object containins a list of rules for different IP addressing scheme. Use this object to set re-IPv6 rules for replication jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SourceIp | Specifies the IPv6 address or the IPv6 addressing scheme of the network in which the source VM is located. You can use the asterisk character (\*) to specify a range of IP addresses.  Default: 0000:0000:0000:0000:ffff:c0a8:0a01 | String | False | Named | False |
| SourcePrefix | Specifies the prefix length of the network in which the source VM is located.  Default: 80 | String | False | Named | False |
| TargetIp | Specifies the IPv6 address of the network in which the replica VM will be located.  Default: 0000:0000:0000:0000:ffff:c078:0a01 | String | False | Named | False |
| TargetPrefix | Specifies the prefix length of the network in which the replica will be located.  Default: 64 | String | False | Named | False |
| TargetGateway | Specifies the gateway address of the network in which the replica will be located.  Default: 0000:0000:0000:0000:ffff:c0a8:0a01 | String | False | Named | False |
| PreferredDns | Specifies the preferred DNS server address. | String | False | Named | False |
| AlternateDNS | Specifies the alternate DNS server address. | String | False | Named | False |
| Description | Specifies the description of the re-IPv6 rule. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRHvReplicaReIpIPv6Rule](vbrhvreplicareipipv6rule.md)

Examples

Creating New Re-IP Rule

This command generates a new re-IPv6 rule. Save it to the $reiprule variable for future needs.

|  |
| --- |
| $reiprule = New-VBRHvReplicaReIpIPv6Rule -SourceIp "2001:0DB8:ABCD:0012:0000:0000:0000:\*" -SourcePrefix "24" -TargetIp "2001:0DB8:ABCD:0012:0000:0000:0000:\*" -TargetPrefix "24" |

Page updated 7/18/2024

Page content applies to build 13.0.1.1071
