---
title: "Start-VBRVMRestoreToAmazon"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrvmrestoretoamazon.html"
last_updated: "11/13/2025"
product_version: "13.0.1.1071"
---

# Start-VBRVMRestoreToAmazon


Short Description

Starts a restore session of workloads to Amazon EC2 service.

Applies to

Platform: VMware, Hyper-V

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRVMRestoreToAmazon -RestorePoint <COib> -LicenseType {BYOL | ProvidedByAWS} -InstanceType <VBRAmazonEC2InstanceType> -VMName <string> -Subnet <VBRAmazonEC2Subnet> -SecurityGroup <VBRAmazonEC2SecurityGroup> [-Region <VBRAmazonEC2Region>] [-DiskConfiguration <VBRAmazonEC2DiskConfiguration[]>] [-VPC <VBRAmazonEC2VPC>] [-Reason <string>] [-EnableAntivirusScan] [-EnableYARAScan] [-YARAScanRule <string>] [-EnableEntireVolumeScan] [-VirusDetectionAction {ConnectToIsolatedSecurityGroup | AbortRecovery}] [-VirusIsolatedSecurityGroup <VBRAmazonEC2SecurityGroup>] [-ProxyAppliance <VBRAmazonEC2ProxyAppliance>] [-Credentials <CCredentials>] [-Wait] [-AmazonEC2Tag <VBRAmazonEC2Tag[]>] [-AllocatePublicIP] [-PrivateIpAddress <VBRAmazonIpAddress>] [-ShutdownVM] [<CommonParameters>] |

Detailed Description

This cmdlet starts a restore session of workloads to Amazon EC2 service.

|  |
| --- |
| Note |
| To stop a restore session, run the [Stop-VBRVMRestoreToAmazon](stop-vbrvmrestoretoamazon.md) cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point of workloads that you want to restore to Amazon EC2. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | False |
| LicenseType | Specifies the OS license. You can select the following types of licenses:   * BYOL - use this option if you want to use your existing licenses for Microsoft software. * ProvidedByAWS - use this option if you want Amazon EC2 to update the license on the restored VM. | VBRAmazonEC2LicenseType | True | Named | False |
| InstanceType | Specifies the Amazon EC2 instance type. The cmdlet will restore the VM with the CPU and memory settings of the selected instance. | Accepts the VBRAmazonEC2InstanceType object. To get this object, run the [Get-VBRAmazonEC2InstanceType](get-vbramazonec2instancetype.md) cmdlet. | True | Named | False |
| VMName | Specifies the name for the target EC2 instance. Veeam Backup & Replication will restore the instance with this name. | String | True | Named | False |
| Region | Specifies the Amazon EC2 region. The cmdlet will restore the VM to this Amazon EC2 region. | Accepts the [VBRAmazonEC2Region](vbramazonec2region.md) object. To get this object, run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. | False | Named | False |
| DiskConfiguration | Specifies the array of storage volume settings for Amazon EC2 instances.  If you do not specify this parameter, the cmdlet will restore all disks as General Purpose SSD (GP2). | Accepts the VBRAmazonEC2DiskConfiguration[] object. To get this object, run the [New-VBRAmazonEC2DiskConfiguration](new-vbramazonec2diskconfiguration.md) cmdlet. | False | Named | False |
| VPC | Specifies the Amazon VPC. | Accepts the VBRAmazonEC2VPC object. To get this object, run the [Get-VBRAmazonEC2VPC](get-vbramazonec2vpc.md) cmdlet. | False | Named | False |
| Subnet | Specifies the Amazon VPC subnet. | Accepts the VBRAmazonEC2Subnet object. To get this object, run the [Get-VBRAmazonEC2Subnet](get-vbramazonec2subnet.md) cmdlet. | True | Named | False |
| SecurityGroup | Specifies the Amazon VPC security group. | Accepts the VBRAmazonEC2SecurityGroup object. To get this object, run the [Get-VBRAmazonEC2SecurityGroup](get-vbramazonec2securitygroup.md) cmdlet. | True | Named | False |
| Reason | Specifies the restore reason. | String | True | Named | False |
| EnableAntivirusScan | Enables the secure restore option. Veeam Backup & Replication will trigger the antivirus software to scan selected machines before the restore. | SwitchParameter | False | Named | False |
| EnableYARAScan | Enables the YARA scan for the selected VMs.  Use the YARAScanRule parameter to specify the YARA rule to be used. | SwitchParameter | False | Named | False |
| YARAScanRule | Specifies the YARA rule. Veeam Backup & Replication will scan VMs with this rule.  Veeam Backup & Replication searches for YARA rules in the YaraRules folder. The default path is: C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules.  To use a YARA rule, you must specify its name and extension. Veeam Backup & Replication accepts only .yar and .yara extensions. | String | False | Named | False |
| EnableEntireVolumeScan | For secure restore.  Enables the option for the antivirus to continue VMs scan after the first virus threat is found. Use this option if you want to get the report on all virus threats. | SwitchParameter | False | Named | False |
| VirusDetectionAction | For secure restore.  Specifies the secure restore action when the virus threat is detected.   * ConnectToIsolatedSecurityGroup - use this option to restore the machine to a different AWS security group. Use the VirusIsolatedSecurityGroup parameter to specify the security group. * AbortRecovery - use this option to cancel the restore session. | VBRAmazonEC2VirusDetectionAction | False | Named | False |
| VirusIsolatedSecurityGroup | For secure restore.  Specifies the AmazonEC2 security group. Veeam Backup & Replication will restore the infected the machine to the selected security group. | Accepts the VBRAmazonEC2SecurityGroup object.  To get this object, run the [Get-VBRAmazonEC2SecurityGroup](get-vbramazonec2securitygroup.md) cmdlet. | False | Named | False |
| ProxyAppliance | Specifies the AmazonEC2 proxy appliance. | Accepts the VBRAmazonEC2ProxyAppliance object. To get this object, run the [New-VBRAmazonEC2ProxyAppliance](new-vbramazonec2proxyappliance.md) cmdlet. | False | Named | False |
| Credentials | For restoring backups located on a network shared folder.  Specifies the credentials to authenticate with the network shared folder. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| Wait | Defines that the command waits for the process to complete before accepting more input. | SwitchParameter | False | Named | False |
| AmazonEC2Tag | Specifies AmazonEC2 tags. The cmdlet will restore VMs with the specified tags. | Accepts the VBRAmazonEC2Tag[] object. To get this object, run the [New-VBRAmazonEC2Tag](new-vbramazonec2tag.md) cmdlet. | False | Named | False |
| AllocatePublicIP | Defines that the cmdlet assigns a public IP to the restored VM.  If you do not provide this parameter, the restored VM remains without the public IP. | SwitchParameter | False | Named | False |
| PrivateIpAddress | Specifies the dynamic or static private IP address that will be assigned to the restored workload. | Accepts the VBRAmazonIpAddress object. To create this object, run the [New-VBRAmazonIpAddress](new-vbramazonipaddress.md) cmdlet. | False | Named | False |
| ShutdownVM | Defines that the cmdlet powers off the restored VM after the restore is complete.  If you do not provide this parameter, the restored VM remains powered on. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRVMRestoreToAmazon object that contains settings of a restore session to Amazon EC2 service.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Workloads to Amazon EC2

