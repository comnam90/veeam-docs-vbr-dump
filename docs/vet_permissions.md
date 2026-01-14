---
title: "Permissions"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vet_permissions.html"
last_updated: "11/20/2025"
product_version: "13.0.1.1071"
---

# Permissions

In this article

The following table lists the user account permissions necessary to launch Veeam Explorer for Microsoft Teams and restore Microsoft Teams data.

| Operation | Required Roles and Permissions |
| --- | --- |
| Veeam Explorer for Microsoft Teams launch | The account used to run Veeam Explorer for Microsoft Teams must meet the following requirements:   * The account must be a member of the local Administrators group on the machine where Veeam Explorer for Microsoft Teams is running.  * The account must have one of the following roles on the backup server:  * The Veeam Backup Administrator or Veeam Restore Operator default roles. * A custom role with at least the Manage restores permission and the Veeam Explorer for Microsoft Teams restore option, with access to the target server and the backup. For more information, see [Configuring Roles](configure_roles.md#custom_roles). |
| Restore to Microsoft 365 | To restore Microsoft Teams data, you must grant the following roles and permissions to user accounts:  Restore Using Basic Authentication Method   * The user account must have a Microsoft 365 license that permits access to Microsoft Teams API. The minimum sufficient license is Microsoft Teams Exploratory experience. For more information about the Microsoft Teams Exploratory experience, see [this Microsoft article](https://learn.microsoft.com/en-us/microsoftteams/teams-exploratory). * To restore Microsoft Teams data, the user account must have the Teams Administrator role.   Restore Using Modern Authentication Method   * The user account must have a Microsoft 365 license that permits access to Microsoft Teams API. The minimum sufficient license is Microsoft Teams Exploratory experience. * The account used to log in to Microsoft Office 365 must have the Global Administrator or Teams Administrator role assigned.  * Make sure that the required settings are specified for the Microsoft Entra application used for restore. For more information, see the [Configuring Microsoft Entra Application Settings](https://helpcenter.veeam.com/docs/vbo365/guide/ad_application_settings_configuring.html?ver=80) section of the Veeam Backup for Microsoft 365 User Guide. |

Page updated 11/20/2025

Page content applies to build 13.0.1.1071
