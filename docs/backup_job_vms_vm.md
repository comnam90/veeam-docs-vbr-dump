---
title: "Step 3. Select VMs to Back Up"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_job_vms_vm.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Select VMs to Back Up


At the Virtual Machines step of the wizard, select VMs and VM containers (hosts, clusters, folders, resource pools, vApps, datastores or tags) that you want to back up:

1. Click Add.
2. In the Add Objects window, select the necessary VMs or VM containers and click Add. If you select VM containers and add new VMs to this container in the future, Veeam Backup & Replication will update backup job settings automatically to include these VMs.

You can use the toolbar at the top right corner of the window to switch between views. Depending on the view you select, some objects may not be available. For example, if you select the Tags combination view, no resource pools, hosts or clusters will be displayed in the tree. In the Tags combination view, you can select multiple tags, and only those VMs that have all the selected tags will be processed by the job.

To quickly find the necessary VMs, you can use the search field at the bottom of the Add Objects window. If you want to switch between the types of VMs you want to search through, use the button to the left of the search field.

You do not have to add any objects at this step. If you leave the list empty, Veeam Backup & Replication creates an empty backup job. You can edit the job later to add VMs and VM containers.

|  |
| --- |
| Important |
| An empty backup job may fail if it runs on schedule, especially if guest processing is enabled. To avoid this, add at least one VM or VM container to the job before its scheduled run. |

|  |
| --- |
| Note |
| You can use a regular backup job to process VMs that are part of vApps created in the vCenter Server. To back up VMware Cloud Director vApps, you must use specifically developed VMware Cloud Director backup jobs. For more information, see [Backup for VMware Cloud Director](vcloud_director_backup.md). |

The total size of objects added to the job is displayed in the Total size field. Use the Recalculate button to refresh the total size value after you add a new object to the job.

![Step 3. Select VMs to Back Up](images/vm_backup_job_add_vms.webp)

Page updated 2026-07-15

