---
title: "New-VBRFileRestoreLinuxHelperApplianceOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrfilerestorelinuxhelperapplianceoptions.html"
last_updated: "9/8/2025"
product_version: "13.0.1.1071"
---

# New-VBRFileRestoreLinuxHelperApplianceOptions

In this article

Short Description

Defines configuration settings for a temporary helper appliance.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRFileRestoreLinuxHelperApplianceOptions -Server <CHost> [-ResourcePool <CViResourcePoolItem>] [-NetworkInfo <IVBRServerNetworkInfo>] [-IP <IPAddress>] [-NetworkMask <String>] [-Gateway <IPAddress>] [-PreferredDNSServer <IPAddress>] [-AlternateDNSServer <IPAddress>] [-IPv6 <IPAddress>] [-IPv6PrefixLength <Int32>] [-IPv6Gateway <IPAddress>] [-IPv6PreferredDNSServer <IPAddress>] [-IPv6AlternateDNSServer <IPAddress>] [-FromNSS] [-EnableFTP] [-VLanId] [<CommonParameters>] |

Detailed Description

This cmdlet defines configuration settings for a temporary helper appliance.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the ESXi host on which the temporary helper appliance must be registered.  Note: If you specify a host for the Novell file system proxy appliance, make sure that it allows running VMs with 64-bit guest OSes. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByPropertyName) |
| ResourcePool | Specifies the resource pool to which the helper appliance must be placed. | Accepts the CViResourcePoolItem object. To get this object, run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. | False | Named | True (ByPropertyName) |
| NetworkInfo | Specifies the network settings for the helper appliance.  Note:   * The helper appliance must be placed in the same network where the backup server resides. * If you do not provide this parameter, the cmdlet will apply the VM network settings for the helper appliance. | Accepts the IVBRServerNetworkInfo[] object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| IP | Specifies the IPv4 address that you want to assign to the helper appliance.  Note: The helper appliance must be placed in the same network where the backup server resides. | IPAddress | False | Named | False |
| NetworkMask | For the IP parameter specified.  Specifies the network mask that you want to assign to the helper appliance.  Note: The helper appliance must be placed in the same network where the backup server resides. | String | False | Named | False |
| Gateway | Specifies the IPv4 address of the DNS server in the network where the helper appliance resides. | IPAddress | False | Named | False |
| PreferredDNSServer | Specifies the IPv4 address of the alternate DNS server in the network where the helper appliance resides. | IPAddress | False | Named | False |
| AlternateDNSServer | Specifies the IPv4 address of the alternate DNS server in the network where the helper appliance resides. | IPAddress | False | Named | False |
| IPv6 | Specifies the IPv6 address that you want to assign to the helper appliance.  Note: The helper appliance must be placed in the same network where the backup server resides. | IPAddress | False | Named | False |
| IPv6PrefixLength | For the IPv6 addresses specified.  Specifies the length of the IPv6 prefix. | Int32 | False | Named | False |
| IPv6Gateway | Specifies the IPv6 address of the default gateway in the network where the appliance resides. | IPAddress | False | Named | False |
| IPv6PreferredDNSServer | Specifies the IPv6 address of the DNS server in the network where the helper appliance resides. | IPAddress | False | Named | False |
| IPv6AlternateDNSServer | Specifies the IPv6 address of the alternate DNS server in the network where the appliance resides. | IPAddress | False | Named | False |
| FromNSS | Defines that the cmdlet will deploy a specific appliance that supports the Novell Storage Services file system.  Default: False. | SwitchParameter | False | Named | False |
| EnableFTP | Enables the FTP access to the restored file system.  If you provide this parameter, users will be able to access the helper appliance over FTP, browse the file system of the restored VM and download necessary files on their own.  Default: False. | SwitchParameter | False | Named | False |
| VLanId | Specifies an ID of an isolated network. The cmdlet will create the isolated network with the specified ID. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRFileRestoreLinuxHelperApplianceOptions object that defines settings for a temporary helper appliance.

Examples

Defining Temporary Helper Appliance for File Restore from CDP Replica

This example shows how to define settings for a temporary helper appliance for file restore from a CDP replica. The helper appliance will be deployed on the ESXi01 ESXi host in the Servers resource pool.

|  |
| --- |
| $server = Get-VBRServer -Name "ESXi01"  $resourcepool = Find-VBRViResourcePool -Server $server -Name "Servers"  $helper = New-VBRFileRestoreLinuxHelperApplianceOptions -Server $server -ResourcePool $resourcepool |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the result to the $resourcepool variable.
3. Run the New-VBRFileRestoreLinuxHelperApplianceOptions cmdlet. Set the $server variable as the Server parameter value. Set the $resourcepool variable as the ResourcePool parameter value. Save the result to the $helper variable.

Page updated 9/8/2025

Page content applies to build 13.0.1.1071
