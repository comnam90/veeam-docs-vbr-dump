---
title: "Start-VBRZip"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrzip.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Start-VBRZip

In this article

Short Description

Performs VeeamZIP on the selected VM.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Target VeeamZIP backups to a backup repository.

|  |
| --- |
| Start-VBRZip -Entity <IItem[]> [-BackupRepository <CBackupRepository>] [-Compression <int>] [-DisableQuiesce] [-RunAsync] [-EncryptionKey <PSCryptoKey>]  [-KMSServer <VBRKMSServer>] [-AutoDelete <EFreeBackupRetention> {Never | Tonight | TomorrowNight | In3days | In1Week | In2Weeks | In1Month | In3Months | In6Months | In1Year}] [-RetentionNumber <Int32>] [-RetentionPeriodType <VBRRetentionPeriodType>] [-Force]  [<CommonParameters>] |

* Target VeeamZIP backups to a folder or for Veeam Backup Free Edition.

|  |
| --- |
| Start-VBRZip -Entity <IItem[]> [-Folder <string>] [-Compression <int>] [-DisableQuiesce] [-RunAsync] [-EncryptionKey <PSCryptoKey>]  [-KMSServer <VBRKMSServer>] [-AutoDelete <EFreeBackupRetention> {Never | Tonight | TomorrowNight | In3days | In1Week | In2Weeks | In1Month | In3Months | In6Months | In1Year}] [-RetentionNumber <Int32>] [-RetentionPeriodType <VBRRetentionPeriodType>] [-NetworkCredentials <CCredentials>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet performs VeeamZIP backup of the selected VM.

VeeamZIP is a quick backup procedure always producing a full backup. The VeeamZIP task runs once the time it is created and does not appear in the jobs list. The result backup file is stored in the specified folder and does not appear automatically in the backups list. Run the [Import-VBRBackup](import-vbrbackup.md) cmdlet to start managing the backup file with Veeam Backup & Replication.

This cmdlet is available for Veeam Backup Free Edition. You can use it in your scripts. For Veeam Backup Free Edition, use the second parameter set.

|  |
| --- |
| Note: |
| The cmdlet will not run if the geographic location of the VMs you want to back up and the job target repository location do not match. If you still want to run the cmdlet, use the Force parameter. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| BackupRepository | Specifies the backup repository where you want to save the backup file. If none is specified, the default repository will be used.  Note: The cmdlet will not run if you do not specify either the BackupRepository or the Folder parameters. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| Entity | Specifies the array of VMs for which you want to create a VeeamZIP file. | Accepts the IItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | True (ByValue, |
| Compression | Specifies then integer number corresponding to the desired compression level:   * 0 = None. Consider disabling compression to achieve better deduplication ratios on deduplicating storage appliances at the cost of reduced backup performance. * 4 = Dedupe-friendly. This is the recommended setting for using with deduplicating storage devices and caching WAN accelerators. This setting is used by default. * 5 = Optimal (recommended). Optimal compression provides for the best compression to performance ratio, and lowest backup proxy CPU usage. * 6 = High. High compression provides additional 10% compression ratio over Optimal, at the cost of 8x higher CPU usage. * 9 = Extreme. Extreme compression provides additional 3% compression ratio over High, at the cost of 2x higher CPU usage. | Int32 | False | Named | False |
| DisableQuiesce | Defines that the cmdlet will back up VM without using the quiescence mechanisms.  If you provide this parameter, you will be able to create a crash-consistent backup of the target VM. Otherwise, the applications that run on the target VM will be quiesced to provide transactionally consistent backup. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Folder | Specifies the full path to the folder on the server where you want to store the created backup file. If omitted, the created backup file will be saved to the C:\backup folder on the Veeam Backup server.  Note: The cmdlet will not run if you do not specify either the BackupRepository or the Folder parameters. | String | False | Named | False |
| EncryptionKey | Specifies the encryption key you want to use to encrypt the created VeeamZIP file. | PSCryptoKey | False | Named | False |
| KMSServer | Specifies the KMS server you want to use to encrypt the data. | Accepts the VBRKMSServer object.  To get this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |
| AutoDelete | Specifies the retention settings for the created VeeamZIP file:   * Never * Tonight * TomorrowNight * In3days * In1Week * In2Weeks * In1Month * In3Months * In6Months * In1Year * In2Years * In3Years * In5Years * In7Years   Note: Use this parameter if the RetentionPeriodType and RetentionNumber parameters are not specified. | EFreeBackupRetention | False | Named | False |
| RetentionPeriodType | Specifies the type of the retention policy. You can set the following types:   * Days: use this option if you want Veeam Backup & Replication to apply retention policy daily. * Months: use this option if you want Veeam Backup & Replication to apply retention policy monthly. * Years: use this option if you want Veeam Backup & Replication to apply retention policy yearly.   Use the RetentionNumber to specify the number of days, months or years.  Note: Use this parameter if the AutoDelete parameter is not specified. | VBRRetentionPeriodType | False | Named | False |
| RetentionNumber | For the RetentionPeriodType option.  Specifies the period of time to keep the VeeamZIP backups. After this period finishes, Veeam Backup & Replication will remove data. | Int32 | False | Named | False |
| NetworkCredentials | Specifies the credentials you want to use for authenticating with the shared folder. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will perform backup even if the geographic location of VMs and the target backup repository location do not match. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Performing VeeamZIP Backup to Backup Repository

|  |  |
| --- | --- |
| This example shows how to perform VeeamZIP backup to a backup repository.  |  | | --- | | $vm = Find-VBRViEntity -Name "Fileserver01"  $rep = Get-VBRBackupRepository -Name "Reports"  Start-VBRZip -BackupRepository $rep -Entity $vm -RunAsync |  You will need to perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet to get the VM where VeeamZIP will be started. Specify the Name parameter value. Save the result to the $vm variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $rep variable. 3. Run the Start-VBRZip cmdlet. Set the $vm variable as the Entity parameter value. Set the $rep variables as the BackupRepository parameter value. Provide the RunAsync parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Performing VeeamZIP Backup to Shared Folder

|  |  |
| --- | --- |
| This example shows how to perform VeeamZIP backup to a shared folder. The cmdlet starts VeeamZIP with the following parameters:   * Path to the folder where the backups will be stored is D:\Repository\VeeamZIP. * The compression level is set to 4 (Dedupe-friendly). * The VMware quiescence is disabled. * The cmdlet will use Shared credentials for authenticating with the shared folder. * The RunAsync parameter is set to bring the process to the background.   |  | | --- | | $vm = Find-VBRViEntity -Name "Tech"  $netcreds = Get-VBRCredentials -Name "Shared"  Start-VBRZip -Folder "D:\Repository\VeeamZIP" -Entity $vm -Compression 4 -DisableQuiesce -NetworkCredentials $netcreds -RunAsync |  You will need to perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet to get the VM where VeeamZIP will be started. Specify the Name parameter value. Save the result to the $vm variable. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Name parameter value. Save the result to the $netcreds variable. 3. Run the Start-VBRZip cmdlet. Specify the following settings:  * Specify the Folder parmeter value. * Set the $vm variable as the Entity parameter value. * Set the 4 value as the Compression parameter value. * Provide the DisableQuiesce parameter. * Set the $netcreds variable as the NetworkCredentials parameter value. * Provide the RunAsync parameter. |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRCredentials](get-vbrcredentials.md)
* [Find-VBRViEntity](find-vbrvientity.md) / [Find-VBRHvEntity](find-vbrhventity.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
