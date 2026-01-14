---
title: "Start-VBRVMRestoreToGoogleCloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrvmrestoretogooglecloud.html"
last_updated: "9/11/2025"
product_version: "13.0.1.1071"
---

# Start-VBRVMRestoreToGoogleCloud

In this article

Short Description

Starts a restore session to Google Compute Engine.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRVMRestoreToGoogleCloud -RestorePoint <COib> -Zone <VBRGoogleCloudComputeZone> [-LicenseType <VBRGoogleCloudLicenseType>] -InstanceType <VBRGoogleCloudComputeInstanceType> -VMName <string> -DiskConfiguration <VBRGoogleCloudComputeDiskConfiguration[]> -Subnet <VBRGoogleCloudComputeSubnet> [-Reason <string>] [-EnableAntivirusScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireVolumeScan] [-VirusDetectionAction {ConnectToIsolatedNetwork | AbortRecovery}] [-VirusIsolatedSubnet <VBRGoogleCloudComputeSubnet>] [-ProxyAppliance <VBRGoogleCloudComputeProxyAppliance>] [-GoogleCloudLabel <VBRGoogleCloudComputeLabel[]>] [-ShutdownVM] [-AllocatePublicIP] [-Wait]  [<CommonParameters>] |

Detailed Description

This cmdlet starts a restore session to Google Compute Engine.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point of machines that you want to restore to Google Compute Engine. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | False |
| Zone | Specifies the Google Cloud availability zone. The cmdlet will restore the VM to this Google Cloud availability zone. | Accepts the VBRGoogleCloudComputeZone object. To get this object, run the [Get-VBRGoogleCloudComputeZone](get-vbrgooglecloudcomputezone.md) cmdlet. | True | Named | False |
| InstanceType | Specifies the Google Cloud VM instance type. The cmdlet will restore the VM with the CPU and memory settings of the selected VM instance. | Accepts the VBRGoogleCloudComputeInstanceType object. To get this object, run the [Get-VBRGoogleCloudComputeInstanceType](get-vbrgooglecloudcomputeinstancetype.md) cmdlet. | True | Named | False |
| VMName | Specifies the name for the target Google Cloud instance. Veeam Backup & Replication will restore the VM instance with this name. | String | True | Named | False |
| DiskConfiguration | Specifies the array of disk settings for Google Cloud VM instances.  If you do not specify this parameter, the cmdlet will restore all disks as balanced persistent. | Accepts the VBRGoogleCloudComputeDiskConfiguration object. To add this object, run the [New-VBRGoogleCloudComputeDiskConfiguration](new-vbrgooglecloudcomputediskconfiguration.md) cmdlet. | True | Named | False |
| Subnet | Specifies the Google Cloud subnet. | Accepts the VBRGoogleCloudComputeSubnet object. To get this object, run the [Get-VBRGoogleCloudComputeSubnet](get-vbrgooglecloudcomputesubnet.md) cmdlet. | True | Named | False |
| LicenseType | Specifies the OS license. You can select the following types of licenses:   * BYOL - set this option if you want to restore the OS license from the backup. For more information, see [Google Cloud documentation](https://cloud.google.com/compute/docs/nodes/bringing-your-own-licenses). * ProvidedByGoogle - set this option if you want Google Compute Engine to provide the license on the restored VM.   If you do not specify this parameter, the cmdlet will launch restore with the license type default for the machine OS. | VBRGoogleCloudLicenseType | False | Named | False |
| Reason | Specifies the restore reason. | String | False | Named | False |
| EnableAntivirusScan | Enables secure restore. If you provide this parameter, Veeam Backup & Replication will trigger the antivirus software to scan selected VMs before the restore. | SwitchParameter | False | Named | False |
| EnableYARAScan | Enables the YARA scan for the selected VMs.  Use the YARAScanRule parameter to specify the YARA rule to be used. | SwitchParameter | False | Named | False |
| YARAScanRule | Specifies the YARA rule. Veeam Backup & Replication will scan VMs with this rule.  Veeam Backup & Replication searches for YARA rules in the YaraRules folder. The default path is: C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules.  To use a YARA rule, you must specify its name and extension. Veeam Backup & Replication accepts only .yar and .yara extensions. | String | False | Named | False |
| EnableEntireVolumeScan | For secure restore.  Enables VMs scan by an antivirus after the first virus threat is found. If you provide this parameter, the cmdlet will generate a report on all virus threats. | SwitchParameter | False | Named | False |
| VirusDetectionAction | For secure restore.  Specifies secure restore action when the virus threat is detected.   * ConnectToIsolatedNetwork - use this option if you want to restore the machine to an isolated Google Cloud network. * AbortRecovery - use this option if you want to cancel the restore session. | Enum | False | Named | False |
| VirusIsolatedSubnet | Specifies the Google Cloud subnet where the restore will be performed if Veeam Backup & Replication detects any virus threats.  Note: This parameter is required if you set the ConnectToIsolatedNetwork option for the VirusDetectionAction parameter value. | Accepts the VBRGoogleCloudComputeSubnet object. To get this object, run the [Get-VBRGoogleCloudComputeSubnet](get-vbrgooglecloudcomputesubnet.md) cmdlet. | False | Named | False |
| ProxyAppliance | Specifies the Google Cloud proxy appliance. | Accepts the VBRGoogleCloudComputeProxyAppliance object. To add this object, run the [New-VBRGoogleCloudComputeProxyAppliance](new-vbrgooglecloudcomputeproxyappliance.md) cmdlet. | False | Named | False |
| GoogleCloudLabel | Specifies an array of Google Cloud labels. The cmdlet will restore VMs with the specified labels. | Accepts the VBRGoogleCloudComputeLabel object. To add this object, run the [New-VBRGoogleCloudComputeLabel](new-vbrgooglecloudcomputelabel.md) cmdlet. | False | Named | False |
| ShutdownVM | Defines that the cmdlet will power off the restored VM after the restore is complete.  If you do not provide this parameter, the restored VM will remain powered on. | SwitchParameter | False | Named | False |
| AllocatePublicIP | Defines that the cmdlet will assign a public IP to the restored VM.  If you do not provide this parameter, the restored VM will remain without the public IP. | SwitchParameter | False | Named | False |
| Wait | Defines that the command will wait for the process to complete before accepting more input. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGoogleCloudRestoreSession](vbrgooglecloudrestoresession.md)

