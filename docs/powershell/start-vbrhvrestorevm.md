---
title: "Start-VBRHvRestoreVM"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrhvrestorevm.html"
last_updated: "12/10/2024"
product_version: "13.0.1.1071"
---

# Start-VBRHvRestoreVM

In this article

Short Description

Starts restore of an entire Hyper-V VM.

Applies to

Platform: Hyper-V

For VMware, run the [Start-VBRRestoreVM](start-vbrrestorevm.md) cmdlet.

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Restore to a new location, and/or to original location with different settings.

|  |
| --- |
| Start-VBRHvRestoreVM -RestorePoint <COib> [-Server <CHost>] [-Path <string>] [-VMName <string>] [-PreserveVmID<bool>] [-PowerUp] [-RegisterAsClusterResource] [-NICsEnabled <bool>] [-PreserveMACs <bool>] [-User <string>] [-Password <string>] [-Credential <pscredential>] [-Reason <string>] [-RunAsync] [-QuickRollback] [-Force] [-EnableAntivirusScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireVolumeScan] [-VirusDetectionAction <VBRVirusDetectionAction>] [-NetworkMapping <VBRHvInstantRecoveryNetworkMappingRule[]>]  [<CommonParameters>] |

* Restore using the staging restore option.

|  |
| --- |
| Start-VBRHvRestoreVM -RestorePoint <COib> -EnableStagedRestore -StagingVirtualLab <CHvSbVirtualLab> -StagingScript <string> -StagingCredentials <CInternalCredentials> [-Server <CHost>] [-Path <string>] [-VMName <string>] [-PreserveVmID <bool>] [-PowerUp] [-RegisterAsClusterResource] [-NICsEnabled <bool>] [-PreserveMACs <bool>] [-User <string>] [-Password <string>] [-Credential <pscredential>] [-Reason <string>] [-RunAsync] [-QuickRollback] [-Force] [-StagingApplicationGroup <CSbAppGroup>] [-StagingStartupOptions <VBRApplicationGroupStartupOptions>] [-EnableAntivirusScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireVolumeScan] [-VirusDetectionAction <VBRVirusDetectionAction>] [-NetworkMapping <VBRHvInstantRecoveryNetworkMappingRule[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet starts the restore of an entire Hyper-V VM. With this cmdlet, you can perform the following recover scenarios:

* Restore to original location
* Restore to original location with different settings

* Restore to another location
* Staged restore
* Secure restore

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point to which you want to restore VMs. | Accepts the RestorePoint object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 1 | True (ByValue, |
| EnableStagedRestore | For staged restore.  Defines that the cmdlet will perform staged restore. If you do not provide this parameter, the cmdlet will not perform staged restore. | SwitchParameter | True | Named | False |
| StagingCredentials | For staged restore.  Specifies the credentials for the account that has administrator privileges on VMs that you want to restore. The cmdlet will use these credentials to authenticate against VMs and run the script. | Accepts the CInternalCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |
| StagingScript | For staged restore.  Specifies the script location. Veeam Backup & Replication will use this script to prepare VMs before the restore. | String | True | Named | False |
| StagingVirtualLab | For staged restore.  Specifies the virtual lab. The cmdlet will use this virtual lab to start VMs and run the script. | Accepts the CHvSbVirtualLab object. To get this object, run the [Get-VSBHvVirtualLab](get-vsbhvvirtuallab.md) cmdlet. | True | Named | False |
| Server | Specifies the host where you want to locate the restored VM. By default, the cmdlet will restore a VM to its original location.  Note: This parameter is required for the staged restore jobs. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| Path | Specifies the path to the folder where you want to restore the VM. | String | False | Named | False |
| VMName | Specifies the name you want to apply to the restored VM. By default, the original VM name is applied. | String | False | Named | False |
| PreserveVmID | Defines whether the restored VM will get the UUID of the original VM.  Note: The cmdlet deletes the original VM if you restore it to the same Hyper-V host. This is done to avoid UUID conflicts. To keep both VMs in the same location, the restored VM must have a new UUID and a different name. To generate a new UUID, set this parameter to False.   * True: The cmdet will restore a VM with the UUID of the original VM. * False: The cmdet will restore a VM with a new UUID. | Bool | False | Named | False |
| PowerUp | Defines that the restored VM will be powered up immediately after the restore. If you do not provide this parameter, you will have to power up the VM manually. | SwitchParameter | False | Named | False |
| RegisterAsClusterResource | Defines that the restored VM will be registered as a part of a cluster in case you restore the VM to a clustered host. | SwitchParameter | False | Named | False |
| NICsEnabled | Defines that the restored VM will be connected to the network. If you do not provide this parameter, the VM will have no network connections.  Default: False. | SwitchParameter | False | Named | False |
| PreserveMACs | Defines that the restored VM will get the MAC address of the original VM. If you do not provide this parameter, the restored VM will get a new MAC address.  Note: If the original VM keeps running, preserving the MAC address will cause conflict. Preserving the MAC address is useful in case the original VM will not be used in future - in this case, the restored VM will be able to use the MAC settings used by its applications, if any are installed.  Default: False. | SwitchParameter | False | Named | False |
| User | Specifies the user name you want to use to access a backup file imported from a shared folder.  Note: If you provide the User and Password parameters, you must omit the Credentials parameter. | String | False | Named | False |
| Password | Specifies the password you want to use to access a backup file imported from a shared folder.  Note: If you provide the User and Password parameters, you must omit the Credentials parameter. | String | False | Named | False |
| Credential | Specifies the credentials you want to use to access a backup file imported from a shared folder.  Note: If you provide this parameter, you must omit the User and Password parameters. | Accepts the PSCredential object. To get this object, run the [Get-Credential](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.1) cmdlet | False | Named | False |
| Reason | Specifies a reason of restoring the selected VM.  The information you provide will be saved in the session history so that you can reference it later. | String | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| QuickRollback | For restore to original location.  Defines that the incremental restore must be performed. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will perform VM restore even if the geographic location of the repository where VM backups reside and the target host location do not match. | SwitchParameter | False | Named | False |
| StagingApplicationGroup | For staged restore.  Specifies the application group that the cmdlet will use for staged restore. | Accepts the CSbAppGroup object. To get this object, run the [Get-VSBApplicationGroup](get-vsbapplicationgroup.md) cmdlet. | False | Named | False |
| StagingStartupOptions | For staged restore.  Specifies startup settings of VMs that you want to restore. Veeam Backup & Replication will use these settings to start selected VMs after recovery. | Accepts the VBRApplicationGroupStartupOptions object. To get this object, run the [New-VBRApplicationGroupStartupOptions](new-vbrapplicationgroupstartupoptions_surebackup.md) cmdlet. | False | Named | False |
| EnableAntivirusScan | Defines that the cmdlet will perform secure restore. Veeam Backup & Replication will trigger the antivirus software to scan selected VMs before the restore. | SwitchParameter | False | Named | False |
| EnableYARAScan | Enables the YARA scan for the selected VMs.  Use the YARAScanRule parameter to specify the YARA rule to be used. | SwitchParameter | False | Named | False |
| YARAScanRule | Specifies the YARA rule. Veeam Backup & Replication will scan VMs with this rule.  Veeam Backup & Replication searches for YARA rules in the YaraRules folder. The default path is: C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules.  To use a YARA rule, you must specify its name and extension. Veeam Backup & Replication accepts only .yar and .yara extensions. | String | False | Named | False |
| EnableEntireVolumeScan | For secure restore.  Enables the option to continue antivirus scan of the VMs after the first virus threat is found. Use this option if you want to get the report on all virus threats. | SwitchParameter | False | Named | False |
| VirusDetectionAction | For secure restore.  Specifies the secure restore action when the infection is detected.   * DisableNetwork - use this option if you want to restore VMs in with disabled network adapters (NICs). * AbortRecovery - use this option if you want to cancel the restore session. | VBRVirusDetectionAction | False | Named | False |
| NetworkMapping | Specifies an array of network mapping rules. These rules specify how to map networks in the original site with networks in the target site (where the recovered VM will reside).    Note: This parameter applies if you perform instant recovery of Veeam Agent computers. | Accepts the VBRHvInstantRecoveryNetworkMappingRule[] object. To create this object, run the [New-VBRHvInstantRecoveryNetworkMappingRule](new-vbrhvinstantrecoverynetworkmappingrule.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Entire Hyper-V VM to Original Location

|  |  |
| --- | --- |
| This example shows how to restore the srv01 Hyper-V VM to its original location.  Note: If the original VM still exists in the virtual infrastructure, its disks will be removed. Make sure that other VMs in the virtual environment do not use these disks.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name srv01 | Sort-Object -Property CreationTime -Descending | Select-Object -First 1  Start-VBRHvRestoreVM -RestorePoint $restorepoint |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Save the result to the $restorepoint variable. 2. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter. 3. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Set 1 as the First parameter value. 4. Run the Start-VBRHvRestoreVM cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Cloning Hyper-V VM to Original Location

|  |  |
| --- | --- |
| This example shows how to clone the srv01 Hyper-V VM to its original location. The cmdlet will keep the restored VM files in the E:\Storage\HyperV\srv01 folder.  Note: To keep the original VM and the cloned VM in the same location, you must specify a different name, UUID and a path to the folder where you want to keep the cloned VM. Otherwise, the cmdlet will replace the original VM with the cloned one.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name srv01 | Sort-Object -Property CreationTime -Descending | Select-Object -First 1  Start-VBRHvRestoreVM -RestorePoint $restorepoint -VMName srv01\_copy -PreserveVmID $false -Path "E:\Storage\HyperV\srv01" |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Save the result to the $restorepoint variable. 2. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter. 3. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Set 1 as the First parameter value. 4. Run the Start-VBRHvRestoreVM cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Specify the VMName parameter value. * Set the PreserveVmID parameter to the $false value. * Specify the Path parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Restoring Hyper-V VM to Another Location

|  |  |
| --- | --- |
| This example shows how to restore the srv01 Hyper-V VM to hyperv01.east.support server. The cmdlet will keep the restored VM files in the D:\Storage\HyperV\srv01\_restored folder.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name srv01 | Sort-Object -Property CreationTime -Descending | Select-Object -First 1  $server = Get-VBRServer -Type HvServer -Name "hyperv01.east.support"  Start-VBRHvRestoreVM –RestorePoint $restorepoint –Server $server -Path "D:\Storage\HyperV\srv01\_restored" |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Save the result to the $restorepoint variable. 2. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter. 3. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Set 1 as the First parameter value. 4. Run the [Get-VBRServer](get-vbrserver.md)  cmdlet. Specify the Type and Name parameter values. Save the result to the $server variable. 5. Run the Start-VBRHvRestoreVM cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Set the $server variable as the Server parameter value.  * Specify the Path parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Performing Staged Restore of Hyper-V VM

|  |  |
| --- | --- |
| This example shows how to perform staged restore for the srv01 VM.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name srv01 | Sort-Object -Property CreationTime -Descending | Select-Object -First 1  $lab = Get-VSBHvVirtualLab -Name VirtualLab  $creds = Get-VBRCredentials -Name Administrator  Start-VBRHvRestoreVM -RestorePoint $restorepoint -StagingVirtualLab $lab -StagingScript "c:/script.cmd" -EnableStagedRestore -StagingCredentials $creds |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Save the result to the $restorepoint variable. 2. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter. 3. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Set 1 as the First parameter value. 4. Run the [Get-VSBHvVirtualLab](get-vsbhvvirtuallab.md) cmdlet. Specify the Name parameter value. Save the result to the $lab variable. 5. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $creds variable. 6. Run the Start-VBRHvRestoreVM cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Set the $lab variable as the StagingVirtualLab parameter value.  * Specify the StagingScript parameter value. * Provide the EnableStagedRestore parameter.  * Set the $creds variable as the StagingVirtualLab parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Performing Secure Restore of Hyper-V VM

|  |  |
| --- | --- |
| This example shows how to perform secure restore of the srv01 VM. The restore session will run with the following settings:   * The antivirus will continue VM scan after the first virus threat is found * In case the threat is detected, Veeam Backup & Replication will restore the VM with disabled NIC * The RunAsync parameter is set to bring the process to the background   |  | | --- | | $restorepoint = Get-VBRRestorePoint -Name srv01 | Sort-Object -Property CreationTime -Descending | Select-Object -First 1  Start-VBRHvRestoreVM -RestorePoint $restorepoint -RunAsync -EnableAntivirusScan -EnableEntireVolumeScan -VirusDetectionAction DisableNetwork |  You must perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Save the result to the $restorepoint variable. 2. Pipe the cmdlet output to the [Sort-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7) cmdlet. Set the CreationTime value for the Property parameter. Provide the Descending parameter. 3. Pipe the cmdlet output to the [Select-Object](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7) cmdlet. Set 1 as the First parameter value. 4. Run the Start-VBRHvRestoreVM cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value.  * Provide the RunAsync parameter. * Provide the EnableAntivirusScan parameter. * Provide the EnableEntireVolumeScan parameter.  * Set the DisableNetwork option for the VirusDetectionAction parameter. |

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRLocation](get-vbrlocation.md)
* [Get-VSBHvVirtualLab](get-vsbhvvirtuallab.md)
* [Get-VBRCredentials](get-vbrcredentials.md)

Page updated 12/10/2024

Page content applies to build 13.0.1.1071
