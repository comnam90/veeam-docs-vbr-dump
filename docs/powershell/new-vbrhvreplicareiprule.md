---
title: "New-VBRHvReplicaReIpRule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrhvreplicareiprule.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# New-VBRHvReplicaReIpRule


Short Description

Creates a new Hyper-V replica re-IPv4 rule.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRHvReplicaReIpRule [-SourceIp <String>] [-SourceMask <String>] [-TargetIp <String>] [-TargetMask <String>] [-TargetGateway <String>] [-DNS <String[]>] [-WINS <String[]>] [-Description <String>] [-PipelineVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRHvReplicaReIpRule](vbrhvreplicareiprule.md) object. This object contains a list of rules for different IP addressing scheme. Use this object to set re-IP rules for replication jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SourceIp | Specifies the IPv4 address or the IPv4 addressing scheme of the network in which the source VM is located. You can use the asterisk character (\*) to specify a range of IP addresses.  Default: 172.24.16.\*. | String | False | Named | False |
| SourceMask | Specifies the mask of the network in which the source VM is located. You can use the asterisk character (\*) to specify a range of IP addresses.  Default: 255.255.240.0. | String | False | Named | False |
| TargetIp | Specifies the IPv4 address or the IPv4 addressing scheme of the network in which the replica VM will be located. You can use the asterisk character (\*) to specify a range of IP addresses.  Default: 172.24.17.\*. | String | False | Named | False |
| TargetMask | Specifies the mask of the network in which the replica VM will be located. You can use the asterisk character (\*) to specify a range of IP addresses.  Default: 255.255.240.0. | String | False | Named | False |
| TargetGateway | Specifies the gateway address of the network in which the replica VM will be located.  Default: 127.24.17.1. | String | False | Named | False |
| DNS | Specifies the DNS server address. | String[] | False | Named | False |
| WINS | Specifies the WINS server address. | String[] | False | Named | False |
| Description | Specifies the description of the re-IP rule. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRHvReplicaReIpRule](vbrhvreplicareiprule.md)

Examples

Creating New Re-IP Rule

This command generates a new re-IP rule. Save it to the $reiprule variable for future needs.

|  |
| --- |
| $reiprule = New-VBRHvReplicaReIpRule -SourceIp 172.16.\*.\* -SourceMask 255.255.0.0 -TargetIp 172.17.\*.\* -TargetMask 255.255.0.0 -TargetGateway 172.17.0.1 |


