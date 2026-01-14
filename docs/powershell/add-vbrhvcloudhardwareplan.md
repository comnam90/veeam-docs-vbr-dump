---
title: "Add-VBRHvCloudHardwarePlan"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrhvcloudhardwareplan.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRHvCloudHardwarePlan

In this article

Short Description

Creates Hyper-V hardware plans.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a VCP license.

Syntax

|  |
| --- |
| Add-VBRHvCloudHardwarePlan -Name <string> -Server <CHost> -Datastore <VBRHvCloudHardwarePlanDatastore[]> [-Description <string>] [-CPU <int32>] [-Memory <int32>] [-UnlimitedCPU] [-UnlimitedMemory] [-NumberOfNetWithInternet <int32>] [-NumberOfNetWithoutInternet <int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new hardware plan for Hyper-V environments.

The hardware plan allocates the following resources to a tenant:

* Cloud host. When creating replicas, the tenant will use this host as target host to register the replicated VMs.
* Quota of the cloud host CPU and memory.
* [Pre-configure] Networks to which the tenant will connect the cloud replicas. Run the [New-VBRCloudVLANConfiguration](new-vbrcloudvlanconfiguration.md) cmdlet to pre-configure the pool of VLANs.
* [Pre-configure] Cloud storage: a quota of datastores allocated to tenants. Run the [New-VBRHvCloudHWPlanDatastore](new-vbrhvcloudhwplandatastore.md) cmdlet to create the cloud storage.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the hardware plan. | String | True | Named | False |
| Description | Specifies the description of the hardware plan. | String | False | Named | False |
| Server | Specifies the Hyper-V host. The resources of this host (CPU and memory quotas) will be allocated to the tenant by the hardware plan. | Accepts the CHost object or string (name of server). To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| CPU | Specifies the quota of CPU resources you want to allocate to the tenant under this hardware plan (MHz). | Int32 | False | Named | False |
| Memory | Specifies the quota of CPU memory you want to allocate to the tenant under this hardware plan (Gb). | Int32 | False | Named | False |
| UnlimitedCPU | Defines that the quota of CPU resources is unlimited.  If you provide this parameter, the tenant will be able to use all CPU resources of the host. | SwitchParameter | False | Named | False |
| UnlimitedMemory | Defines that the quota of CPU memory is unlimited.  If you provide this parameter, the tenant will be able to use all memory resources of the host. | SwitchParameter | False | Named | False |
| NumberOfNetWithInternet | Specifies the number of networks with access to the Internet that you want to allocate to the tenant under this hardware plan. | Int32 | False | Named | False |
| NumberOfNetWithoutInternet | Specifies the number of networks without access to the Internet that you want to allocate to the tenant under this hardware plan. | Int32 | False | Named | False |
| Datastore | Specifies the array of cloud storage objects. The hardware plan will use these objects to allocate storage space to the tenant under this hardware plan. | Accepts the [VBRHvCloudHardwarePlanDatastore[]](vbrhvcloudhardwareplandatastore.md) object. To get this object, run the [New-VBRHvCloudHWPlanDatastore](new-vbrhvcloudhwplandatastore.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRHvCloudHardwarePlan](vbrhvcloudhardwareplan.md)

Examples

Creating Hyper-V Hardware Plan

This example shows how to create a hardware plan with the following settings:

* CPU quota: 4000 MHz
* Memory quota: 2000 Gb
* Cloud storage: Cloud Replicas
* Networks without access to the Internet: 1

|  |
| --- |
| $server = Get-VBRServer -Type HvServer -Name "Hyper-VHost"  $switches = Get-VBRHvServerNetworkInfo -Server $server  New-VBRCloudVLANConfiguration –Server $server -HvNetworkInfo $switches[0] –FirstVLANWithInternet 1 –LastVLANWithInternet 5 –FirstVLANWithoutInternet 6 –LastVLANWithoutInternet 10  $cloudreplicas = New-VBRHvCloudHWPlanDatastore -DatastorePath "D:\Replicas" -FriendlyName "Cloud Replicas" -Quota 500  $server = Get-VBRServer -Type HvServer -Name "Hyper-V Host"  Add-VBRHvCloudHardwarePlan -Name "Hyper-V Silver" -Description "Hyper-V Hardware Plan" -Server $server -Datastore $cloudreplicas -CPU 4000 -Memory 2000 -NumberOfNetWithoutInternet 1 |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Set the HvServer option for the Type parameter. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $switches variable.
3. Run the [New-VBRCloudVLANConfiguration](new-vbrcloudvlanconfiguration.md) cmdlet. Set the $server variable as the Server parameter value. Set the $switches variable as the HvNetworkInfo parameter value. Specify the FirstVLANWithInternet, LastVLANWithInternet, FirstVLANWithoutInternet, LastVLANWithoutInternet parameter values.
4. Run the [New-VBRHvCloudHWPlanDatastore](new-vbrhvcloudhwplandatastore.md) cmdlet. Specify the DatastorePath parameter value. Specify the FriendlyName and the Quota parameter values. Save the storage to the $cloudreplicas variable.
5. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Set the HvServer option for the Type parameter. Specify the Name parameter value. Save the result to the $server variable.
6. Run the Add-VBRHvCloudHardwarePlan cmdlet. Specify the following settings:

* Specify the Name and the Description parameter values.
* Set the $server variable as the Server parameter value.
* Set the $cloudreplicas variable as the Datastore parameter value.
* Specify the CPU and the Memory parameter values.
* Specify the NumberOfNetWithoutInternet parameter value.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [New-VBRHvCloudHWPlanDatastore](new-vbrhvcloudhwplandatastore.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
