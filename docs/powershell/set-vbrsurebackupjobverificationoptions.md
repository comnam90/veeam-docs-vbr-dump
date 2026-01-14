---
title: "Set-VBRSureBackupJobVerificationOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrsurebackupjobverificationoptions.html"
last_updated: "12/10/2024"
product_version: "13.0.1.1071"
---

# Set-VBRSureBackupJobVerificationOptions

In this article

Short Description

Modifies additional settings for the SureBackup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRSureBackupJobVerificationOptions -VerificationOptions <VBRSureBackupJobVerificationOptions> [-EnableDiskContentValidation] [-DisableApplicationGroupValidation] [-EnableMalwareScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireImageScan][-DisableApplicationGroupMalwareScan] [-EnableSNMPNotification] [-EnableEmailNotification] [-Address <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies additional settings for the SureBackup job.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| VerificationOptions | Specifies additional settings for the SureBackup job. The cmdlet will modify these settings. | Accepts the VBRSureBackupJobVerificationOptions object. To create this object, run the [New-VBRSureBackupJobVerificationOptions](new-vbrsurebackupjobverificationoptions.md) cmdlet. | True | Named | False |
| EnableDiskContentValidation | Defines that Veeam Backup & Replication will validate backup files of VMs with a CRC check to make sure that the file is not corrupted.  If you do not provide this parameter, Veeam Backup & Replication will not apply the CRC check to backup files.  Default: False. | SwitchParamter | False | Named | False |
| DisableApplicationGroupValidation | Defines that Veeam Backup & Replication will not apply the CRC test to backup files of VMs from an application group.  If you want to apply CRC test to backup files of VMs from application groups, provide the :$false value for the parameter.  Default: True. | SwitchParamter | False | Named | False |
| EnableMalwareScan | Defines that Veeam Backup & Replication will scan VMs with antivirus software.  If you do not specify this parameter, Veeam Backup & Replication will not scan VMs with antivirus software.  Default: False. | SwitchParamter | False | Named | False |
| EnableYARAScan | Defines that Veeam Backup & Replication will scan VMs with the specified YARA rule.  If you do not provide this parameter, Veeam Backup & Replication will not scan VMs with the YARA rule.  Use the YARAScanRule parameter to specify the YARA rule.  Default: False. | SwitchParamter | False | Named | False |
| YARAScanRule | Specifies the YARA rule. Veeam Backup & Replication will scan VMs with this rule.  Veeam Backup & Replication searches for YARA rules in the YaraRules folder. The default path is: C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules.  To use a YARA rule, you must specify its name and extension. Veeam Backup & Replication accepts only .yar and .yara extensions. | String | False | Named | False |
| EnableEntireImageScan | For the antivirus scan option.  Defines that the antivirus software will continue scanning VMs after the first malware is found.  If you do not provide this parameter, the antivirus software will stop scanning VMs after the first malware is found.  Default: False. | SwitchParamter | False | Named | False |
| DisableApplicationGroupMalwareScan | Defines that Veeam Backup & Replication will not perform an antivirus scan of VMs from an application group and will scan VMs from linked jobs only.  If you want to perform an antivirus scan of VMs from an application group, provide the :$false value for the parameter.  Default: True. | SwitchParamter | False | Named | False |
| EnableSNMPNotification | Defines that Veeam Backup & Replication will send SNMP traps.  If you do not provide this parameter, SNMP traps will not be sent.  Default: False. | SwitchParamter | False | Named | False |
| EnableEmailNotification | Defines that Veeam Backup & Replication will send email notifications on the job state.  If you do not provide this parameter, email notifications will not be sent.  Default: False. | SwitchParamter | False | Named | False |
| Address | Specifies an array of email addresses. Veeam Backup & Replication will send notifications to these email addresses. | String[] | False | Named | False |
| NotifyOnError | Defines that Veeam Backup & Replication will send email notifications on error.  If you do not provide the EnableEmailNotification parameter, email notifications will not be sent.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParamter | False | Named | False |
| NotifyOnSuccess | Defines that Veeam Backup & Replication will send email notifications on success.  If you do not provide the EnableEmailNotification parameter, email notifications will not be sent.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParamter | False | Named | False |
| NotifyOnWarning | Defines that Veeam Backup & Replication will send email notifications on warning.  If you do not provide the EnableEmailNotification parameter, email notifications will not be sent.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParamter | False | Named | False |
| Subject | Specifies the email subject. | String | False | Named | False |
| UseCustomEmailSettings | Defines that Veeam Backup & Replication will use custom settings email instead of global email settings.  If you do not provide this parameter, global email settings will be used.  Default: False. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSureBackupJobVerificationOptions object that defines additional settings for the SureBackup job.

Examples

Modifying Email Notifications Address

This example shows how to modify the emall notification address for the SureBackup job. Veeam Backup & Replication will send email notifications to the administrator@tech.com and tech@tech.com email addresses.

|  |
| --- |
| $options = New-VBRSureBackupJobVerificationOptions -EnableEmailNotification -Address "administrator@tech.com"  Set-VBRSureBackupJobVerificationOptions -VerificationOptions $options -Address "administrator@tech.com, tech@tech.com" |

Perform the following steps:

1. Run the [New-VBRSureBackupJobVerificationOptions](new-vbrsurebackupjobverificationoptions.md) cmdlet. Provide the EnableEmailNotification parameter. Specify the Address parameter value. Save the result to the $options variable.
2. Run the Set-VBRSureBackupJobVerificationOptions cmdlet. Set the $options variable as the VerificationOptions parameter value. Specify the Address parameter value.

Related Commands

[New-VBRSureBackupJobVerificationOptions](new-vbrsurebackupjobverificationoptions.md)

Page updated 12/10/2024

Page content applies to build 13.0.1.1071
