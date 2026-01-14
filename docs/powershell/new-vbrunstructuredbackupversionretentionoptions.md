---
title: "New-VBRUnstructuredBackupVersionRetentionOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrunstructuredbackupversionretentionoptions.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# New-VBRUnstructuredBackupVersionRetentionOptions

In this article

Short Description

Defines version-based retention policy settings for file backup jobs and object storage backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRUnstructuredBackupVersionRetentionOptions [-VersionRetentionType {None | Archive | BackupAndArchive}] [-ActiveFileVersionRetention <int>] [-DeletedFileVersionRetention <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet defines version-based retention policy for file backup jobs and object storage backup jobs. You can specify either a number of restore points to keep or the number of file versions to keep.

|  |
| --- |
| Important |
| If you use retention options configured with the [New-VBRUnstructuredBackupArchivalOptions](new-vbrunstructuredbackuparchivaloptions.md) cmdlet, the settings configured with New-VBRUnstructuredBackupVersionRetentionOptions scripts may not work correctly. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| VersionRetentionType | Specifies to what repositories the version-based retention policy will be applied. You can specify one of the following filter settings:   * None: use this option if you do not want to apply the version-based retention policy either to the backup or archive repository. * Archive: use this option if you want to apply the version-based retention policy to the archive repository only. * BackupAndArchive: use this option if you want to apply the version-based retention policy both to the backup and archive repositories.   Note: If you do not specify this parameter, version-based retention policy settings are applied by default both to backup and archive repositories. | VBRUnstructuredBackupVersionRetentionType | False | Named | False |
| ActiveFileVersionRetention | Specifies the number of active file versions. Veeam Backup & Replication will keep the specified number of file versions for active (not deleted) files. Once the number of file versions exceeds, Veeam Backup & Replication will remove the oldest file version from the repository.  Note: If you do not specify this parameter, the number of file versions for active files is set to unlimited. Veeam Backup & Replication will delete file versions for active files from the backup repository after the specified retention period passes.  Default: 10. | Int32 | False | Named | False |
| DeletedFileVersionRetention | Specifies the number of file versions for deleted files. Veeam Backup & Replication will keep the specified number of file versions for deleted files. Once the number of file versions exceeds, Veeam Backup & Replication will remove the oldest version from the repository.  Note: If you do not specify this parameter, the number of file versions for deleted files is set to unlimited. Veeam Backup & Replication will remove files versions for deleted files from the backup repository after the specified retention period passes.  Default: 3. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUnstructuredBackupVersionRetentionOptions object that contains version-based retention settings for file backup job and object storage backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Retention Policy for File Versions of Active Files Both in Backup and Archive Repositories

|  |  |
| --- | --- |
| This command shows how to define retention policy for file versions of active files. The backup and archive repositories together will keep file versions of active files for 14 days.  |  | | --- | | New-VBRUnstructuredBackupVersionRetentionOptions -VersionRetentionType BackupAndArchive -ActiveFileVersionRetention 14 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Retention Policy for File Versions of Deleted Files in Archive Repository

|  |  |
| --- | --- |
| This command shows how to define retention policy for file versions of deleted files. The version-based retention settings applies to the archive repository only and it will keep file versions of deleted files for 7 days.  |  | | --- | | New-VBRUnstructuredBackupVersionRetentionOptions -VersionRetentionType Archive -DeletedFileVersionRetention 7 | |

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