Examples

Starting Session of Machine Restore to Google Compute Engine

This example shows how to restore machines to Google Compute Engine.

|  |
| --- |
| $backup = Get-VBRBackup -Name "MSExchange Backup"  $restorepoint = Get-VBRRestorePoint -backup $backup  $account = Get-VBRGoogleCloudComputeAccount -Name "GCP service acc 1"  $computeregion = Get-VBRGoogleCloudComputeRegion -Account $account  $computezone = Get-VBRGoogleCloudComputeZone -Region $computeregion  $instancetype = Get-VBRGoogleCloudComputeInstanceType -Zone $computezone  $diskconfig = New-VBRGoogleCloudComputeDiskConfiguration -DiskName "srv20.vhdx" -DiskType StandardPersistent  $subnet = Get-VBRGoogleCloudComputeSubnet -Region $computeregion  $label = New-VBRGoogleCloudComputeLabel -Key "location" -Value "west"  Start-VBRVMRestoreToGoogleCloud -RestorePoint $restorepoint -Zone $computezone -InstanceType $instancetype -VMName "Restored VM" -DiskConfiguration $diskconfig -Subnet $subnet -Reason "Data recovery" -EnableAntivirusScan -EnableEntireVolumeScan -VirusDetectionAction AbortRecovery -GoogleCloudLabel $label -AllocatePublicIP |

Perform the following steps:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Provide the Name parameter value. Save the result to the $backup variable.
2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the backup parameter. Save the result to the $restorepoint variable.
3. Run the [Get-VBRGoogleCloudComputeAccount](get-vbrgooglecloudcomputeaccount.md) cmdlet. Provide the Name parameter value. Save the result to the $account variable.
4. Run the [Get-VBRGoogleCloudComputeRegion](get-vbrgooglecloudcomputeregion.md) cmdlet. Set the $account variable as the Account parameter. Save the result to the $computeregion variable.
5. Run the [Get-VBRGoogleCloudComputeZone](get-vbrgooglecloudcomputezone.md) cmdlet. Set the $computeregion variable as the Region parameter. Save the result to the $computezone variable.
6. Run the [Get-VBRGoogleCloudComputeInstanceType](get-vbrgooglecloudcomputeinstancetype.md) cmdlet. Set the $computezone variable as the Zone parameter. Save the result to the $instancetype variable.
7. Run the [New-VBRGoogleCloudComputeDiskConfiguration](new-vbrgooglecloudcomputediskconfiguration.md) cmdlet. Specify the DiskName and DiskType parameter values. Save the result to the $diskconfig variable.
8. Run the [Get-VBRGoogleCloudComputeSubnet](get-vbrgooglecloudcomputesubnet.md) cmdlet. Set the $computeregion variable as the Region parameter. Save the result to the $subnet variable.
9. Run the [New-VBRGoogleCloudComputeLabel](new-vbrgooglecloudcomputelabel.md) cmdlet. Specify the Key and Value parameter values. Save the result to the $label variable.
10. Run the Start-VBRVMRestoreToGoogleCloud cmdlet. Specify the following settings:

* Set the $restorepoint variable as the RestorePoint parameter value.
* Set the $computezone variable as the Zone parameter value.
* Set the $instancetype variable as the InstanceType parameter value.
* Specify the VMName parameter value.
* Set the $diskconfig variable as the DiskConfiguration parameter value.
* Set the $subnet variable as the Subnet parameter value.
* Specify the Reason parameter value.
* Provide the EnableAntivirusScan parameter.
* Provide the EnableEntireVolumeScan parameter.
* Set the AbortRecovery option for the VirusDetectionAction parameter value.
* Set the $label variable as the GoogleCloudLabel parameter value.
* Provide the AllocatePublicIP parameter.

Related Commands

* [Get-VBRBackup](get-vbrrestorepoint.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRGoogleCloudComputeRegion](get-vbrgooglecloudcomputeregion.md)
* [Get-VBRGoogleCloudComputeZone](get-vbrgooglecloudcomputezone.md)
* [Get-VBRGoogleCloudComputeInstanceType](get-vbrgooglecloudcomputeinstancetype.md)
* [New-VBRGoogleCloudComputeDiskConfiguration](new-vbrgooglecloudcomputediskconfiguration.md)
* [Get-VBRGoogleCloudComputeSubnet](get-vbrgooglecloudcomputesubnet.md)
* [New-VBRGoogleCloudComputeLabel](new-vbrgooglecloudcomputelabel.md)

Page updated 9/11/2025

Page content applies to build 13.0.1.1071
