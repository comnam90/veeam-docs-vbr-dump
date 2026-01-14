---
title: "Find-VBRvCloudEntity"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/find-vbrvcloudentity.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Find-VBRvCloudEntity

In this article

Short Description

Looks for Cloud Director entities.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Look for all Cloud Director entities.

|  |
| --- |
| Find-VBRvCloudEntity [-Name <String[]>] [-Server <CHost[]>] [-Full]  [<CommonParameters>] |

* Look for vApps.

|  |
| --- |
| Find-VBRvCloudEntity [-Name <String[]>] [-Server <CHost[]>] [-VApp]  [<CommonParameters>] |

* Look for vApp templates.

|  |
| --- |
| Find-VBRvCloudEntity [-Name <String[]>] [-Server <CHost[]>] [-Template]  [<CommonParameters>] |

* Look for VM templates.

|  |
| --- |
| Find-VBRvCloudEntity [-Name <String[]>] [-Server <CHost[]>] [-VmTemplate]  [<CommonParameters>] |

* Look for VMs.

|  |
| --- |
| Find-VBRvCloudEntity [-Name <string[]>] [-Server <CHost[]>] [-Vm]  [<CommonParameters>] |

* Look for organization VDCs.

|  |
| --- |
| Find-VBRvCloudEntity [-Name <string[]>] [-Server <CHost[]>] [-OrganizationVdc]  [<CommonParameters>] |

* Look for storage profiles.

|  |
| --- |
| Find-VBRvCloudEntity [-Name <string[]>] [-Server <CHost[]>] [-StorageProfile]  [<CommonParameters>} |

* Look for datastores.

|  |
| --- |
| Find-VBRvCloudEntity [-Name <String[]>] [-Server <CHost[]>] [-Datastore]  [<CommonParameters>] |

* Look for vCenter Servers managed by Cloud Director.

|  |
| --- |
| Find-VBRvCloudEntity [-Name <string[]>] [-Server <CHost[]>] [-Vc]  [<CommonParameters>} |

* Look for Organizations.

|  |
| --- |
| Find-VBRvCloudEntity [-Name <string[]>] [-Server <CHost[]>] [-Organization]  [<CommonParameters>] |

* Look for Organization users.

|  |
| --- |
| Find-VBRvCloudEntity [-Name <string[]>] [-Server <CHost[]>] [-OrganizationUser]  [<CommonParameters>] |

Detailed Description

This cmdlet looks for Cloud Director entities. Use this cmdlet to get Cloud Director entities from the Service Provider's Veeam backup server.

To get Cloud Director entities from the Tenant Veeam Backup & Replication, use the following cmdlets:

* Run the [Get-VBRvCDCloudOrganizationvDC](get-vbrvcdcloudorganizationvdc.md) cmdlet to get the organization VDC.
* Run the [Get-VBRvCDCloudStoragePolicy](get-vbrvcdcloudstoragepolicy.md) cmdlet to get the Cloud Director storage policy.
* Run the [Get-VBRvCDCloudvApp](get-vbrvcdcloudvapp.md) cmdlet to get Cloud Director vApps.
* Run the [Get-VBRvCDCloudOrganizationUser](get-vbrvcdcloudorganizationuser.md) cmdlet to get the organization users.

|  |
| --- |
| ![Find-VBRvCloudEntity](images/icon_important.webp) Important! |
| Consider the following:   * This cmdlet works from the Service Provider side only. * The cmdlet will not return users with administrator roles. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of Cloud Director entity names. The cmdlet will return entities with these names. | String[] | False | Named | False |
| Server | Specifies the array of servers. The cmdlet will return Cloud Director entities located on these servers. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | True (ByValue, |
| Full | Defines that the cmdlet will return only Cloud Director entities. | SwitchParameter | False | Named | False |
| VApp | Defines that the cmdlet will return only vApps. | SwitchParameter | False | Named | False |
| Template | Defines that the cmdlet will return only vApp templates. | SwitchParameter | False | Named | False |
| VmTemplate | Defines that the cmdlet will return only VM templates. | SwitchParameter | False | Named | False |
| Vm | Defines that the cmdlet will return only VMs. | SwitchParameter | False | Named | False |
| OrganizationVdc | Defines that the cmdlet will return only organization VDCs. | SwitchParameter | False | Named | False |
| StorageProfile | Defines that the cmdlet will return only storage profiles. | SwitchParameter | False | Named | False |
| Datastore | Defines that the cmdlet will return only datastores. | SwitchParameter | False | Named | False |
| Vc | Defines that the cmdlet will return only vCenter Servers managed by Cloud Director. | SwitchParameter | False | Named | False |
| Organization | Defines that the cmdlet will return only Organizations. | SwitchParameter | False | Named | False |
| OrganizationUser | Defines that the cmdlet will return only Organization users.  Note: The cmdlet will not return users with administrator roles. | SwitchParameter | False | Named | False |
| EntityRef | Specifies one of the following Cloud Director entities:   * VM * vApp * OrganizationVDC * Organization   The cmdlet will return these entities. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

* CVcdSystemItem
* CVcdOrganizationItem
* CVcdOrganizationVdcItem
* CVcdVappItem
* CVcdVmItem
* CVcdOrgVdcStorageProfile
* CVcdDatastoreRestoreInfo
* CVcdVcInfo
* VBRvCloudOrganizationUser

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Cloud Entities

|  |  |
| --- | --- |
| This example shows how to look for all Cloud Director entities registered on the server.  |  | | --- | | $server = Get-VBRServer -Name "172.16.1.13"  Find-VBRvCloudEntity -Server $server -Full |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. 2. Run the Find-VBRvCloudEntity cmdlet. Set the $server variable as the Server parameter value. Provide the Full parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cloud Director Server by Name

|  |  |
| --- | --- |
| This example shows how to look for the particular Cloud Director server.  |  | | --- | | $server = Get-VBRServer -Name "172.16.1.13"  Find-VBRvCloudEntity -Server $server -Name \*SQL\* |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Find-VBRvCloudEntity cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting vApps on Specific Cloud Director Server

|  |  |
| --- | --- |
| This example shows how to get the vApps on the particular Cloud Director server.  |  | | --- | | $server = Get-VBRServer -Name "Cloud Server"  Find-VBRvCloudEntity -Server $server -VApp |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Find-VBRvCloudEntity cmdlet. Set the $server variable as the Server parameter value. Provide the VApp parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Datastore on Sprecific Cloud Director Server

|  |  |
| --- | --- |
| This example shows how to get the datastore on the particular Cloud Director server.  |  | | --- | | $server = Get-VBRServer -Name "Cloud Server"  Find-VBRvCloudEntity -Server $server -Datastore -Name "Datastore 04" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Find-VBRvCloudEntity cmdlet. Set the $server variable as the Server parameter value. Provide the Datastore parameter. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Getting All Organization DCs

|  |  |
| --- | --- |
| This command gets all Organization DCs.  |  | | --- | | Find-VBRvCloudEntity -OrganizationVdc | |

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 4/24/2024

Page content applies to build 13.0.1.1071
