---
title: "Start-VBRCloudTapeRestore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrcloudtaperestore.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# Start-VBRCloudTapeRestore


Short Description

Starts a restore session of the tenant data from tape.

Applies to

Product Edition: Enterprise

Requires Cloud Connect license

Syntax

This cmdlet provides parameter sets that allow you to:

* Restore to original location.

|  |
| --- |
| Start-VBRCloudTapeRestore [-BackupObject] <VBRCloudTapeBackupObject[]> -PointInTime <datetime> [-Overwrite] [-RunAsync]  [<CommonParameters>] |

* Restore to another cloud repository.

|  |
| --- |
| Start-VBRCloudTapeRestore [-BackupObject] <VBRCloudTapeBackupObject[]> -MappingTarget <VBRCloudTenantResource[]> -PointInTime <datetime> [-Overwrite] [-RunAsync]  [<CommonParameters>] |

* Export backup files to disk.

|  |
| --- |
| Start-VBRCloudTapeRestore [-BackupObject] <VBRCloudTapeBackupObject[]> -Server <CHost> -Path <string> -Credentials <CCredentials> -PointInTime <datetime> [-RunAsync]  [<CommonParameters>] |

Detailed Description

Starts a restore session of the tenant data from tape.

Run the [Stop-VBRCloudTapeRestore](stop-vbrcloudtaperestore.md) cmdlet to stop the restore session.

|  |
| --- |
| ![Start-VBRCloudTapeRestore](images/icon_important.webp) Important! |
| Consider the following:   * Veeam Backup & Replication disables the tenant until the restore operation completes. * For the restore to another cloud repository scenario you must create a new cloud tenant resource beforehand. Run the [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md) cmdlet to create the cloud tenant resource. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| BackupObject | Specifies the tenant object that you want to restore. You can restore the following tenant objects:   * Tenants * Tenants quotas * Tenants jobs | Accepts the VBRCloudTapeBackupObject[] object. To get this object, run one of the following cmdlets:   * [Get-VBRCloudTapeBackupTenant](get-vbrcloudtapebackuptenant.md) * [Get-VBRCloudTapeBackupTenantRepository](get-vbrcloudtapebackuptenantrepository.md) * [Get-VBRCloudTapeBackupTenantJob](get-vbrcloudtapebackuptenantjob.md) | True | 0 | True (ByValue) |
| Credentials | For export backup files to disk.  Specifies credentials that Veeam Backup & Replication will use to connect to a server added to Veeam Backup & Replication infrastructure. Veeam Backup & Replication will restore tenant backups to the folder on this server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| MappingTarget | For restore to another cloud repository.  Specifies the target repository. The cmdlet will restore the backup to the specified location. | Accepts the [VBRCloudTenantResource[]](vbrcloudtenantresource.md) object. Run the [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md) cmdlet to create this object. | True | Named | False |
| Path | For exporting backup files to disk.  Specifies the path to the folder.  Veeam Backup & Replication will restore the files to the folder specified in the path. | String | True | Named | False |
| PointInTime | Specifies the point in time. The cmdlet will select the restore point that is the closest to the selected point in time.  For example, if you specify Thursday, October 25, 2023 3:25:45 PM as the point in time, the cmdlet will select the closest restore point to this point in time.  Note: The date format depends on the date format of the OS where you run the script. | Accepts the DateTime object. To get this object, run the [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1) cmdlet. | True | Named | False |
| Server | For exporting backup files to disk.  Specifies a server in the Veeam Backup & Replication infrastructure. Veeam Backup & Replication will restore tenant backups to the folder on this server. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| Overwrite | For the following types of restore:   * To original location * To another cloud repository   Defines that the cmdlet will overwrite the existing backup file. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Tenant Data from Tape to Original Location [Using Variable]

