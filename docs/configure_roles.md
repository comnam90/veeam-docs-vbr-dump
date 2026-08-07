---
title: "Configuring Roles"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/configure_roles.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Configuring Roles


To perform Veeam Backup & Replication operations, you can either assign the [default roles](#default_roles) to users or create [custom roles](#custom_roles) depending on your needs.

Default Roles

The default roles are the following:

Default Roles

| Role | Operations |
| Backup Administrator | Can perform all administrative activities in the Veeam Backup & Replication console. Note that Backup Administrator has full access to all files on servers and hosts added to the backup infrastructure. |
| Security Administrator | Can perform the following operations:   * Add, edit and delete all types of credential records supported by Veeam Backup & Replication. For more details, see [Managing Credentials](managing_credentials.md). * Manage Security & Compliance Analyzer: run security checks, configure scan scheduling, exclude parameters from the checklist. For more details, see [Security & Compliance Analyzer](best_practices_analyzer.md). * Approve four-eyes authorization requests. For more details, see [Four-Eyes Authorization](four_eyes_authorization.md). |
| Incident API Operator | Can perform Veeam Backup & Replication REST API requests to manage malware detection events. For more details, see the [Malware Detection](https://helpcenter.veeam.com/references/vbr/13/rest/1.3-rev0/tag/Malware-Detection) section in the Veeam Backup & Replication REST API Reference.  Incident API Operators do not have access to the Veeam Backup & Replication console. Since they interact only with Veeam Backup & Replication REST API, make sure that multi-factor authentication is disabled for the user you add as Incident API Operator. For more details, see [Disabling MFA for Service Accounts](mfa.md#disable_mfa_service_accounts). |
| Restore Operator | Can perform restore operations using existing backups and replicas.  Consider the following:   * Restore Operator can restore data from any backups. This allows them to restore disks and files with specially crafted malicious content. To reduce the risk of privilege escalation attacks and the entire system takeovers, assign this role with caution. * Restore Operator can overwrite existing VM, disk and file instances during VM, disk and file-level restore operations. * Restore Operator can migrate a recovered VM to the production environment during Instant Recovery. |
| Backup Operator | Can start and stop existing jobs, export backups, copy backups and create VeeamZip backups. |
| Backup Viewer | Has the read-only access to the Veeam Backup & Replication console. Can view a list of existing jobs and review the job session details. |
| Tape Operator | Can manage tapes and perform the following operations:   * Rescan tape libraries and tape servers. * Run tape backup jobs, tape catalog jobs, tape inventory jobs, tape verification jobs. * Eject tapes. * Import and export tapes. * Mark tapes as free. * Move tapes to a media pool. * Erase tapes. * Set a tape password. * Copy tapes. |

You can assign several roles to the same user. For example, if you want a user to start jobs and perform restore operations, you can assign both the Backup Operator and Restore Operator roles to this user.

Custom Roles

You can create custom roles in Veeam Backup & Replication to assign tailored permissions and granular access scopes to users or groups. Custom roles help you enforce the principle of least privilege and align user access with your organization’s operational policies.

You can configure custom roles in one of the following ways:

* [Configuring Roles Using Console](configure_roles_console.md)
* [Configuring Roles Using Web UI](configure_roles_web.md)

Roles Limitations

General

* Enhanced Role-Based Access Control (RBAC) feature is only available with a certain license edition. For more information, see [Veeam Data Platform Feature Comparison](https://www.veeam.com/veeam_data_platform_feature_comparison_ds.pdf).
* Assigning both custom and built-in roles to the same user or group is not supported.
* Empty nodes may be displayed if their objects are inaccessible to a custom role.
* If an administrator moves or copies a backup, the backup ACL will be reset, which may result in custom roles losing access to the backup.

Backup

* If a user does not have permission to view certain credentials, those credentials do not appear in the backup wizard when editing a job. However, the credentials remain configured in the job.
* If a custom backup operator is not restricted to a specific repository, backups can be created in Snapshot Repositories.

Recovery

* Quick Migration is only available to users with administrator privileges.
* The Encrypted backups node is not available to restore operators.
* Backup copy jobs are not visible in the backup scope selection for roles.
* Backups imported as VBK are not visible in the backup scope selection in the role wizard.
* A role with restrictions on the restore target cannot select a different location for the Copy to option in Linux file-level restore.
* The software appliance backup server remains available for use even if only the Original location option is selected.

VMware vSphere

* In the Tag view, all vCenters are always visible but cannot be added or expanded. VMware tags can only be used if they have been explicitly added to a role.
* vApps may be visible but cannot be used.
* VMware objects associated with those added to a role may be visible but cannot be used.
* Unavailable original hosts may remain visible in certain restore wizards.

Unstructured Data Backup

* Role-based access control does not support [instant file share recovery](instant_nas_recovery.md).
* If the original location is included in the target restore scope, the Copy to option in [specific file and folder restore](file_share_recovery_restore_files_folders.md) is unavailable.
* The Copy to option may be used to restore to more locations than those defined in the target restore scope.

Page updated 2026-07-13