|  |  |
| --- | --- |
| This example shows how to restore workloads to Amazon EC2.  |  | | --- | | $backup = Get-VBRBackup -Name "MSExchange"  $restorepoint = Get-VBRRestorePoint -Name \*MSExchange02\* -Backup $backup  $account = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c"  $region = Get-VBRAmazonEC2Region -Account $account -RegionType Global -Name "ap-northeast-1"  $config = New-VBRAmazonEC2DiskConfiguration -DiskName "Virtual Disk" -Include -DiskType GeneralPurposeSSD  $instance = Get-VBRAmazonEC2InstanceType -Region $region  $vpc = Get-VBRAmazonEC2VPC -Region $region  $sgroup = Get-VBRAmazonEC2SecurityGroup -VPC $vpc  $subnet = Get-VBRAmazonEC2Subnet -VPC $vpc -AvailabilityZone "eu-west-1a"  Start-VBRVMRestoreToAmazon -RestorePoint $restorepoint -Region $region -LicenseType ProvidedByAWS -InstanceType $instance -VMName "Restored VM" -DiskConfiguration $config -VPC $vpc -SecurityGroup $sgroup -Subnet $subnet -Reason "Data recovery" |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable. 3. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable. 4. Run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. Set the $account variable as the Account parameter value. Set the Global value as the RegionType parameter value. Specify the Name parameter value. Save the result to the $region variable. 5. Run the [New-VBRAmazonEC2DiskConfiguration](new-vbramazonec2diskconfiguration.md) cmdlet. Specify the DiskName parameter value. Provide the Include parameter. Set the GeneralPurposeSSD value as the DiskType parameter value. Save the result to the $config variable. 6. Run the [Get-VBRAmazonEC2InstanceType](get-vbramazonec2instancetype.md) cmdlet. Set the $region variable as the Region parameter value. Save the result to the $instance variable. 7. Run the [Get-VBRAmazonEC2VPC](get-vbramazonec2vpc.md) cmdlet. Set the $region variable as the Region parameter value. Save the result to the $vpc variable. 8. Run the [Get-VBRAmazonEC2SecurityGroup](get-vbramazonec2securitygroup.md) cmdlet. Set the $vpc variable as the VPC parameter value. Save the result to the $sgroup variable. 9. Run the [Get-VBRAmazonEC2Subnet](get-vbramazonec2subnet.md) cmdlet. Set the $vpc variable as the VPC parameter value. Specify the AvailabilityZone parameter value. Save the result to the $subnet variable. 10. Run the Start-VBRVMRestoreToAmazon cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Set the $region variable as the Region parameter value. * Set the ProvidedByAWS value as the LicenseType parameter value. * Set the $instance variable as the InstanceType parameter value. * Specify the VMName parameter value. * Set the $config variable as the DiskConfiguration parameter value. * Set the $vpc variable as the VPC parameter value. * Set the $sgroup variable as the SecurityGroup parameter value. * Set the $subnet variable as the Subnet parameter value. * Specify the Reason parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Workloads to Amazon EC2 using Proxy Appliance

