---
title: "Permissions"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesp_permissions.html"
last_updated: "11/20/2025"
product_version: "13.0.1.1071"
---

# Permissions

In this article

The following table lists the user account permissions necessary to launch Veeam Explorer for Microsoft SharePoint and restore Microsoft SharePoint data.

| Operation | Required Roles and Permissions |
| --- | --- |
| Veeam Explorer for Microsoft SharePoint launch | The account used to run Veeam Explorer for Microsoft SharePoint must meet the following requirements:   * The account must be a member of the local Administrators group on the machine where Veeam Explorer for Microsoft SharePoint is running.  * The account must have one of the following roles on the backup server:  * The Veeam Backup Administrator or Veeam Restore Operator default roles. * A custom role with at least the Manage restores permission and the Veeam Explorer for Microsoft SharePoint restore option, with access to the target server and the backup. For more information, see [Configuring Roles](configure_roles.md#custom_roles). |
| Restore to Microsoft Office 365 | To restore data to SharePoint Online organizations, you must grant the following roles and permissions to user accounts:  Restore Using Basic Authentication Method   * The account used to log in to Microsoft Office 365 must have the Global Administrator or SharePoint Administrator role assigned.  * For restore of personal SharePoint sites, make sure to select the Allow users to run custom script on personal sites option in the SharePoint admin center. For more information, see [this Microsoft article](https://docs.microsoft.com/en-us/sharepoint/allow-or-prevent-custom-script). * During restore, Veeam Backup for Microsoft 365 automatically assigns the Site Collection Administrator role to the user account.   Restore Using Modern Authentication Method   * The account used to log in to Microsoft Office 365 must have the Global Administrator or SharePoint Administrator role assigned.  * For restore of personal SharePoint sites, make sure to select the Allow users to run custom script on personal sites option in the SharePoint admin center. For more information, see [this Microsoft article](https://docs.microsoft.com/en-us/sharepoint/allow-or-prevent-custom-script). * During restore, Veeam Backup for Microsoft 365 automatically assigns the Site Collection Administrator role to the user account. * Make sure that the required settings are specified for the Microsoft Entra application used for restore. For more information, see the [Configuring Microsoft Entra Application Settings](https://helpcenter.veeam.com/docs/vbo365/guide/ad_application_settings_configuring.html?ver=80) section of the Veeam Backup for Microsoft 365 User Guide. |
| Restore to on-premises Microsoft SharePoint | To restore data to on-premises Microsoft SharePoint organizations, you must grant the following roles and permissions to user accounts:   * The account must be granted Full Control to connect to the target SharePoint server. * The account must be assigned either the Site Administrator or System Account role to restore user permissions. * If permissions of items being restored are inherited from the parent one, the account must be granted Full Control. * If permissions of items being restored are not inherited from the parent one and items being restored replace the existing ones, the account must be granted Contribute and Full Control. |
| Staging Microsoft SQL Server configuration | To work with Veeam Backup & Replication backups or manually add databases, the account must be granted the sysadmin fixed server role on the staging Microsoft SQL Server machine.  Consider the following:   * If you want to use a local Microsoft SQL Server instance as a staging server and Veeam Explorer for Microsoft SQL Server runs under an account that does not belong to the local Administrators group, you must specify the current account for connection to the staging server, or you will get an impersonation error. * The current account can only be used to access a local staging server. To connect to a remote server, use appropriate authentication credentials to access that server.   For more information on the staging server prerequisites, see [Staging SQL Server](vesp_staging_microsoft_sql_server.md). For more information on how to configure and use the staging server, see [Staging SQL Server Settings](vesp_configuring_sql_settings.md). |

Consider the following if you are using ADFS as an authentication provider:

* When using Windows Authentication, you can use both your current account or provide another account.
* When using Forms Authentication, the current account cannot be used.

Page updated 11/20/2025

Page content applies to build 13.0.1.1071
