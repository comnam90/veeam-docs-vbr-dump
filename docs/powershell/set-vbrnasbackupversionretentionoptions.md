---
title: "Set-VBRNASBackupVersionRetentionOptions (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrnasbackupversionretentionoptions.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Set-VBRNASBackupVersionRetentionOptions (obsolete)

In this article

Short Description

Modifies version-based retention policy settings that will be applied for the file backup job.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Set-VBRUnstructuredBackupVersionRetentionOptions](set-vbrunstructuredbackupversionretentionoptions.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRNASBackupVersionRetentionOptions -Options <VBRNASBackupVersionRetentionOptions> [-VersionRetentionType {None | Archive | BackupAndArchive}] [-EnableActiveFileVersionRetention] [-ActiveFileVersionRetention <int>] [-EnableDeletedFileVersionRetention] [-DeletedFileVersionRetention <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies version-based retention policy settings that will be applied for the file backup job.

For file backups, Veeam Backup & Replication allows defining retention settings not only as the number of restore points to keep, but also as the number of file versions to keep.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the retention policy for file versions. The cmdlet will modify the settings of this policy. | Accepts the VBRNASBackupVersionRetentionOptions object. To create this object, run the [New-VBRNASBackupVersionRetentionOptions](new-vbrnasbackupversionretentionoptions.md) cmdlet. | True | Named | True |
| VersionRetentionType | Specifies to what repositories the version-based retention policy will be applied. You can specify either of the following filter settings:   * None: use this option if you do not want to apply the version-based retention policy either to the backup or archive repository. * Archive: use this option if you want to apply the version-based retention policy to the archive repository only. * BackupAndArchive: use this option if you want to apply the version-based retention policy both to the backup and archive repositories.   Note: If you do not specify this parameter, version-based retention policy settings are applied by default both to backup and archive repositories. | VBRNASBackupVersionRetentionType | False | Named | False |
| EnableActiveFileVersionRetention | Defines that the cmdlet will enable the version-based retention for active files. | SwitchParameter | False | Named | False |
| ActiveFileVersionRetention | Specifies the number of active file versions. Veeam Backup & Replication will keep the specified number of file versions for active (not deleted) files. Once the number of file versions exceeds, Veeam Backup & Replication will remove the oldest file version from the repository.  Note: If you do not specify this parameter, the number of file versions for active files is set to unlimited. Veeam Backup & Replication will delete file versions for active files from the backup repository after the specified retention period passes.  Default: 10 | Int32 | False | Named | False |
| EnableDeletedFileVersionRetention | Defines that the cmdlet will enable the version-based retention for deleted files. | SwitchParameter | False | Named | False |
| DeletedFileVersionRetention | Specifies the number of file versions for deleted files. Veeam Backup & Replication will keep the specified number of file versions for deleted files. Once the number of file versions exceeds, Veeam Backup & Replication will remove the oldest version from the repository.  Note: If you do not specify this parameter, the number of file versions for deleted files is set to unlimited. Veeam Backup & Replication will remove files versions for deleted files from the backup repository after the specified retention period passes.  Default: 3 | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASBackupVersionRetentionOptions object that contains version-based retention settings that will be added to the file backup job.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Retention Policy for File Versions of Active Files in Archive Repository

|  |  |
| --- | --- |
| This example shows how to modify retention policy for file versions of active files. Only the archive repository will keep use version-based retention, and will keep the last 14 versions of active files.  |  | | --- | | $version\_retention\_options = New-VBRNASBackupVersionRetentionOptions -VersionRetentionType  $new\_version\_retention\_options = Set-VBRNASBackupVersionRetentionOptions -Options $version\_retention\_options -VersionRetentionType Archive -EnableActiveFileVersionRetention -ActiveFileVersionRetention 14 |  Perform the following steps:   1. Run the [New-VBRNASBackupVersionRetentionOptions](new-vbrnasbackupversionretentionoptions.md) cmdlet. Use default settings. Save the result to the $version\_retention\_options variable. 2. Run the Set-VBRNASBackupVersionRetentionOptions cmdlet. Specify the following settings:  * Set the $new\_version\_retention\_options variable as the Options parameter value. * Set the VersionRetentionType parameter to the Archive value. * Specify the EnableActiveFileVersionRetention parameter value. * Set the ActiveFileVersionRetention parameter to the 14 value. * Save the result to the $new\_version\_retention\_options variable to be used with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Retention Policy for File Versions of Active and Deleted Files in Backup and Archive Repositories

|  |  |
| --- | --- |
| This example shows how to enable the version-based retention settings for active files and it for deleted files. The version-based retention settings applies to the backup and archive repository and they will keep file versions of active files for 21 days and deleted files for 7 days.  |  | | --- | | $version\_retention\_options = New-VBRNASBackupVersionRetentionOptions -VersionRetentionType  $new\_version\_retention\_options = Set-VBRNASBackupVersionRetentionOptions -Options $version\_retention\_options -VersionRetentionType BackupAndArchive -EnableActiveFileVersionRetention -ActiveFileVersionRetention 21 -EnableDeletedFileVersionRetention -DeletedFileVersionRetention 7 |  Perform the following steps:   1. Run the [New-VBRNASBackupVersionRetentionOptions](new-vbrnasbackupversionretentionoptions.md) cmdlet. Use default settings. Save the result to the $version\_retention\_options variable. 2. Run the Set-VBRNASBackupVersionRetentionOptions cmdlet. Specify the following settings:  * Set the $new\_version\_retention\_options variable as the Options parameter value. * Set the VersionRetentionType parameter to the BackupAndArchive value. * Specify the EnableActiveFileVersionRetention parameter value. * Set the ActiveFileVersionRetention parameter to the 21 value. * Specify the EnableDeletedFileVersionRetention parameter value. * Set the DeletedFileVersionRetention parameter to the 7 value.  * Save the result to the $new\_version\_retention\_options variable to be used with other cmdlets. |

Page updated 1/6/2025

Page content applies to build 13.0.1.1071
