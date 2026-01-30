---
title: "New-VBRViReplicaReIpIPv6Rule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrvireplicareipipv6rule.html"
last_updated: "7/18/2024"
product_version: "13.0.1.1071"
---

# New-VBRViReplicaReIpIPv6Rule


Short Description

Creates a new VMware replica re-IPv6 rule.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRViReplicaReIpIPv6Rule [-SourceIp <String>] [-SourcePrefix <String>] [-TargetIp <String>] [-TargetPrefix <String>] [-TargetGateway <String>] [-PreferredDNS <String>] [-AlternateDNS <String>] [-Description <String>] [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRViReplicaReIpIPv6Rule](vbrvireplicareipipv6rule.md) object. This object contains a list of rules for different IP addressing scheme. Use this object to set re-IPv6 rules for replication jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SourceIp | Specifies the IPv6 address or the IPv6 addressing scheme of the network in which the source VM is located. You can use the asterisk character (\*) to specify a range of IP addresses.  Default: 0000:0000:0000:0000:ffff:c0a8:0a01 | String | False | Named | False |
| SourcePrefix | Specifies the prefix length of the network in which the source VM is located.  Default: 80 | String | False | Named | False |
| TargetIp | Specifies the IPv6 address of the network in which the replica VM will be located.  Default: 0000:0000:0000:0000:ffff:c078:0a01 | String | False | Named | False |
| TargetPrefix | Specifies the prefix length of the network in which the replica will be located.  Default: 64 | String | False | Named | False |
| TargetGateway | Specifies the gateway address of the network in which the replica will be located.  Default: 0000:0000:0000:0000:ffff:c0a8:0a01 | String | False | Named | False |
| PreferredDNS | Specifies the preferred DNS server address. | String | False | Named | False |
| AlternateDNS | Specifies the alternate DNS server address. | String | False | Named | False |
| Description | Specifies the description of the re-IPv6 rule. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRViReplicaReIPv6Rule](vbrvireplicareipipv6rule.md)

Examples

Creating New Re-IP Rule

This command generates a new re-IPv6 rule. Save it to the $reiprule variable for future needs.

|  |
| --- |
| $reiprule = New-VBRViReplicaReIpIPv6Rule -SourceIp "2001:0DB8:ABCD:0012:0000:0000:0000:\*" -SourcePrefix "24" -TargetIp "2001:0DB8:ABCD:0012:0000:0000:0000:\*" -TargetPrefix "24" |


