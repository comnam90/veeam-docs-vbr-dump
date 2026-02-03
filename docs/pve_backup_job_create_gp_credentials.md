---
title: "Step 5d. Manage VM Guest OS Credentials"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_backup_job_create_gp_credentials.html"
last_updated: "1/13/2026"
product_version: "13.0.1.1071"
---

# Step 5d. Manage VM Guest OS Credentials


If you enable application-aware processing or instruct Veeam Backup & Replication to create a catalog of VM files and folders, you must also specify a user whose credentials will be used to communicate with VM guest OSes. Note the specified user must have the permissions required to perform guest processing. For more information on the required permissions, see [Planning and Preparation](pve_permissions.md).

By default, Veeam Backup & Replication uses single credentials to access guest OSes of all VMs included into the backup scope. However, since Windows-based VMs and Linux-based VMs require different types of access credentials, you may need to specify the credentials explicitly for each of the processed VMs. To do that, click Credentials, select a VM in the Guest OS credentials window, and then click Set User > Standard credentials (for a Windows-based VM) or Set User > SSH credentials (for a Linux-based VM).

For a user to be displayed in the Credentials list, it must be added to the Credentials Manager as described in section [Credentials Manager](credentials_manager.md). If you have not added the necessary user to the Credentials Manager beforehand, you can do it without closing the New Job wizard. To do that, click either the Manage accounts link or the Add button, and specify the user name, password and description in the Credentials window.

|  |
| --- |
| Tip |
| If the backup scope includes a resource pool, host or cluster, you can specify both Standard and SSH credentials. This will allow Veeam Backup & Replication to access the processed VMs regardless of their guest OSes. |

To check whether Veeam Backup & Replication is able to connect to the VM guest OSes using the specified credentials, click Verify Network Connectivity.

![Step 5d. Manage VM Guest OS Credentials](images/pve_backup_job_create_gp_credentials.webp)


