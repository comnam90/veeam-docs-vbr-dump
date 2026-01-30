---
title: "New-VBRSureBackupJobVerificationOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrsurebackupjobverificationoptions.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# New-VBRSureBackupJobVerificationOptions


Short Description

Defines verification settings for the SureBackup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRSureBackupJobVerificationOptions [-EnableDiskContentValidation] [-DisableApplicationGroupValidation] [-EnableMalwareScan] [-EnableYARAScan] [-YARAScanRule <String>] [-EnableEntireImageScan] [-DisableApplicationGroupMalwareScan] [-EnableSNMPNotification] [-Address <String[]>] [-EnableEmailNotification] [-UseCustomEmailSettings] [-Subject <String>] [-NotifyOnSuccess] [-NotifyOnWarning] [-NotifyOnError]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRSureBackupJobVerificationOptions object. This object defines the following settings for the SureBackup job:

* Backup file integrity scan
* Malware scan
* Notifications

|  |
| --- |
| Important! |
| Veeam Backup & Replication will send email notifications and SNMP notifications only in case these options are set up in the Veeam Backup & Replication general settings. Note that you cannot enable email notifications and SNMP notifications with Veeam PowerShell.  For more information on configuring notification, see the [Specifying Email Notification Settings](https://helpcenter.veeam.com/docs/vbr/userguide/email_notification_settings.html?ver=13) section of the User Guide for VMware vSphere.  For more information on configuring SNMP notifications, see the [Specifying SNMP Settings](https://helpcenter.veeam.com/docs/vbr/userguide/snmp_settings.html?ver=13) section of the User Guide for VMware vSphere. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| EnableDiskContentValidation | Defines that Veeam Backup & Replication will validate backup files of VMs with a CRC check to make sure that the file is not corrupted.  If you do not provide this parameter, Veeam Backup & Replication will not apply the CRC check to backup files.  Default: False. | SwitchParamter | False | Named | False |
| DisableApplicationGroupValidation | Defines that Veeam Backup & Replication will not apply the CRC test to backup files of VMs from an application group.  If you want to apply CRC test to backup files of VMs from application groups, provide the :$False value for the parameter.  Default: True. | SwitchParamter | False | Named | False |
| EnableMalwareScan | Defines that Veeam Backup & Replication will scan VMs with antivirus software.  If you do not specify this parameter, Veeam Backup & Replication will not scan VMs with antivirus software.  Default: False. | SwitchParamter | False | Named | False |
| EnableYARAScan | Defines that Veeam Backup & Replication will scan VMs with the specified YARA rule.  If you do not provide this parameter, Veeam Backup & Replication will not scan VMs with the YARA rule.  Use the YARAScanRule parameter to specify the YARA rule.  Default: False. | SwitchParamter | False | Named | False |
| YARAScanRule | Specifies the YARA rule. Veeam Backup & Replication will scan VMs with this rule.  Veeam Backup & Replication searches for YARA rules in the YaraRules folder. The default path is: C:\Program Files\Veeam\Backup and Replication\Backup\YaraRules.  To use a YARA rule, you must specify its name and extension. Veeam Backup & Replication accepts only .yar and .yara extensions. | String | False | Named | False |
| EnableEntireImageScan | For the antivirus scan option.  Defines that the antivirus software will continue scanning VMs after the first malware is found.  If you do not provide this parameter, the antivirus software will stop scanning VMs after the first malware is found.  Default: False. | SwitchParamter | False | Named | False |
| DisableApplicationGroupMalwareScan | Defines that Veeam Backup & Replication will not perform an antivirus scan of VMs from an application group and will scan VMs from linked jobs only.  If you want to perform an antivirus scan of VMs from an application group, provide the :$False value for the parameter.  Default: True. | SwitchParamter | False | Named | False |
| EnableSNMPNotification | Defines that Veeam Backup & Replication will send SNMP traps.  If you do not provide this parameter, SNMP traps will not be sent.  Default: False. | SwitchParamter | False | Named | False |
| EnableEmailNotification | Defines that Veeam Backup & Replication will send email notifications on the job state.  If you do not provide this parameter, email notifications will not be sent.  Default: False. | SwitchParamter | False | Named | False |
| Address | Specifies an array of email addresses. Veeam Backup & Replication will send notifications to these email addresses. | String[] | False | Named | False |
| NotifyOnError | Defines that Veeam Backup & Replication will send email notifications on error.  If you do not provide the EnableEmailNotification parameter, email notifications will not be sent.  Default: True. | SwitchParamter | False | Named | False |
| NotifyOnSuccess | Defines that Veeam Backup & Replication will send email notifications on success.  If you do not provide the EnableEmailNotification parameter, email notifications will not be sent.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParamter | False | Named | False |
| NotifyOnWarning | Defines that Veeam Backup & Replication will send email notifications on warning.  If you do not provide the EnableEmailNotification parameter, email notifications will not be sent.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParamter | False | Named | False |
| Subject | Specifies the email subject. | String | False | Named | False |
| UseCustomEmailSettings | Defines that Veeam Backup & Replication will use custom settings email instead of global email settings.  If you do not provide this parameter, global email settings will be used.  Default: False. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSureBackupJobVerificationOptions object that defines additional settings for the SureBackup job.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Backup Files Validation Option

|  |  |
| --- | --- |
| This command defines the validation of backup files of VMs with a CRC check. Veeam Backup & Replication will not include VMs from application groups to the CRC check.  |  | | --- | | New-VBRSureBackupJobVerificationOptions -EnableDiskContentValidation | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Antivirus and YARA Scan Options

|  |  |
| --- | --- |
| This command enables an antivirus and YARA scan of VMs from application groups and linked jobs. Veeam Backup & Replication will scan VMs with the YARA rule named Rule.yara.  |  | | --- | | New-VBRSureBackupJobVerificationOptions -EnableMalwareScan -EnableEntireImageScan -EnableYARAScan -YARAScanRule "Rule.yara" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Defining Notifications Options

|  |  |
| --- | --- |
| This command enables the notifications option. Veeam Backup & Replication will send email notifications on the error and success job states to the administrator@tech.com email address with Job State subject.  |  | | --- | | New-VBRSureBackupJobVerificationOptions -EnableEmailNotification -Address "administrator@tech.com" -NotifyOnError -NotifyOnSuccess -Subject "Job State" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Enabling CRC Tests for Backups Files of VMs from Application Group

|  |  |
| --- | --- |
| This command defines the validation of backup files of VMs with a CRC check and enables CRC tests to backup files of VMs from application groups.  |  | | --- | | New-VBRSureBackupJobVerificationOptions -EnableDiskContentValidation -DisableApplicationGroupValidation:$False | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Enabling Antivirus Scan of VMs for Application Groups

|  |  |
| --- | --- |
| This command defines the validation of backup files of VMs with a CRC check and enables antivirus scan of VMs from an application group.  |  | | --- | | New-VBRSureBackupJobVerificationOptions -EnableDiskContentValidation -DisableApplicationGroupMalwareScan:$False | |


