---
title: "Start-VBREpInstantRecovery"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrepinstantrecovery.html"
last_updated: "12/10/2024"
product_version: "13.0.1.1071"
---

# Start-VBREpInstantRecovery


Short Description

Starts instant recovery of physical computers to virtual infrastructure.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBREpInstantRecovery -RestorePoint <COib> -Server <CHost> -Path <string> [-VMName <string>] [-PowerUp <bool>] [-NICsEnabled <bool>] [-PreserveMACs <bool>] [-Reason <string>] [-Credentials <CCredentials>] [-EnableAntivirusScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireVolumeScan] [-VirusDetectionAction <VBRVirusDetectionAction> {DisableNetwork | AbortRecovery}]  [<CommonParameters>] |

Detailed Description

This cmdlet starts an instant recovery session for physical machines. The process restores a backup of a physical computer to a virtualization host.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point of the physical computer to which you want to restore the VM. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| Server | Specifies the host where you want to locate the restored VM. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | 2 | False |
| Path | Used to redirect the redo logs.  Specifies the path to the folder where you want to store the changes made to the VM during the instant recovery. | String | True | 3 | False |
| VmName | Specifies the name you want to apply to the restored VM. By default, the original VM name is applied. | String | False | Named | False |
| PowerUp | If set to True, the restored VM will be powered up immediately after the restore. Otherwise, you will have to power up the VM manually. | Bool | False | Named | False |
| NICsEnabled | If set to True, the restored VM will be connected to the network. Otherwise the VM will have no network connections. | Bool | False | Named | False |
| PreserveMACs | If set to True, the restored VM will get the MAC address of the original VM. Otherwise, the restored VM will get a new MAC address.  Note: If the original computer keeps running, preserving the MAC address will cause conflict. Preserving the MAC address is useful in case the original computer will not be used in future - in this case, the restored VM will be able to use the MAC settings used by its applications, if any are installed. | Bool | False | Named | False |
| Reason | Specifies the reason for performing restore of the selected endpoint.  The information you provide will be saved in the session history so that you can reference it later. | String | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the VM. | Accepts the CCredentials object. To get this object, run the  cmdlet. | False | Named | False |
| EnableAntivirusScan | Enables the option to perform secure restore. Veeam Backup & Replication will trigger the antivirus software to scan selected VMs before the restore. | SwitchParameter | False | Named | False |
| EnableYARAScan | Enables the YARA scan for the selected VMs.  Use the YARAScanRule parameter to specify the YARA rule to be used. | SwitchParameter | False | Named | False |
| YARAScanRule | Specifies the YARA rule. Veeam Backup & Replication will scan VMs with this rule.  Veeam Backup & Replication searches for YARA rules in the YaraRules folder. The default path is: C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules.  To use a YARA rule, you must specify its name and extension. Veeam Backup & Replication accepts only .yar and .yara extensions. | String | False | Named | False |
| EnableEntireVolumeScan | For secure restore.  Enables the option for the antivirus to continue machine scan after the first virus threat is found. Use this option if you want to get the report on all virus threats. | SwitchParameter | False | Named | False |
| VirusDetectionAction | For secure restore.  Specifies secure restore action when the virus threat is detected.   * DisableNetwork - use this option if you want to restore VMs in safe state with disabled network adapters (NICs). * AbortRecovery - use this option if you want to cancel the restore session. | VBRVirusDetectionAction | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Starting Secure Restore of Selected Machine

This example shows how to run secure restore of the selected machine. The job will run with the following settings:

* The antivirus will continue VM scan after the first virus threat is found

* In case the threat is detected, Veeam Backup & Replication will restore the machine with disabled NIC

* The RunAsync parameter is set to bring the process to the background.

|  |
| --- |
| $restorepoint = Get-VBRRestorePoint  Start-VBREpInstantRecovery -RestorePoint $restorepoint[1] -RunAsync -EnableAntivirusScan -EnableEntireVolumeScan -VirusDetectionAction DisableNetwork |

Perform the following steps:

1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable.

The [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the second restore point in the array).

1. Run the Start-VBREpInstantRecovery cmdlet. Specify the following settings:

* Set the $restorepoint variable as the RestorePoint parameter value.
* Provide the RunAsync parameter value.
* Provide the EnableAntivirusScan parameter value.
* Provide the EnableEntireVolumeScan parameter value.
* Set the DisableNetwork option for the VirusDetectionAction parameter.

Related Commands

[Get-VBRRestorePoint](get-vbrrestorepoint.md)


