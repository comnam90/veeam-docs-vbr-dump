---
title: "Using vSphere Self-Service Backup Portal"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_working_with_vsphere_vms.html"
last_updated: "12/8/2025"
product_version: "13.0.1.1071"
---

# Using vSphere Self-Service Backup Portal


vSphere Self-Service Backup Portal is a tool for VMware vSphere users that facilitates operations with delegated VM protection, including VM restore and files restore. These operations do not require access to the Veeam Backup & Replication console. For backup and restore operations, tenants access vSphere Self-Service Backup Portal.

Accessing Portal

To access vSphere Self-Service Backup Portal:

1. Open your web browser and enter the following address in the address bar:

|  |
| --- |
| https://<EnterpriseManagerServer>/backup |

For example:

|  |
| --- |
| https://enterprise01.tech.local/backup |

1. From the drop-down list, select a language that you want to use as the display language. For more information, see [Managing Languages](em_lang_manage.md).
2. Log in using your credentials:

* To log in with Enterprise Manager credentials:

1. In the Username and Password fields, specify credentials of the domain user for which the Enterprise Manager administrator created a vSphere Self-Service Backup Portal tenant account. The username must be provided in the DOMAIN\Username format.
2. To save the entered credentials for future access, select the Remain signed in option.
3. Click Sign in.

* To log in with the credentials of the Microsoft Windows account that you are currently signed in on the machine where you are launching Enterprise Manager, click Sign in as current user option.

* To log in with single sign-on, click Sign in with SSO. You will be redirected to the login webpage of the single sign-on service. Complete the sign-in procedure on the login page. If the account is already authenticated in the single sign-on service, you will immediately access the Enterprise Manager website.

The Sign in with SSO option is available if SAML authentication is configured for Veeam Backup Enterprise Manager. For more information, see [Configuring SAML Authentication Settings](veeam_backup_em_saml.md).

Working with Portal

You can use vSphere Self-Service Backup Portal to perform the following operations:

* View statistics on backups of vSphere VMs. For more information, see [Viewing Self-Service Backup Portal Statistics](em_viewing_statistics_vsphere_self_service.md).
* Work with backup jobs that process vSphere VMs: create and edit backup jobs; examine and export backup job session data; start, stop and retry backup jobs. For more information, see [Managing Backup Jobs](em_vsphere_user_backup_job.md).
* Perform backup and restore operations with vSphere VMs. For more information, see [Managing VMs](em_vsphere_user_vms_restore.md).
* Search for files in guest file systems of backed-up VMs and restore the necessary files to the original location or download them to a local machine. For more information, see [Restoring Guest OS Files](em_vsphere_user_files_restore.md).
* Perform item-level restore of Microsoft SQL Server and Oracle databases. For more information, see [Restoring Application Items](em_vsphere_user_items_restore.md).

|  |
| --- |
| Note |
| If the Veeam Backup Enterprise Manager server is added to the Veeam ONE monitoring scope, the restore operations performed with vSphere Self-Service Backup Portal are included in the [Restore Operator Activity](https://helpcenter.veeam.com/docs/one/userguide/restore_operator_activity.html?ver=13) report available in Veeam ONE. |


