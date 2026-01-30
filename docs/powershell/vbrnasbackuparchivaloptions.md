---
title: "VBRNASBackupArchivalOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrnasbackuparchivaloptions.html"
last_updated: "1/19/2024"
product_version: "13.0.1.1071"
---

# VBRNASBackupArchivalOptions


Contains retention policy for file versions and settings of files and folders that will be added to the file backup job.

Properties

| Property | Type | Description |
| --- | --- | --- |
| ActiveFileVersionRetentionEnabled | Bool | Defines if the file version retention policy is enabled:   * True - Enabled * False - Disabled |
| ActiveFileVersionRetention | Int32 | Time period for the file version retention policy for existing files. |
| DeletedFileVersionRetentionEnabled | Bool | Defines if the file version retention policy is enabled for deleted versions of files:   * True - Enabled * False - Disabled |
| DeletedFileVersionRetention | Int32 | Time period for the file version retention policy for deleted versions of files. |
| ArchivalType | VBRNASBackupArchivalType | Filter settings for file versions that must be kept on the long-term repository. |
| InclussionMask | String[] | File mask for files and folders that you want to add to the file backup job. |
| ExclussionMask | String[] | File mask for files and folders that you do not want to add to the file backup job. |

Related Commands

* [New-VBRNASBackupArchivalOptions](new-vbrnasbackuparchivaloptions.md)
* [Set-VBRNASBackupArchivalOptions](set-vbrnasbackuparchivaloptions.md)


