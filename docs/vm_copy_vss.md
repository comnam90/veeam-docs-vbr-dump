---
title: "Step 6. Specify Guest Processing Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vm_copy_vss.html"
last_updated: "4/29/2025"
product_version: "13.0.1.1071"
---

# Step 6. Specify Guest Processing Settings

In this article

At the Guest Processing step of the wizard, you can enable the following settings for VM guest OS processing:

* [Application-aware processing](vm_copy_vss_application.md)
* [Microsoft SQL Server transaction log settings](vm_copy_vss_transaction_sql.md)
* [Oracle archived log settings](vm_copy_vss_transaction_oracle.md)
* [PostgreSQL WAL Files settings](vm_copy_vss_postgresql_vm.md)
* [Use of pre-freeze and post-thaw scripts](vm_copy_vss_scripts.md)

To coordinate guest processing activities, Veeam Backup & Replication deploys non-persistent runtime components or uses (if necessary, deploys) persistent agent components on the VM guest OS.

The non-persistent runtime components run only during guest processing and are stopped immediately after the processing is finished (depending on the selected option, during the VM copy job session or after the replication job completes).

You must specify a user account that will be used to connect to the VM guest OS and deploy the non-persistent runtime components or connect to (if necessary, deploy) persistent agent components:

1. From the Guest OS credentials list, select a user account that has enough permissions. For more information on the permissions and requirements for the user account, see [Permissions for Guest Processing](required_permissions.md#rptcb).

If you have not set up credentials beforehand, click the Manage accounts link or click the Add button to add credentials. For more information on adding credentials, see the [Credentials Manager](credentials_manager.md) section.

1. By default, Veeam Backup & Replication uses the same credentials for all VMs in the job. If some VM requires a different user account, click Credentials and enter custom credentials for the VM.

|  |
| --- |
| Important |
| Credentials for application-aware processing and guest OS file indexing for Microsoft Windows VMs must be specified in the following format:   * For Active Directory accounts — DOMAIN\Username * For local accounts — Username or HOST\Username |

1. If you have added Microsoft Windows VMs to the job, specify which guest interaction proxy Veeam Backup & Replication can use to deploy the non-persistent runtime components or connect to (if necessary, deploy) persistent agent components on the VM guest OS. On the right of the Guest interaction proxy field, click Choose.

* Leave Automatic selection to let Veeam Backup & Replication automatically select the guest interaction proxy.
* Select Use the selected guest interaction proxy servers only to explicitly define which servers will perform the guest interaction proxy role. The list of servers contains Microsoft Windows servers added to the backup infrastructure.

To check if Veeam Backup & Replication can communicate with VMs added to the job and deploy the non-persistent runtime components or connect to (if necessary, deploy) persistent agent components on their guest OSes, click Test Now. Veeam Backup & Replication will use the specified credentials to connect to all VMs in the list.

|  |
| --- |
| Note |
| The guest interaction proxy functionality is included in the Veeam Universal License. When using a legacy socket-based license, Enterprise or higher edition is required. |

![Step 6. Specify Guest Processing Settings](images/vm_copy_job_vss.webp)

Page updated 4/29/2025

Page content applies to build 13.0.1.1071