|  |  |
| --- | --- |
| This example shows how to restore workloads to Amazon EC2 with AmazonEC2 proxy appliance.  |  | | --- | | $backup = Get-VBRBackup -Name "MSExchange"  $restorepoint = Get-VBRRestorePoint -Name \*MSExchange02\* -Backup $backup  $account = Get-VBRAmazonAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c"  $region = Get-VBRAmazonEC2Region -Account $account -RegionType Global -Name "ap-northeast-1"  $config = New-VBRAmazonEC2DiskConfiguration -DiskName "Virtual Disk" -Include -DiskType GeneralPurposeSSD  $instance = Get-VBRAmazonEC2InstanceType -Region $region  $vpc = Get-VBRAmazonEC2VPC -Region $region  $sgroup = Get-VBRAmazonEC2SecurityGroup -VPC $vpc  $subnet = Get-VBRAmazonEC2Subnet -VPC $vpc -AvailabilityZone eu-west-1a  $proxy = New-VBRAmazonEC2ProxyAppliance -InstanceType $instance -Subnet $subnet -SecurityGroup $sgroup -RedirectorPort 443  Start-VBRVMRestoreToAmazon -RestorePoint $restorepoint -Region $region -LicenseType ProvidedByAWS -InstanceType $instance -VMName "Restored VM" -DiskConfiguration $config -VPC $vpc -SecurityGroup $sgroup -Subnet $subnet -ProxyAppliance $proxy -Reason "Data recovery" |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable. 3. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable. 4. Run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. Set the $account variable as the Account parameter value. Set the Global value as the RegionType parameter value. Specify the Name parameter value. Save the result to the $region variable. 5. Run the [New-VBRAmazonEC2DiskConfiguration](new-vbramazonec2diskconfiguration.md) cmdlet. Specify the DiskName parameter value. Provide the Include parameter. Set the GeneralPurposeSSD value as the DiskType parameter value. Save the result to the $config variable. 6. Run the [Get-VBRAmazonEC2InstanceType](get-vbramazonec2instancetype.md) cmdlet. Set the $region variable as the Region parameter value. Save the result to the $instance variable. 7. Run the [Get-VBRAmazonEC2VPC](get-vbramazonec2vpc.md) cmdlet. Set the $region variable as the Region parameter value. Save the result to the $vpc variable. 8. Run the [Get-VBRAmazonEC2SecurityGroup](get-vbramazonec2securitygroup.md) cmdlet. Set the $vpc variable as the VPC parameter value. Save the result to the $sgroup variable. 9. Run the [Get-VBRAmazonEC2Subnet](get-vbramazonec2subnet.md) cmdlet. Set the $vpc variable as the VPC parameter value. Specify the AvailabilityZone parameter value. Save the result to the $subnet variable. 10. Run the [New-VBRAmazonEC2ProxyAppliance](new-vbramazonec2proxyappliance.md) cmdlet. Set the $instance variable as the InstanceType parameter value. Set the $subnet variable as the Subnet parameter value. Set the $sgroup variable as the SecurityGroup parameter value. Specify the RedirectorPort parameter value. Save the result to the $proxy variable. 11. Run the Start-VBRVMRestoreToAmazon cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Set the $region variable as the Region parameter value. * Set the ProvidedByAWS value as the LicenseType parameter value. * Set the $instance variable as the InstanceType parameter value. * Specify the VMName parameter value. * Set the $config variable as the DiskConfiguration parameter value. * Set the $vpc variable as the VPC parameter value. * Set the $sgroup variable as the SecurityGroup parameter value. * Set the $subnet variable as the Subnet parameter value. * Set the $proxy variable as the ProxyAppliance parameter value. * Specify the Reason parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Restoring Backups Created by Veeam Agent for Microsoft Windows to Amazon EC2

