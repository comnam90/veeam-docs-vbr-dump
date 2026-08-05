---
title: "Step 3. Configure Backup Source Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_backup_job_vbr_assign_vms_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 3. Configure Backup Source Settings


At the Sources step of the wizard, specify the backup scope — select resources that Veeam Backup & Replication will back up:

1. Click Add.
2. In the Add Objects window, choose whether you want to back up all VMs in the cluster, only specific VMs or protection domains. In the [Prism Central deployment](ahv_infrastructure_prism_central.md), you can also back up VMs and clusters assigned to a specific category or all VMs managed by a Prism Central.

To view the list of available protection domains, click the Protection Domains icon. If you add a protection domain, Veeam Backup & Replication will regularly check for new consistency groups (VMs and volume groups) added to the domain and automatically update the job settings to include these groups in the backup scope. For a protection domain to be displayed in the list of the available domains, it must be configured in the Nutanix AHV cluster as described in [Nutanix documentation](https://portal.nutanix.com/page/documents/details?targetId=Prism-Element-Data-Protection-Guide-v7_3:wc-protection-domain-wc-t.html).

To view the list of available categories, click the Categories icon. If you add a category, Veeam Backup & Replication will regularly check for new VMs and clusters assigned to the category and automatically update the job settings to include these resources in the backup scope. You can also add several categories using the <AND> Categories icon — in this case Veeam Backup & Replication will check for new VMs and clusters assigned to all of the selected categories. For a category to be displayed in the list of the available categories, it must be configured in the Nutanix AHV Prism Central as described in [Nutanix documentation](https://portal.nutanix.com/page/documents/details?targetId=Prism-Central-Admin-Center-Guide-vpc_7_3:ssp-ssp-categories-manage-pc-c.html).

1. [Applies only to the [Prism Central deployment scenario](ahv_infrastructure_prism_central.md)] If you want to instruct Veeam Backup & Replication to obtain VM data from a replica cluster, select the Use snapshots from a replica site (if available) check box.

Using replica clusters helps reduce the load on the production environment. If Veeam Backup & Replication fails to obtain data from a replica cluster, backup will be still performed using VM data obtained from the main cluster. For more information on snapshots from replica sites, see [Snapshot Types](ahv_nutanix_snapshots.md#replica).

|  |
| --- |
| Tip |
| As an alternative to specifying resources explicitly, you can exclude a number of resources from the backup scope. To do that, click Backup Filters and specify the VMs, protection domains, cluster or categories that you do not want to back up — the procedure is the same as described for including resources in the backup scope.  Consider that if a resource appears both in the list of included and excluded resources, Veeam Backup & Replication will not process the resource because the list of excluded resources has a higher priority. |

While running the job, Veeam Backup & Replication processes resources in the order they are added to the backup scope. However, you can change the order, for example, if you add some mission-critical VMs to the job and want them to be processed first. To change the processing order, select a resource and use the Up or Down buttons.

|  |
| --- |
| Notes |
| * If you include a resource into the backup scope multiple times (for example, an individual VM and a PD that contains this VM), Veeam Backup & Replication will process this resource only once.  * If you include a protection domain, category, cluster or Prism Central into the backup scope, VMs in this object are processed at random. To ensure that the VMs are processed in a specific order, you must add them as standalone VMs — not as a part of the protection domain, category, cluster or Prism Central. |

[![Launch Add Job Wizard](images/ahv_backup_job_add_vbr_scope_web.webp)](images/ahv_backup_job_add_vbr_scope_web.webp "Launch Add Job Wizard")

Excluding Disks and Volume Groups from Backup Scope

By default, jobs process all disks and volume groups attached to VMs included into the backup scope. However, you can instruct Veeam Backup & Replication to back up only specific virtual disks and volume groups related to the selected backup scope. To do that:

1. Click Backup Filters.
2. In the Backup Filters window, switch to the Objects to Exclude tab and click Add.
3. In the Add Objects window, select a resource that you have added to the backup scope and click OK.
4. Back to the Backup Filters window, switch to the Disks to Protect tab and click Add.
5. In the Select Disks window, select the Selected Disks option, click Add and choose a bus type of the disks that you want to back up. Then, select the necessary disks.

Disks that you do not select will be excluded from the backup job.

|  |
| --- |
| Notes |
| * If you configure multiple disk protection rules, specific rules will override general ones. For example, if you add a rule for a protection domain and for a VM included in this domain, Veeam Backup & Replication will process the VM disks according to the rule configured for the VM. * If a resource appears both in the list of included and excluded resources, Veeam Backup & Replication will not process the resource because the list of excluded resources has a higher priority. |

[![Launch Add Job Wizard](images/ahv_backup_job_add_vbr_exclude_web.webp)](images/ahv_backup_job_add_vbr_exclude_web.webp "Launch Add Job Wizard")

Page updated 2026-07-14

