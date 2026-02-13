---
title: "Step 3b. Choose Disks"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_backup_job_create_disk_excludes.html"
last_updated: "2/11/2026"
product_version: "13.0.1.1071"
---

# Step 3b. Choose Disks


Second, at the Virtual Machines step of the wizard, you can instruct Veeam Plug-in for Scale Computing HyperCore to back up only specific virtual disks related to the selected backup scope:

1. Click Exclusions.
2. In the Exclusions window, switch to the Disks tab and click Add.
3. In the Add Objects window, select a resource that you have added to the backup scope at [step 3a](sch_backup_job_create_resources.md), and click OK.
4. Back to the Exclusions window, select the resource and click Edit.
5. In the Select Disks window, select the Selected Disks option, click Add and choose a bus type of the disks that you want to back up. Then, select the necessary disks.

Disks that you do not select will be excluded from the backup job.

[![Select Disks and Volume Groups](images/sch_backup_job_create_disk_excludes.webp)](images/sch_backup_job_create_disk_excludes.webp "Select Disks and Volume Groups")