|  |  |
| --- | --- |
| This example shows how to restore backups of computers created by Veeam Agent for Microsoft Windows to Amazon EC2.  |  | | --- | | $winbackup = Get-VBRBackup -Name "WinBackup\*"  $restorepoint = Get-VBRRestorePoint -Backup $winbackup  $disk = Get-VBRComputerDisk -RestorePoint $restorepoint[1]  $account = Get-VBRAmazonAccount -Id '6c4746ba-5422-4649-ac20-5d29939eda1a'  $region = Get-VBRAmazonEC2Region -Account $account -RegionType Global -Name 'eu-west-2'  $instance = Get-VBRAmazonEC2InstanceType -Region $region -Name 'c4.large'  $config = New-VBRAmazonEC2DiskConfiguration -DiskName $disk.UniqueId -DiskType GeneralPurposeSSD -Include  $vpc = Get-VBRAmazonEC2VPC -Region $region  $subnet = Get-VBRAmazonEC2Subnet -VPC $vpc[0]  $sgroup = Get-VBRAmazonEC2SecurityGroup -VPC $vpc[0]  Start-VBRVMRestoreToAmazon -RestorePoint $restorepoint[1] -Region $region -LicenseType ProvidedByAWS -InstanceType $instance -VMName 'agent-restored' -DiskConfiguration $config -VPC $vpc -Subnet $subnet[0] -SecurityGroup $sgroup -Reason 'test' |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $winbackup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $winbackup variable as the Backup parameter value. Save the result to the $restorepoint variable. 3. Run the [Get-VBRComputerDisk](get-vbrcomputerdisk.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $disk variable.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the second restore point is used.   1. Run the [Get-VBRAmazonAccount](get-vbramazonaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable. 2. Run the [Get-VBRAmazonEC2Region](get-vbramazonec2region.md) cmdlet. Set the $account variable as the Account parameter value. Set the Global value as the RegionType parameter value. Specify the Name parameter value. Save the result to the $region variable. 3. Run the [Get-VBRAmazonEC2InstanceType](get-vbramazonec2instancetype.md) cmdlet. Set the $region variable as the Region parameter value. Save the result to the $instance variable. 4. Run the [New-VBRAmazonEC2DiskConfiguration](new-vbramazonec2diskconfiguration.md) cmdlet. Set the UniqueId parameter of the $disk variable as the DiskName parameter value. Set the GeneralPurposeSSD value as the DiskType parameter value. Provide the Include parameter. Save the result to the $config variable. 5. Run the [Get-VBRAmazonEC2VPC](get-vbramazonec2vpc.md) cmdlet. Set the $region variable as the Region parameter value. Save the result to the $vpc variable.   The Get-VBRAmazonEC2VPC cmdlet will return an array of VPCs. Consider that the array numbering starts with 0. In our example, the first VPC will be used.   1. Run the [Get-VBRAmazonEC2Subnet](get-vbramazonec2subnet.md) cmdlet. Set the $vpc variable as the VPC parameter value. Save the result to the $subnet variable. 2. Run the [Get-VBRAmazonEC2SecurityGroup](get-vbramazonec2securitygroup.md) cmdlet. Set the $vpc variable as the VPC parameter value. Save the result to the $sgroup variable. 3. Run the Start-VBRVMRestoreToAmazon cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Set the $region variable as the Region parameter value. * Set the ProvidedByAWS value as the LicenseType parameter value. * Set the $instance variable as the InstanceType parameter value. * Specify the VMName parameter value. * Set the $config variable as the DiskConfiguration parameter value. * Set the $vpc variable as the VPC parameter value. * Set the $sgroup variable as the SecurityGroup parameter value. * Set the $subnet variable as the Subnet parameter value. * Set the $sgroup variable as the SecurityGroup parameter value. * Specify the Reason parameter value. |

Related Commands

* [Get-VBRAmazonAccount](get-vbramazonaccount.md)
* [Get-VBRAmazonEC2Region](get-vbramazonec2region.md)
* [New-VBRAmazonEC2DiskConfiguration](new-vbramazonec2diskconfiguration.md)
* [Get-VBRAmazonEC2InstanceType](get-vbramazonec2instancetype.md)
* [Get-VBRAmazonEC2VPC](get-vbramazonec2vpc.md)
* [Get-VBRAmazonEC2SecurityGroup](get-vbramazonec2securitygroup.md)
* [Get-VBRAmazonEC2Subnet](get-vbramazonec2subnet.md)
* [New-VBRAmazonEC2ProxyAppliance](new-vbramazonec2proxyappliance.md)


