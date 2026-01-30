---
title: "Step 3. Select VMs to Back Up"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_job_vms_hv_web.html"
last_updated: "9/17/2025"
product_version: "13.0.1.1071"
---

# Step 3. Select VMs to Back Up


At the Virtual Machines step of the wizard, select VMs and VM containers (hosts, clusters, folders, resource pools, VirtualApps, datastores or tags) that you want to back up:

1. Click Add.
2. In the Add Objects window, select the necessary VMs or VM containers and click Add. If you select VM containers and add new VMs to this container in the future, Veeam Backup & Replication will update backup job settings automatically to include these VMs.

You can use the toolbar at the top of the window to switch between views. Depending on the view you select, some objects may not be available.

To quickly find the necessary VMs, you can use the search field below the toolbar. If you want to switch between the types of VMs you want to search through, use the drop-down list to the left of the search field.

|  |
| --- |
| Note |
| You can use a regular backup job to process VMs that are part of vApps created in the vCenter Server. To back up VMware Cloud Director vApps, you must use specifically developed VMware Cloud Director backup jobs. For more information, see [Backup for VMware Cloud Director](vcloud_director_backup.md). |

[![Click to zoom in](images/hv_backup_job_add_vms_web.webp)](images/hv_backup_job_add_vms_web.webp "Click to zoom in")