|  |  |
| --- | --- |
| This example shows how to restore the tenant data from tape to original location. Veeam Backup & Replication will select the restore point that is the closest to Thursday, October 25, 2023 3:25:45 PM.  |  | | --- | | $repository = Get-VBRCloudTapeBackupTenantRepository -Name “Silver Cloud Repository”  $date = New-Object 2023, 10, 25, 15, 25, 45  Start-VBRCloudTapeRestore -BackupObject $repository -PointInTime $date |  Perform the following steps:   1. Run the [Get-VBRCloudTapeBackupTenantRepository](get-vbrcloudtapebackuptenantrepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 2. Run the New-Object cmdlet to specify the date and time for the restore point. Save the result to the $date variable. 3. Run the Start-VBRCloudTapeRestore cmdlet. Set the $repository variable as the BackupObject parameter value. Set the $date variable as the PointInTime parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Tenant Data from Tape to Another Cloud Repository [Using Variable]

|  |  |
| --- | --- |
| This example shows how to restore a tenant backup job from tape to another cloud repository. Veeam Backup & Replication will select the restore point that is the closest to Thursday, November 15, 2023 1:00:31 PM.  |  | | --- | | $backupjob = Get-VBRCloudTapeBackupTenantJob -Name "Exchange Backup Job"  $repo = Get-VBRBackupRepository -Name "NewCloudRepository"  $newtenant = New-VBRCloudTenantResource -Repository $repo -RepositoryFriendlyName "Silver Cloud Repository" -Quota 100  $date = New-Object DateTime 2023, 11, 15, 13, 00, 31  Start-VBRCloudTapeRestore -BackupObject $backupjob -MappingTarget $newtenant -PointInTime $date |  Perform the following steps:   1. Run the [Get-VBRCloudTapeBackupTenantJob](get-vbrcloudtapebackuptenantjob.md) cmdlet. Specify the Name parameter value. Save the result to the $backupjob variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet to get the target cloud repository. Specify the Name parameter value. Save the result to the $repo variable. 3. Run the [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md) cmdlet. Set the $repo variable as the Repository parameter value. Specify the RepositoryFriendlyName and Quota parameter values. Save the result to the $newtenant variable. 4. Run the New-Object cmdlet to specify the date and time for the restore point. Save the result to the $date variable. 5. Run the Start-VBRCloudTapeRestore cmdlet. Set the $backupjob variable as the BackupObject parameter value. Set the $newtenant variable as the MappingTarget parameter value. Set the $date variable as the PointInTime parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Restoring Tenant Data from Tape to Target Server [Using Variable]

|  |  |
| --- | --- |
| This example shows how to restore the selected tenant to a folder on the Fileserver target server.  Veeam Backup & Replication will select the restore point that is closest to Thursday, October 23, 2023 1:58:31 PM.  |  | | --- | | $creds = Get-VBRCredentials -Name "Fileserver"  $tenant = Get-VBRCloudTapeBackupTenant -Name "New tenant"  $targetserver = Get-VBRServer -Name "Fileserver"  $date = New-Object DateTime 2023, 11, 15, 13, 00, 31  Start-VBRCloudTapeRestore -BackupObject $tenant -Server $targetserver -Path "D:\Backups" -Credentials $creds -PointInTime $date |  Perform the following steps:   1. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $creds variable. 2. Run the [Get-VBRCloudTapeBackupTenant](get-vbrcloudtapebackuptenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable. 3. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $targetserver variable. 4. Run the New-Object cmdlet to specify the date and time for the restore point. Save the result to the $date variable. 5. Run the Start-VBRCloudTapeRestore cmdlet. Specify the following settings:  * Set the $tenant variable as the BackupObject parameter value. * Set the $targetserver variable as the Server parameter value. * Specify the Path parameter value. * Set the $creds variable as the Credentials parameter value. * Set the $date variable as the PointInTime parameter value. |

Related Commands

* [Get-VBRCloudTapeBackupTenantRepository](get-vbrcloudtapebackuptenantrepository.md)
* [Get-VBRCloudTapeBackupTenant](get-vbrcloudtapebackuptenant.md)
* [Get-VBRCloudTapeBackupTenantJob](get-vbrcloudtapebackuptenantjob.md)
* [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md)
* [Get-VBRCredentials](get-vbrcredentials.md)
* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md)


