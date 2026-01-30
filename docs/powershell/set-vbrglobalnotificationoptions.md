---
title: "Set-VBRGlobalNotificationOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrglobalnotificationoptions.html"
last_updated: "4/3/2024"
product_version: "13.0.1.1071"
---

# Set-VBRGlobalNotificationOptions


Short Description

Modifies global notification settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRGlobalNotificationOptions [-StorageSpaceThresholdEnabled] [-StorageSpaceThreshold <int>] [-DatastoreSpaceThresholdEnabled] [-DatastoreSpaceThreshold <int>] [-SkipVMSpaceThresholdEnabled] [-SkipVMSpaceThreshold <int>] [-NotifyOnSupportExpiration] [-NotifyOnUpdates] [<CommonParameters>] |

Detailed Description

This cmdlet modifies global notification settings.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| StorageSpaceThresholdEnabled | Defines that Veeam Backup & Replication will display a warning message in the job session details when the disk space in the target backup repository is below a specific value.  To specify a disk space threshold provide the  StorageSpaceThreshold parameter.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| StorageSpaceThreshold | Specifies a disk space threshold for backup repositories in percent.  Default: 10. | Int | False | Named | False |
| DatastoreSpaceThresholdEnabled | Defines that Veeam Backup & Replication will display a warning message in the job session details when the disk space in a production datastore is below a specific value.  To specify a disk space threshold for a production datastore provide the DatastoreSpaceThreshold parameter.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| DatastoreSpaceThreshold | Specifies a disk space threshold for production datastore in percent.  Default: 10. | Int | False | Named | False |
| SkipVMSpaceThresholdEnabled | Defines that Veeam Backup & Replication will stop backup jobs that work with production datastores before VM snapshots are taken if free disk space in this datastore is below the specified threshold.  To specify a disk space threshold for a production datastore provide the DatastoreSpaceThreshold parameter.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| SkipVMSpaceThreshold | Specifies a disk space threshold for production datastore in percent.  Default: 5. | Int | False | Named | False |
| NotifyOnSupportExpiration | Defines that Veeam Backup & Replication will notify about the support expiration date in every email notification.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| NotifyOnUpdates | Defines that Veeam Backup & Replication will notify about new product versions and patches available on the Veeam website.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGlobalNotificationOptions](vbrglobalnotificationoptions.md)

Examples

Modifying Target Backup Repository Disk Space Threshold

This command sets the disk space threshold of the target backup repository to 15 percent.

|  |
| --- |
| Set-VBRGlobalNotificationOptions -StorageSpaceThreshold 15 -StorageSpaceThresholdEnabled:$False  StorageSpaceThresholdEnabled   : True  StorageSpaceThreshold          : 15  DatastoreSpaceThresholdEnabled : True  DatastoreSpaceThreshold        : 10  SkipVMSpaceThresholdEnabled    : True  SkipVMSpaceThreshold           : 5  NotifyOnSupportExpiration      : True  NotifyOnUpdates                : True |

Related Commands

[Get-VBRGlobalNotificationOptions](get-vbrglobalnotificationoptions.md)


