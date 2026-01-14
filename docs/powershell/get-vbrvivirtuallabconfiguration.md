---
title: "Get-VBRViVirtualLabConfiguration"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvivirtuallabconfiguration.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Get-VBRViVirtualLabConfiguration

In this article

Short Description

Returns virtual labs and their settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRViVirtualLabConfiguration [-Id <guid[]>] [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the VBRViVirtualLabConfiguration object that contains an array of virtual labs and all their settings. You can use this object to modify settings of virtual labs.

Run the [Set-VBRViVirtualLab](set-vbrvivirtuallab.md) cmdlet to modify settings of virtual labs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of IDs for a virtual lab. The cmdlet will return an array of virtual labs with the specifies ID. | Guid[] | False | Named | False |
| Name | Specifies an array of names for a virtual lab. The cmdlet will return an array of virtual labs with the specifies names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRViVirtualLabConfiguration object that an array of virtual labs and all their settings

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Virtual Labs

|  |  |
| --- | --- |
| This command returns all virtual labs that are added to the Veeam Backup & Replication infrastructure. The cmdlet output will contain settings of the virtual labs.  |  | | --- | | Get-VBRViVirtualLabConfiguration  DesignatedResourcePoolName : Exchange Virtual Lab  DesignatedVMFolderName     : Exchange Virtual Lab  CacheDatastore             : esx09-das05  ProxyAppliance             : Exchange Virtual Lab  ProxyApplianceEnabled      : True  NetworkMapping             : {Exchange Virtual Lab VM Network}  NetworkOptions             : {Veeam.Backup.PowerShell.Infos.VBRViVirtualLabNetworkOptions  RoutingBetweenvNicsEnabled : False  IsMultiHost                : False  DVS                        :  IpMappingRule              : {}  StaticIPMappingEnabled     : False  Type                       : Advanced  IdOnHost                   : 6b2686ae-9e1b-4c6e-b6fb-842d7155a9ec  Server                     : Veeam.Backup.Core.Common.CHost  Platform                   : VMWare  Id                         : 8762b1ea-3422-4f84-8472-e596d7c8265e  Name                       : Exchange Virtual Lab  Description                : Created by Powershell at 2/20/2020 5:56 AM.    DesignatedResourcePoolName : SQL Virtual Lab  DesignatedVMFolderName     : SQL Virtual Lab  CacheDatastore             : esx09-das05  ProxyAppliance             : SQL Virtual Lab  ProxyApplianceEnabled      : True  NetworkMapping             : {SQL Virtual Lab VM Network}  NetworkOptions             : {Veeam.Backup.PowerShell.Infos.VBRViVirtualLabNetworkOptions  RoutingBetweenvNicsEnabled : False  IsMultiHost                : False  DVS                        :  IpMappingRule              : {}  StaticIPMappingEnabled     : False  Type                       : Advanced  IdOnHost                   : 43d2457a-ddee-424d-9fd3-42e021a77309  Server                     : Veeam.Backup.Core.Common.CHost  Platform                   : VMWare  Id                         : 8762b1ea-3422-4f84-8472-e596d7c8265e  Name                       : SQL Virtual Lab  Description                : Created by Powershell at 2/20/2020 5:56 AM. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Virtual Lab by ID

|  |  |
| --- | --- |
| This command returns the 6b2686ae-9e1b-4c6e-b6fb-842d7155a9ec virtual lab. The cmdlet output will contain settings of the virtual lab.  |  | | --- | | Get-VBRViVirtualLabConfiguration -Id "6b2686ae-9e1b-4c6e-b6fb-842d7155a9ec"  DesignatedResourcePoolName : Exchange Virtual Lab  DesignatedVMFolderName     : Exchange Virtual Lab  CacheDatastore             : esx09-das05  ProxyAppliance             : Exchange Virtual Lab  ProxyApplianceEnabled      : True  NetworkMapping             : {Exchange Virtual Lab VM Network}  NetworkOptions             : {Veeam.Backup.PowerShell.Infos.VBRViVirtualLabNetworkOptions  RoutingBetweenvNicsEnabled : False  IsMultiHost                : False  DVS                        :  IpMappingRule              : {}  StaticIPMappingEnabled     : False  Type                       : Advanced  IdOnHost                   : 6b2686ae-9e1b-4c6e-b6fb-842d7155a9ec  Server                     : Veeam.Backup.Core.Common.CHost  Platform                   : VMWare  Id                         : 8762b1ea-3422-4f84-8472-e596d7c8265e  Name                       : Exchange Virtual Lab  Description                : Created by Powershell at 2/20/2020 5:56 AM. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Virtual Lab by Name

|  |  |
| --- | --- |
| This command returns the SQL Virtual Lab virtual lab. The cmdlet output will contain settings of the virtual lab.  |  | | --- | | Get-VBRViVirtualLabConfiguration -Name "SQL Virtual Lab"  DesignatedResourcePoolName : SQL Virtual Lab  DesignatedVMFolderName     : SQL Virtual Lab  CacheDatastore             : esx09-das05  ProxyAppliance             : SQL Virtual Lab  ProxyApplianceEnabled      : True  NetworkMapping             : {SQL Virtual Lab VM Network}  NetworkOptions             : {Veeam.Backup.PowerShell.Infos.VBRViVirtualLabNetworkOptions  RoutingBetweenvNicsEnabled : False  IsMultiHost                : False  DVS                        :  IpMappingRule              : {}  StaticIPMappingEnabled     : False  Type                       : Advanced  IdOnHost                   : 43d2457a-ddee-424d-9fd3-42e021a77309  Server                     : Veeam.Backup.Core.Common.CHost  Platform                   : VMWare  Id                         : 8762b1ea-3422-4f84-8472-e596d7c8265e  Name                       : SQL Virtual Lab  Description                : Created by Powershell at 2/20/2020 5:56 AM. | |

Page updated 3/1/2024

Page content applies to build 13.0.1.1071
