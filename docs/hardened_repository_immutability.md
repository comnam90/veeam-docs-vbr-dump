---
title: "How Immutability Works"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/hardened_repository_immutability.html"
last_updated: "10/17/2025"
product_version: "13.0.1.1071"
---

# How Immutability Works

In this article

Immutability is managed by the following services:

* The Veeam Data Mover Service/Veeam Transport Service (veeamtransport). It communicates with the backup server, gets information about the immutability time period, and forwards it to the Veeam Immutability Service that manages immutability attributes. The service uses port 6162 and runs as a non-root user.
* The Veeam Immutability Service (veeamimmureposvc). It checks file immutability attributes every 20 minutes, calculates the time until a file needs to be immutable, and sets or removes the immutable attribute. The service runs with root permissions as a child process of the Veeam Data Mover Service.

These services are deployed and updated by the Veeam Installer Service for Linux (veeamdeploymentsvc). For more information on how the service works, see [Veeam Installer Service](installer_service.md).

Timeshift Detection

The Veeam Immutability Service also performs timeshift detection. The mechanism works in the following way:

1. After the Veeam Immutability Service starts, it creates the /etc/veeam/immureposvc/timeLog file. The file is updated every 10 minutes and contains the following information:

* systemTime — current UTC value (Unix timestamp)
* moveTime — timeshift value based on comparison between two metrics:

* difference between current and previous UTC values
* the value of the check interval (in seconds)

For example, the value of the check interval is 600 seconds (10 minutes). The previous UTC value is 1699367670, the current UTC value is 1699368270. The difference between current and previous UTC values also equals 600 seconds. As two metrics have the same value, the current value of the moveTime parameter will not change.

* hwTime — current RTC value (Unix timestamp)
* accelerationTime — timeshift value based on comparison between two metrics:

* difference between current and previous RTC values
* difference between current and previous UTC values

1. If the value of the moveTime or accelerationTime parameter exceeds 86400 seconds (24 hours), retention operations will be blocked with the warning in the backup job session.

|  |
| --- |
| Note |
| Consider the following:   * To detect timeshift more precisely, RTC should be set to UTC. * If RTC is disabled, the accelerationTime parameter value will be ignored. The Veeam Immutability Service will check only the moveTime parameter. * If you shut down the repository for more than 24 hours, retention operations will be blocked. * If retention operations are blocked, the Veeam Immutability Service will not set or remove the immutable attribute for existing and new backup files. |

