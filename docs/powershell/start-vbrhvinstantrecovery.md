---
title: "Start-VBRHvInstantRecovery"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrhvinstantrecovery.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Start-VBRHvInstantRecovery


Short Description

Starts Hyper-V Instant Recovery.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRHvInstantRecovery -RestorePoint <COib> [-Credentials <CCredentials>] [-DisableDiskAllocation] [-DiskMappingRule <VBRHvVirtualDeviceMappingRule>] [-EnableAntivirusScan] [-EnableEntireVolumeScan] [-EnableYARAScan] [-Force] [-HelperAppliance <VBRHvInstantRecoveryHelperAppliance>] [-NetworkMapping <VBRHvInstantRecoveryNetworkMappingRule[]>] [-NICsEnabled <bool>] [-Path <string>] [-PowerUp <bool>] [-PreserveMACs <bool>] [-PreserveVmID <bool>] [-Reason <string>] [-RegisterAsClusterResource] [-Server <CHost>] [-VirusDetectionAction {DisableNetwork | AbortRecovery}] [-VMName <string>] [-YARAScanRule <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet starts Instant Recovery to Microsoft Hyper-V. The Instant Recovery for Microsoft Hyper-V process creates a copy of a workload in a target location reading data from the directly from a compressed and deduplicated backup file. For the list of workload types that you can restore, see in the [Instant Recovery to Microsoft Hyper-V](https://helpcenter.veeam.com/docs/vbr/userguide/instant_recovery_to_hv.html?ver=13) section in the Veeam Backup & Replication User Guide.

With this cmdlet, you can perform the following recover scenarios:

* Restore to original location
* Restore to original location with different settings

* Restore to another location
* Secure restore

The recovered VM runs from a backup and does not provide a wholly functioning service. You need to finalize the successful instant recovery by one of the following steps:

* Remove the recovered VM. You can stop publishing the recovered VM and discard the changes made to it while it was running from backup. To do this, run the [Stop-VBRInstantRecovery](stop-vbrinstantrecovery.md) cmdlet.
* Migrate the recovered VM to the production. To do this, run the [Start-VBRHvInstantRecoveryMigration](start-vbrhvinstantrecoverymigration.md) cmdlet.

Run the [Restart-VBRInstantRecovery](restart-vbrinstantrecovery.md) cmdlet to restart the Instant Recovery session if it failed for some reason.

Run the [Get-VBRInstantRecovery](get-vbrinstantrecovery.md) cmdlet to get the session status.

|  |
| --- |
| Note: |
| * To recover Hyper-V workloads to VMware vSphere VMs, run the [Start-VBRViComputerInstantRecovery](start-vbrvicomputerinstantrecovery.md) cmdlet. * The cmdlet will not run if the geographic location of the repository where backups reside and the target host location do not match. If you still want to run the cmdlet, use the Force parameter. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point to which you want to restore the workload. | Accepts the COib object. To create this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| Server | Specifies the host where the restored VM will reside. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| Path | To redirect the redo logs.  Specifies the path to the folder where you want to restore the VM.  Note: This parameter is required if you provide the Server parameter. | String | False | Named | False |
| VMName | Specifies the name you want to apply to the restored VM. By default, the original name is applied. | String | False | Named | False |
| PreserveVmID | Defines whether the restored VM gets the ID of the original workload:   * True: the restored VM will get the ID of the original VM. * False: the restored VM will get a new ID. | Bool | False | Named | False |
| PowerUp | Defines whether to power on the VM right after restore:   * True: the restored VM will be powered on. * False: the restored VM will be powered off and you will need to power on it manually. | Bool | False | Named | False |
| NICsEnabled | Defines whether to connect the restored VM to the network:   * True: the restored VM will be connected to the network. * False: the restored VM will have no network connections. | Bool | False | Named | False |
| PreserveMACs | Defines whether the restored VM gets the MAC address of the original workload:   * True: the restored VM will get the MAC address of the original workload. * False: the restored VM will get a new MAC address.   Note: If the original workload keeps running, preserving the MAC address will cause conflict. Preserving the workload address is useful if the original VM will not be used in future — in this case, the restored VM will be able to use the MAC settings used by its applications, if any are installed. | Bool | False | Named | False |
| Reason | Specifies the reason for performing restore of the selected workload.  The information you provide will be saved in the session history so that you can reference it later. | String | False | Named | False |
| Credentials | Used to access VMs stored on shared folders.  Specifies the credentials you want to use to authenticate with the shared folder. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will perform restore even if the geographic location of the repository where backups reside and the target host location do not match. The cmdlet will not show any warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| EnableAntivirusScan | Enables secure restore. Veeam Backup & Replication will trigger the antivirus software to scan the selected workloads before the restore. | SwitchParameter | False | Named | False |
| EnableYARAScan | Enables the YARA scan for the selected VMs.  Use the YARAScanRule parameter to specify the YARA rule to be used. | SwitchParameter | False | Named | False |
| YARAScanRule | Specifies the YARA rule. Veeam Backup & Replication will scan VMs with this rule.  Veeam Backup & Replication searches for YARA rules in the YaraRules folder. The default path is: C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules.  To use a YARA rule, you must specify its name and extension. Veeam Backup & Replication accepts only .yar and .yara extensions. | String | False | Named | False |
| EnableEntireVolumeScan | For secure restore.  Defines that the antivirus will continue workload scan after the first virus threat is found. Use this option if you want to get the report on all virus threats. | SwitchParameter | False | Named | False |
| VirusDetectionAction | For secure restore.  Specifies the secure restore action when the infection is detected.   * DisableNetwork — use this option if you want to restore VMs in with disabled network adapters (NICs). * AbortRecovery — use this option if you want to cancel the restore session. | Accepts the VBRVirusDetectionAction enum type. | False | Named | False |
| NetworkMapping | Specifies an array of network mapping rules. These rules specify how to map networks in the original site with networks in the target site (where the recovered VM will reside).  Note: This parameter applies if you perform instant recovery of Veeam Agent computers. | Accepts the VBRHvInstantRecoveryNetworkMappingRule[] object. To create this object, run the [New-VBRHvInstantRecoveryNetworkMappingRule](new-vbrhvinstantrecoverynetworkmappingrule.md) cmdlet. | False | Named | False |
| HelperAppliance | Specifies settings of a helper appliance used to restore Linux-based VMs.  Note: This parameter applies if you perform instant recovery for workloads other than Microsoft Hyper-V VMs. | Accepts the VBRHvInstantRecoveryHelperAppliance object. To create this object, run the [New-VBRHvInstantRecoveryHelperAppliance](new-vbrhvinstantrecoveryhelperappliance.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| DisableDiskAllocation | Defines whether to allocate disk space. | SwitchParameter | False | Named | False |
| DiskMappingRule | Specifies backed-up virtual disk mapping settings. | Accepts the VBRHvVirtualDeviceMappingRule[] object. To create this object, run the [New-VBRHvVirtualDeviceMappingRule](new-vbrhvvirtualdevicemappingrule.md) cmdlet. | False | Named | False |
| RegisterAsClusterResource | Defines that the restored VM will be registered as a part of a cluster in case you restore the VM to a clustered host. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Instant Recovery of VM

|  |  |
| --- | --- |
| The example shows how to start Instant Recovery of the VM.  |  | | --- | | $restorepoint = Get-VBRRestorePoint  Start-VBRHvInstantRecovery -RestorePoint $restorepoint[1] |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the Start-VBRHvInstantRecovery cmdlet. Set the $restorepoint variable as the RestorePoint parameter value.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the second restore point is used. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting Instant Recovery of VM with Different Settings

|  |  |
| --- | --- |
| The example shows how to start Instant Recovery of the VM. The job will run with the following settings:   * The path to the folder where the restored VM is located is C:\Hyper-V\Virtual Hard Disks. * The VM will be restored with the New-Exch01 name. * The PowerUp parameter is set to enable the VM power up automatically.   |  | | --- | | $restorepoint = Get-VBRRestorePoint  $server = Get-VBRServer  Start-VBRHvInstantRecovery -RestorePoint $restorepoint[1] -Server $server -Path "c:\Hyper-V\Virtual Hard Disks" -VMName "New-Exch01" -PowerUp $True |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Save the result to the $server variable. 3. Run the Start-VBRHvInstantRecovery cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the second restore point is used.   * Set the $server variable as the Server parameter value. * Specify the Path parameter value. * Specify the VMName parameter value. * Set the PowerUp parameter to $True. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Starting Secure Restore of VM

|  |  |
| --- | --- |
| The example shows how to run the secure restore of the selected VM. The job will run with the following settings:   * The antivirus will continue VM scan after the first virus threat is found.  * In case the threat is detected, Veeam Backup & Replication will restore the VM with disabled NIC.   |  | | --- | | $restorepoint = Get-VBRRestorePoint  Start-VBRHvInstantRecovery -RestorePoint $restorepoint[1] -EnableAntivirusScan -EnableEntireVolumeScan -VirusDetectionAction DisableNetwork |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable. 2. Run the Start-VBRHvInstantRecovery cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the second restore point is used.   * Provide the EnableAntivirusScan parameter value. * Provide the EnableEntireVolumeScan parameter value. * Set the DisableNetwork option for the VirusDetectionAction parameter. |

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRLocation](get-vbrlocation.md)


