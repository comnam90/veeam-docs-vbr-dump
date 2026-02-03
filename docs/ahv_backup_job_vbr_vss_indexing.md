---
title: "Step 5b. Enable VM Guest OS File Indexing"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_backup_job_vbr_vss_indexing.html"
last_updated: "1/13/2026"
product_version: "13.0.1.1071"
---

# Step 5b. Enable VM Guest OS File Indexing


To be able to recover individual files with 1 click and to search for specific items in Veeam Backup Enterprise Manager during [file-level restore](https://helpcenter.veeam.com/docs/vbr/em/searching_restoring_vm_guest_files.html?ver=13), you must enable file indexing to instruct Veeam Backup & Replication to create a catalog of files and folders that belong to VMs included into the backup scope. To do that, select the Enable guest file system indexing and malware detection check box at the Guest Processing step of the wizard.

|  |
| --- |
| Note |
| If you enable file indexing, Veeam Backup & Replication will scan VM data for suspicious file system activity and malware file presence every time the backup job completes successfully. For more information, see [How Guest Indexing Data Scan Works](malware_detection_guest_index_hiw.md). |

By default, Veeam Backup & Replication will create a catalog of all files and folders for each processed VM — except for system files. To change this behavior and configure indexing settings for a specific VM, do the following:

1. Click Customize guest file system indexing settings.
2. In the Guest File System Indexing Options window, select the necessary VM and click Edit > Windows indexing or Linux indexing. You can configure indexing settings for one or more VMs at a time.
3. In the Indexing Settings window, choose whether you want to index files in all guest OS folders, to index files only in specific folders, or not to index any files at all.

If you select the Index everything except or Index only following folders option, you will be able to modify the list of folders included into the indexing scope — either manually or by using system environment variables (for example, %windir%, %ProgramFiles% and %Temp%).

|  |
| --- |
| Important |
| To allow Veeam Backup & Replication to perform guest OS file indexing for Linux VMs, openssh, gzip and tar utilities must be installed on the processed VMs. |

![Step 5b. Enable VM Guest OS File Indexing](images/ahv_backup_job_vbr_vss_indexing.webp)


