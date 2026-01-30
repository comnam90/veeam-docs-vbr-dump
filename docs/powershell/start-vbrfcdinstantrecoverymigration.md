---
title: "Start-VBRFCDInstantRecoveryMigration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrfcdinstantrecoverymigration.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# Start-VBRFCDInstantRecoveryMigration


Short Description

Starts Quick Migration of FCDs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRFCDInstantRecoveryMigration -Session <VBRFCDInstantRecoverySession> -TargetDatastore <VBRViDatastore> [-StoragePolicy <VBRViStoragePolicy>] [-MountedDiskNames <string[]>] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts Quick Migration of FCDs.

|  |
| --- |
| Important |
| Only the vMotion Quick Migration method is supported. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the Instant FCD recovery session. The cmdlet will start Quick Migration of FCDs that are restored using this session.  Note: The cmdlet will dismount the session after the virtual disks are migrated to the target datastore. | Accepts the VBRFCDInstantRecoverySession object. To create this object, run the [Get-VBRFCDInstantRecoverySession](get-vbrfcdinstantrecoverysession.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| TargetDatastore | Specifies a target datastore to which you want to mirgate FCDs.  Note: The datastore must be located in the same vCenter, where a cluster to to which Veeam Backup & Replication will register FCDs, is located. | Accepts the VBRViDatastore object. To create this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | True | 1 | False |
| StoragePolicy | Specifies a VM storage policy. Veeam Backup & Replication will apply this storage policy for FCDs and for a datastore that keeps redo logs for the restored FCDs.  Note: The encrypted VM storage policy is not applied for FCD disks. However, you can apply this policy for a datastore that keeps redo logs for the restored FCDs. | Accepts the VBRViStoragePolicy object. To create this object, run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md)  cmdlet. | False | Named | False |
| MountedDiskNames | Specifies an array of FCDs names. The cmdlet will migrate these FCDs. | String[] | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CBackupSession object that contains setting of the Quick Migration session of FCDs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Quick Migration of all FCDs

|  |  |
| --- | --- |
| This example shows how to starts Quick Migration of all FCDs. The cmdlet will perform migration with the following settings:   * The cmdlet will mirgate FCDs that have been recovered within the 49664A5F-9C55-4A1F-8E6A-1CD5705A684B FCD recovery session. * The cmdlet will migrate FCDS to the VeeamDatastore target datastore.   |  | | --- | | $fcdInstantRecovery = Get-VBRFCDInstantRecoverySession -Id "49664A5F-9C55-4A1F-8E6A-1CD5705A684B"  $server = Get-VBRServer -Name "tech.local"  $datastore = Find-VBRViDatastore -Server $server -Name "VeeamDatastore"  Start-VBRFCDInstantRecoveryMigration -Session $fcdInstantRecovery -TargetDatastore $datastore |  Perform the following steps:   1. Run the [Get-VBRFCDInstantRecoverySession](get-vbrfcdinstantrecoverysession.md) cmdlet. Specify the Id parameter value. Save the result to the $fcdInstantRecovery variable.  1. Get the datastore:  1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Specify the Server and Name parameter values. Save the result to the $datastore variable.  1. Run the Start-VBRFCDInstantRecoveryMigration cmdlet. Set the $fcdInstantRecovery varialbe as the Session parameter value. Set the $datastore varialbe as the TargetDatastore parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting Quick Migration of Specific FCDs

|  |  |
| --- | --- |
| This example shows how to starts Quick Migration of the disk1 and disk2 FCDs. The cmdlet will perform migration with the following settings:   * The cmdlet will mirgate FCDs that have been recovered within the 49664A5F-9C55-4A1F-8E6A-1CD5705A684B FCD recovery session. * The cmdlet will migrate FCDS to the VeeamDatastore target datastore.   |  | | --- | | $fcdInstantRecovery = Get-VBRFCDInstantRecoverySession -Id "49664A5F-9C55-4A1F-8E6A-1CD5705A684B"  $server = Get-VBRServer -Name "tech.local"  $datastore = Find-VBRViDatastore -Server $server -Name "VeeamDatastore"  Start-VBRFCDInstantRecoveryMigration -Session $fcdInstantRecovery -TargetDatastore $datastore -MountedDiskNames ("disk1", "disk2") |  Perform the following steps:   1. Run the [Get-VBRFCDInstantRecoverySession](get-vbrfcdinstantrecoverysession.md) cmdlet. Specify the Id parameter value. Save the result to the $fcdInstantRecovery variable.  1. Get the datastore:  1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Specify the Server and Name parameter values. Save the result to the $datastore variable.  1. Run the Start-VBRFCDInstantRecoveryMigration cmdlet. Specify the following settings:  * Set the $fcdInstantRecovery varialbe as the Session parameter value. * Set the $datastore varialbe as the TargetDatastore parameter value. * Specify the MountedDiskNames parameter values. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Starting Quick Migration of all FCDs and Applying Specific Storage Policy

|  |  |
| --- | --- |
| This example shows how to starts Quick Migration for all FCDs and apply the Virtual SAN Default storage policy to these FCDs. The cmdlet will perform migration with the following settings:   * The cmdlet will mirgate FCDs that have been recovered within the 49664A5F-9C55-4A1F-8E6A-1CD5705A684B FCD recovery session. * The cmdlet will migrate FCDS to the VeeamDatastore target datastore.   |  | | --- | | $fcdInstantRecovery = Get-VBRFCDInstantRecoverySession -Id "49664A5F-9C55-4A1F-8E6A-1CD5705A684B"  $server = Get-VBRServer -Name "tech.local"  $datastore = Find-VBRViDatastore -Server $server -Name "VeeamDatastore"  $storagePolicy = Find-VBRViStoragePolicy -Server $server -Datastore $datastore -Name "Virtual SAN Default"  Start-VBRFCDInstantRecoveryMigration -Session $fcdInstantRecovery -TargetDatastore $datastore -StoragePolicy $storagePolicy |  Perform the following steps:   1. Run the [Get-VBRFCDInstantRecoverySession](get-vbrfcdinstantrecoverysession.md) cmdlet. Specify the Id parameter value. Save the result to the $fcdInstantRecovery variable.  1. Get the datastore:  1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.  1. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Specify the Server and Name parameter values. Save the result to the $datastore variable.  1. Run the [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md) cmdlet. Specify the Server, Datastore and Name parameter values. Save the result to the $storagePolicy variable. 2. Run the Start-VBRFCDInstantRecoveryMigration cmdlet. Specify the following settings:  * Set the $fcdInstantRecovery varialbe as the Session parameter value. * Set the $datastore varialbe as the TargetDatastore parameter value. * Specify the MountedDiskNames parameter values. |

Related Commands

* [Get-VBRFCDInstantRecoverySession](get-vbrfcdinstantrecoverysession.md)
* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)
* [Find-VBRViStoragePolicy](find-vbrvistoragepolicy.md)


