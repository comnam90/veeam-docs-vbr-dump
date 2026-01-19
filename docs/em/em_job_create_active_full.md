---
title: "Creating Active Full Backups"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_job_create_active_full.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Creating Active Full Backups


You can create an ad-hoc full backup — active full backup, and add it to the backup chain in the backup repository. The active full backup resets the backup chain. All subsequent incremental backups use the active full backup as a starting point. The previously used full backup will remain in the backup repository until it is removed from the backup chain according to the retention policy.

|  |
| --- |
| Note |
| Creating active full backups is unavailable for backup copy jobs, file backup jobs and object storage backup jobs. |

To perform an active full backup:

1. Select the required job in the list on the Jobs tab.
2. Expand the menu commands by clicking Job, then select Active Full.

[![Creating Active Full Backups](images/em_job_active_full.webp)](images/em_job_active_full.webp "Creating Active Full Backups")


