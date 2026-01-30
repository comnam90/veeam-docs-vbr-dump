---
title: "Start-VBRvCloudQuickMigration"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrvcloudquickmigration.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Start-VBRvCloudQuickMigration


Short Description

Starts a quick migration of Cloud Director VMs.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRvCloudQuickMigration -InstantRecovery <InstantRecoveryObject> [-StorageProfile <CVcdOrgVdcStorageProfile>] [-vCloudDatastore <CVcdDatastoreRestoreInfo>] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts a quick migration of Cloud Director VMs.

|  |
| --- |
| ![Start-VBRvCloudQuickMigration](images/icon_note.webp) Note: |
| To perform a quick migration of Cloud Director VMs you must run an instant recovery of  the necessary Cloud Director VMs beforehand. Run the [Start-VBRvCloudInstantRecovery](start-vbrvcloudinstantrecovery.md) cmdlet to perform an instant recovery of  the necessary Cloud Director VMs. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstantRecovery | Specifies the Cloud Director VM that you want to migrate. | Accepts the InstantRecoveryObject type. To get this object, run the [Start-VBRvCloudInstantRecovery](start-vbrvcloudinstantrecovery.md) cmdlet. | True | Named | True (ByValue, |
| StorageProfile | Specifies the storage policy of the selected Cloud Director VM that is restored to the original location.  Note: the cmdlet will not restore the storage policy of Cloud Director VMs in case you restore them to the different location. | Accepts the CVcdOrgVdcStorageProfile object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| vCloudDatastore | Specifies the Cloud Director datastore. Veeam Backup & Replication will move the Cloud Director VM data to the selected Cloud Director datastore. | Accepts the CVcdDatastoreRestoreInfo object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Starting Quick Migration of Cloud VM

This example shows how to start quick migration of the Cloud Director VM.

|  |
| --- |
| $restorepoint = Get-VBRRestorePoint  $VM = Start-VBRvCloudInstantRecovery -RestorePoint $restorepoint[1]  Start-VBRvCloudQuickMigration -InstantRecovery $VM |

Perform the following steps:

1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable.
2. Run the [Start-VBRvCloudInstantRecovery](start-vbrvcloudinstantrecovery.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $VM variable.

The [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the second restore point in the array).

1. Run the Start-VBRvCloudQuickMigration cmdlet. Set the $VM variable as the InstantRecovery parameter value.

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Start-VBRvCloudInstantRecovery](start-vbrvcloudinstantrecovery.md)


