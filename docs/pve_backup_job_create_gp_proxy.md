---
title: "Step 5c. Choose Guest Interaction Proxy"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_backup_job_create_gp_proxy.html"
last_updated: "1/13/2026"
product_version: "13.0.1.1071"
---

# Step 5c. Choose Guest Interaction Proxy


To produce transactionally consistent backups and to perform file system indexing, Veeam Backup & Replication communicates with the guest OS of each processed VM to deploy non-persistent runtime components that coordinate guest processing activities such as accessing VM applications and creating a catalog of VM files. Since these activities may significantly increase the load on the backup server in case of a large backup scope, Veeam Backup & Replication distributes the load among all Microsoft Windows and Linux servers added to the backup infrastructure (further referred to as guest interaction proxies).

By default, Veeam Backup & Replication automatically chooses which guest interaction proxy to use for each of the processed VMs based on network settings and rules listed in section [Guest Interaction Proxies](guest_interaction_proxy.md). You can also manually limit the list of servers that may be used as proxies — to do that, click Choose, select the Prefer the following guest interaction proxy servers option and then select check boxes next to the necessary servers.

For a server to be displayed in the list of available log shipping servers, it must be added to the backup infrastructure as described in sections [Adding Microsoft Windows Servers](add_windows_server.md) and [Adding Linux Servers](add_linux_server.md).

|  |
| --- |
| Important |
| Due to technical limitations, Linux-based proxies cannot access Windows guest OSes in the current version. That is why if you have added Windows-based VMs to the backup scope at [step 3](pve_backup_job_create_assign_vms.md) of the wizard, you must also add at least one Microsoft Windows server to the backup infrastructure. |

![Step 5c. Choose Guest Interaction Proxy](images/pve_backup_job_create_gp_proxy.webp)


