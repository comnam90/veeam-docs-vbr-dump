---
title: "Set-VBRvCloudOrganizationJobMapping"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvcloudorganizationjobmapping.html"
last_updated: "9/12/2025"
product_version: "13.0.1.1071"
---

# Set-VBRvCloudOrganizationJobMapping

In this article

Short Description

Adds Cloud Director backup jobs, replication jobs, CDP policies, backups and replicas to the self-service portal of a Cloud Director Organization or removes them from it.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRvCloudOrganizationJobMapping -Action <VBRMapOrganizationAction> {Map | Unmap} -Job <VBRJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet allows Cloud Director service providers to map Veeam Backup & Replication backup jobs, replication jobs, and CDP policies created to the organization configurations of their tenants. After you map the jobs and policies, tenants can manage them and perform recovery operations independently in Veeam Self-Service Backup Portal. For more information on the mapping procedure, see [Veeam Backup Enterprise Manager Guide](https://helpcenter.veeam.com/docs/backup/em/em_working_with_vcd_vms.html?ver=120).

Cloud Director providers can use this cmdlet to make Cloud Director backup jobs, replication jobs and CDP policies visible for their customers in the Veeam Self-Service Backup Portal. As a result, the self-service portal users can manage these jobs and policies, or perform restore operations through Veeam Self-Service Backup Portal of Veeam Backup Enterprise Manager. The users get access to:

* Backups and replicas created by these jobs and policies
* Guest OS credentials configured in these jobs and policies

This cmdlet does not add imported backups.

Users of the self-service portal will not see the backup job sessions run previously by the Cloud Director providers.

|  |
| --- |
| Important |
| You cannot map Veeam Backup & Replication backup jobs, replication jobs, and CDP policies if any objects in this job have been deleted from the source VMware Cloud Director infrastructure.  To successfully map the necessary job that contains deleted objects, perform the following steps:   1. Remove all deleted objects from the job. 2. If all objects in the job were deleted, add to the job existing objects from the same VMware Cloud Director organization. 3. Run the Set-VBRvCloudOrganizationJobMapping cmdlet and retry the mapping operation again. |

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Action | Specifies the action:   * Map: Adds jobs and policies to the Cloud Director Organization. * Unmap: Removes jobs and policies from the Cloud Director Organization. | VBRMapOrganizationAction | True | Named | False |
| Job | Specifies the array of jobs and policies. The cmdlet will add these jobs and policies to the self-service portal or remove them from it.  Note: If you map multiple jobs or policies simultaneously, the execution time of the cmdlet can significantly increase with the number of jobs and policies. | Accepts the VBRJob[] object. To get this object, run the following cmdlets:   * [Get-VBRJob](get-vbrjob.md) to get backup and replication jobs. * [Get-VBRCDPPolicy](get-vbrcdppolicy.md) to get CDP policies. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Backup Jobs and Backups to Self-Service Portal

|  |  |
| --- | --- |
| This example shows how to add backup jobs and backups to Veeam Self-Service Backup Portal.  |  | | --- | | $job = Get-VBRJob -Name "Backup Job 1", "Backup Job 2"  Set-VBRvCloudOrganizationJobMapping -Action Map -Job $job |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Set-VBRvCloudOrganizationJobMapping cmdlet. Set the Map option for the Action parameter. Set the $job variable as the Job parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Backup Jobs and Backups from Self-Service Portal

|  |  |
| --- | --- |
| This example shows how to remove backup jobs and backups from Veeam Self-Service Backup Portal.  |  | | --- | | $job = Get-VBRJob -Name "Backup Job 1", "Backup Job 2"  Set-VBRvCloudOrganizationJobMapping -Action Unmap -Job $job |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Set-VBRvCloudOrganizationJobMapping cmdlet. Set the Unmap option for the Action parameter. Set the $job variable as the Job parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Adding Replication Job and Replicas to Self-Service Portal

|  |  |
| --- | --- |
| This example shows how to add a replication job and replicas to the Veeam Self-Service Backup Portal.  |  | | --- | | $job = Get-VBRJob -Name "Cloud Director Replication"  Set-VBRvCloudOrganizationJobMapping -Action Map -Job $job |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Set-VBRvCloudOrganizationJobMapping cmdlet. Set the Map option for the Action parameter. Set the $job variable as the Job parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Adding CDP Replication Policy and Replicas to Self-Service Portal

|  |  |
| --- | --- |
| This example shows how to add a CDP policy and replicas to the Veeam Self-Service Backup Portal.  |  | | --- | | $job = Get-VBRCDPPolicy -Name "Cloud Director CDP Replication"  Set-VBRvCloudOrganizationJobMapping -Action Map -Job $job |  Perform the following steps:   1. Run the [Get-VBRCDPPolicy](get-vbrcdppolicy.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Set-VBRvCloudOrganizationJobMapping cmdlet. Set the Map option for the Action parameter. Set the $job variable as the Job parameter value. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRvCDReplicaJob](get-vbrvcdreplicajob.md)
* [Get-VBRCDPPolicy](get-vbrcdppolicy.md)

Page updated 9/12/2025

Page content applies to build 13.0.1.1071
