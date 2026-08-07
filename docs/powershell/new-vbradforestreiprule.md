---
title: "New-VBRADForestReIpRule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbradforestreiprule.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# New-VBRADForestReIpRule


Short Description

Creates a re-IP rule for a Microsoft Active Directory forest restore.

Applies to

Platform: VMware, Hyper-V

Product Edition: Veeam Universal License

Syntax

|  |
| --- |
| New-VBRADForestReIpRule [-VlanTag <Int32>] [-SourceIp <String>] [-SourceMask <String>] [-TargetIp <String>] [-TargetMask <String>] -TargetGateway <String> [-DNS <String[]>] [-WINS <String[]>] [-Description <String>] [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRADForestReIpRule](vbradforestreiprule.md) object. This object contains settings for re-assigning IP addresses to domain controller VMs during a Microsoft Active Directory forest restore. Use re-IP rules when the domain controllers must be restored to a network with a different IP addressing scheme. Use this object with the [Start-VBRADForestRestore](start-vbradforestrestore.md) cmdlet.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| TargetGateway | Specifies the default gateway address of the network to which the domain controller VM will be restored. | String | True | Named | False |
| SourceIp | Specifies the IPv4 address or the IPv4 addressing scheme of the network in which the source domain controller VM is located. You can use the asterisk character (\*) to specify a range of IP addresses.  Default: 172.24.16.\*. | String | False | Named | False |
| SourceMask | Specifies the subnet mask of the network in which the source domain controller VM is located. You can use the asterisk character (\*) to specify a range of addresses.  Default: 255.255.240.0. | String | False | Named | False |
| TargetIp | Specifies the IPv4 address or the IPv4 addressing scheme of the network to which the domain controller VM will be restored. You can use the asterisk character (\*) to specify a range of IP addresses.  Default: 172.24.17.\*. | String | False | Named | False |
| TargetMask | Specifies the subnet mask of the network to which the domain controller VM will be restored. You can use the asterisk character (\*) to specify a range of addresses.  Default: 255.255.240.0. | String | False | Named | False |
| DNS | Specifies the DNS server addresses to assign to the restored domain controller VM. | String[] | False | Named | False |
| WINS | Specifies the WINS server addresses to assign to the restored domain controller VM. | String[] | False | Named | False |
| VlanTag | Specifies the VLAN ID of the network to which the domain controller VM will be restored. Permitted values: 1 to 4094.  Note: This parameter applies only when you restore domain controllers to a Microsoft Hyper-V host. For VMware vSphere, the VLAN is defined by the target network. | Int32 | False | Named | False |
| Description | Specifies the description of the re-IP rule. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRADForestReIpRule](vbradforestreiprule.md) object that contains the re-IP rule settings for Microsoft Active Directory forest restore.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Re-IP Rule

|  |  |
| --- | --- |
| This command creates a re-IP rule with source and target IP addressing schemes and a target gateway. Save it to the $reIpRule variable to use it when you run the [Start-VBRADForestRestore](start-vbradforestrestore.md) cmdlet.  |  | | --- | | $reIpRule = New-VBRADForestReIpRule -SourceIp 172.16.\*.\* -SourceMask 255.255.0.0 -TargetIp 172.17.\*.\* -TargetMask 255.255.0.0 -TargetGateway 172.17.0.1 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Re-IP Rule with DNS and WINS

|  |  |
| --- | --- |
| This command creates a re-IP rule that also reassigns DNS and WINS server addresses. Save it to the $reIpRule variable to use it when you run the [Start-VBRADForestRestore](start-vbradforestrestore.md) cmdlet.  |  | | --- | | $reIpRule = New-VBRADForestReIpRule -SourceIp 172.16.\*.\* -SourceMask 255.255.0.0 -TargetIp 172.17.\*.\* -TargetMask 255.255.0.0 -TargetGateway 172.17.0.1 -DNS "172.17.0.2","172.17.0.3" -WINS "172.17.0.4" -Description "Production to DR network" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Creating Re-IP Rule with VLAN ID

|  |  |
| --- | --- |
| This command creates a re-IP rule that assigns VLAN ID 120 to the restored domain controller VM on the target network. Save it to the $reIpRule variable to use it when you run the [Start-VBRADForestRestore](start-vbradforestrestore.md) cmdlet.  |  | | --- | | $reIpRule = New-VBRADForestReIpRule -SourceIp 172.16.\*.\* -SourceMask 255.255.0.0 -TargetIp 172.17.\*.\* -TargetMask 255.255.0.0 -TargetGateway 172.17.0.1 -VlanTag 120 | |

Related Commands

[Start-VBRADForestRestore](start-vbradforestrestore.md)

Page updated 2026-07-28

