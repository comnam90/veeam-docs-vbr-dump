---
title: "Set-VBRUnstructuredBackupVersionRetentionOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrunstructuredbackupversionretentionoptions.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Set-VBRUnstructuredBackupVersionRetentionOptions


Short Description

Modifies version-based retention policy settings for file backup jobs and object storage backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRUnstructuredBackupVersionRetentionOptions -Options <VBRUnstructuredBackupVersionRetentionOptions> [-ActiveFileVersionRetention <Int32>] [-DeletedFileVersionRetention <Int32>] [-EnableActiveFileVersionRetention] [-EnableDeletedFileVersionRetention] [-VersionRetentionType {None | Archive | BackupAndArchive}]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies version-based retention policy settings for file backup jobs and object storage backup jobs. You can specify either a number of restore points to keep or the number of file versions to keep.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the retention policy for file versions. The cmdlet will modify the settings of this policy. | Accepts the VBRUnstructuredBackupVersionRetentionOptions object. To create this object, run the [New-VBRUnstructuredBackupVersionRetentionOptions](new-vbrunstructuredbackupversionretentionoptions.md) cmdlet. | True | Named | True |
| VersionRetentionType | Specifies to what repositories the version-based retention policy will be applied. You can specify either of the following filter settings:   * None: use this option if you do not want to apply the version-based retention policy either to the backup or archive repository. * Archive: use this option if you want to apply the version-based retention policy to the archive repository only. * BackupAndArchive: use this option if you want to apply the version-based retention policy both to the backup and archive repositories.   Note: If you do not specify this parameter, version-based retention policy settings are applied by default both to backup and archive repositories. | VBRUnstructuredBackupVersionRetentionType | False | Named | False |
| EnableActiveFileVersionRetention | Defines that the cmdlet will enable the version-based retention for active files. | SwitchParameter | False | Named | False |
| ActiveFileVersionRetention | Specifies the number of active file versions. Veeam Backup & Replication will keep the specified number of file versions for active (not deleted) files. Once the number of file versions exceeds, Veeam Backup & Replication will remove the oldest file version from the repository.  Note: If you do not specify this parameter, the number of file versions for active files is set to unlimited. Veeam Backup & Replication will delete file versions for active files from the backup repository after the specified retention period passes.  Default: 10. | Int32 | False | Named | False |
| EnableDeletedFileVersionRetention | Defines that the cmdlet will enable the version-based retention for deleted files. | SwitchParameter | False | Named | False |
| DeletedFileVersionRetention | Specifies the number of file versions for deleted files. Veeam Backup & Replication will keep the specified number of file versions for deleted files. Once the number of file versions exceeds, Veeam Backup & Replication will remove the oldest version from the repository.  Note: If you do not specify this parameter, the number of file versions for deleted files is set to unlimited. Veeam Backup & Replication will remove files versions for deleted files from the backup repository after the specified retention period passes.  Default: 3. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUnstructuredBackupVersionRetentionOptions object that contains version-based retention settings that will be added to the file backup job and object storage backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Retention Policy for File Versions of Active Files in Archive Repository

|  |  |
| --- | --- |
| This command shows how to modify retention policy for file versions of active files. Only the archive repository will keep use version-based retention, and will keep the last 14 versions of active files.  |  | | --- | | $new\_version\_retention\_options = New-VBRUnstructuredBackupVersionRetentionOptions -VersionRetentionType  Set-VBRUnstructuredBackupVersionRetentionOptions -Options $new\_version\_retention\_options -VersionRetentionType Archive -EnableActiveFileVersionRetention -ActiveFileVersionRetention 14 |  Perform the following steps:   1. Run the [New-VBRUnstructuredBackupVersionRetentionOptions](new-vbrunstructuredbackupversionretentionoptions.md) cmdlet. Use default settings. Save the result to the $new\_version\_retention\_options variable. 2. Run the Set-VBRUnstructuredBackupVersionRetentionOptions cmdlet. Specify the following settings:  * Set the $new\_version\_retention\_options variable as the Options parameter value. * Set the Archive option for the VersionRetentionType parameter. * Provide the EnableActiveFileVersionRetention parameter. * Set the ActiveFileVersionRetention parameter to 14. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Retention Policy for File Versions of Active and Deleted Files in Backup and Archive Repositories

|  |  |
| --- | --- |
| This command shows how to enable the version-based retention settings for active files and it for deleted files. The version-based retention settings applies to the backup and archive repository and they will keep file versions of active files for 21 days and deleted files for 7 days.  |  | | --- | | $new\_version\_retention\_options = New-VBRUnstructuredBackupVersionRetentionOptions -VersionRetentionType  Set-VBRUnstructuredBackupVersionRetentionOptions -Options $new\_version\_retention\_options -VersionRetentionType BackupAndArchive -EnableActiveFileVersionRetention -ActiveFileVersionRetention 21 -EnableDeletedFileVersionRetention -DeletedFileVersionRetention 7 |  Perform the following steps:   1. Run the [New-VBRUnstructuredBackupVersionRetentionOptions](new-vbrunstructuredbackupversionretentionoptions.md) cmdlet. Use default settings. Save the result to the $new\_version\_retention\_options variable. 2. Run the Set-VBRUnstructuredBackupVersionRetentionOptions cmdlet. Specify the following settings:  * Set the $new\_version\_retention\_options variable as the Options parameter value. * Set the BackupAndArchive option for the VersionRetentionType parameter. * Provide the EnableActiveFileVersionRetention parameter. * Set the ActiveFileVersionRetention parameter to 21. * Provide the EnableDeletedFileVersionRetention parameter. * Set the DeletedFileVersionRetention parameter to 7. |

Related Commands

[New-VBRUnstructuredBackupVersionRetentionOptions](new-vbrunstructuredbackupversionretentionoptions.md)