To get back to the normal operation mode, you will need to access the hardened repository under the user account with root privileges and perform the necessary operations. For more information, see [this Veeam KB article](https://www.veeam.com/kb4482).

The described hardened repository architecture prevents backup files from being deleted or modified by a potential attacker even if they exploit the Veeam Data Mover Service/Veeam Transport Service or compromise the NTP server. For more details, see [Protect against Ransomware with Immutable Backups](https://www.veeam.com/wp-guide-protect-ransomware-immutable-backups.html).

Immutability for Image-Level VM and Physical Machine Backups

For image-level VM backups and physical machine backups, immutability works in the following way:

1. For each backup file, Veeam Backup & Replication creates a.veeam.N.lock file that contains information about the immutability time period. Also, the xattr attribute with immutable time period is set on each backup file. These files are stored on the hardened repository.
2. Backup files become immutable for the configured time period (minimum 7 days, maximum — 9999). The immutability period is set according to the following:

* The count of the immutability period starts from the moment the last restore point in the active backup chain is created. For example:

* The full backup file of the active chain was created on January 12. The first increment was created on January 13. The last increment was created on January 14.
* The immutability period is set for 10 days and will be automatically extended for all backup files in the active chain. If there are several chains in the backup, Veeam Backup & Replication does not extend the immutability for inactive chains.
* Full and incremental backup files will be immutable until January 24: the date of the last restore point creation (January 14) + 10 days.

* The immutability flag is set on the file only when the current backup session is completed.

|  |
| --- |
| Note |
| For image-level VM backups, consider the following:   * If you use per-machine backup with single metadata file or per-machine backup with separate metadata files format for storing backups and the restore point was incomplete, the immutability flag will be set only on successfully created backup files. * If you use single-file backup format for storing backups and the restore point was incomplete, the immutability flag will not be set on the backup file.   For more information about backup chain formats, see [Backup Chain Formats](per_vm_backup_files.md). |

* If you increase the immutability period in repository settings, a new value will be applied for the active and next chains.
* If you decrease the immutability period and a new value for the next restore point is less than the previous one, it will be applied for the next incremental backups in the active chain and for the next chains. For example:

+ The immutability period is set for 20 days. The full backup file of the active chain was created on November 1. The first increment was created on November 2. The second increment was created on November 3. Full and incremental backup files will be immutable until November 23: the date of the last restore point creation (November 3) + 20 days.
+ If you decrease the immutability period to 7 days on November 4, all previous backup files in the active chain will be immutable until November 23. The next incremental backup in the active chain will be immutable until November 11: the date of the last restore point creation (November 4) + 7 days.

* If you decrease the immutability period and a new value for the next restore point is greater than the previous one, it will be applied for all backup files in the active chain and in the next chains. For example:

+ The immutability period is set for 20 days. The full backup file of the active chain was created on November 1. The first increment was created on November 2. The second increment was created on November 3. Full and incremental backup files will be immutable until November 23: the date of the last restore point creation (November 3) + 20 days.
+ If you decrease the immutability period to 7 days on November 22, all backup files in the active chain will be immutable until November 29: the date of the last restore point creation (November 22) + 7 days.

* If you use GFS retention policy, see [Retention Scenarios](#retention).

1. When the immutability time period expires, the immutability service makes backup files mutable again so they can be deleted or modified.

Immutability for Application-Aware Processing Log Backups

For application-aware processing log backups, immutability works in the following way:

1. For each log backup file, Veeam Backup & Replication creates a.veeam.N.lock file that contain information about immutability time period. These files are stored on the hardened repository.
2. Log backup files become immutable for the configured time period (minimum 7 days, maximum — 9999). The immutability period is set according to the following:

* Newly created log backup files are being updated several times according to the interval settings. Thus, the count of the immutability period starts and the immutability flag is set on the file only when the log backup job finished writing any data to the VLB file.
* The immutability period is not extended for log backup files in the active chain. If there are several chains in the backup, Veeam Backup & Replication also does not extend the immutability for old chains.

|  |
| --- |
| Important |
| If the immutability period is expired for log backup files in the active chain, these files become mutable and may be potentially removed. In this case, the application restore may fail as the log backup chain becomes incomplete. To mitigate risks, make sure that the immutability period covers all backups in the active backup chain. |

* If you increase the immutability period in repository settings, a new value will be applied for all log backup files created after the last successful image-level VM backup or physical machine backup. If you decrease the immutability period, a new value will be applied only for the next log backup files.
* If you use GFS retention policy, see [Retention Scenarios](#retention).

1. When the immutability time period expires, the immutability service makes backup files mutable again so they can be deleted or modified.

Immutability for Other Backups

For information on how immutability works for unstructured data backups and enterprise application backups, see the following sections:

* [Unstructured Data Backups in Immutable Repositories](unstructured_data_backup_in_immutable_repo.md)

* [Veeam Plug-In for Oracle RMAN](repos_rman.md#hardened)
* [Veeam Plug-In for SAP HANA](sap_repos.md#hardened)
* [Veeam Plug-In for SAP on Oracle](sap_orcl_repos.md#hardened)
* [Veeam Plug-In for Microsoft SQL Server](repos_mssql.md#hardened)

Retention Scenarios

Consider the following retention scenarios:

* An immutability retention overrides a job retention: if the job retention period is shorter than the immutability period, Veeam Backup & Replication does not delete backup files when the retention period is over, but only when the immutability period expires.
* Veeam Backup & Replication compares the immutability period of the backup repository and the GFS backup file lifetime, and sets an immutability period for full backup files with GFS retention policy as equal to the longest of these periods. For example: the backup repository immutability period is 10 days; the GFS backup file lifetime is 3 years; the backup file will be immutable for 3 years; the increments from this full backup file will be immutable for 10 days from the moment of the last increment creation.
* The immutability period for backup files produced with [VeeamZIP](veeamzip.md) or [Export Backup](exporting_backups.md) jobs is set according to the following:

* [With enabled retention period] Veeam Backup & Replication compares the immutability period of the backup repository and the retention period, and sets an immutability period for backup files with retention period as equal to the longest of these periods. For example: the backup repository immutability period is 1 month; the VeeamZIP or Export Backup backup file lifetime is 7 years; the backup file will be immutable for 7 years.

|  |
| --- |
| Note |
| If a hardened repository is a part of a scale-out backup repository with the capacity tier added and the move policy enabled and is used as a target for VeeamZIP or Export Backup jobs, Veeam Backup & Replication ignores the VeeamZIP or Export Backup retention period. The immutability time period for VeeamZIP or Export Backup backup files equals the period specified in the setting of a hardened repository. |

* [With disabled retention period] Veeam Backup & Replication ignores the VeeamZIP or Export Backup retention period. The immutability time period for VeeamZIP or Export Backup backup files equals the period specified in the setting of a hardened repository.

Page updated 10/17/2025

Page content applies to build 13.0.1.1071
