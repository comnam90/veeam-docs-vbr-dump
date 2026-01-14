---
title: "Considerations and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vet_considerations.html"
last_updated: "11/20/2025"
product_version: "13.0.1.1071"
---

# Considerations and Limitations

In this article

This section lists considerations and limitations of Veeam Explorer for Microsoft Teams.

General

Consider the following:

* Veeam Explorer for Microsoft Teams must stay open during all data recovery operations. If the user who started the operation logs out or is logged out automatically, the operation will be terminated.

* If a user never opened the Files tab of a team channel in Microsoft Teams before data backup, files from this tab are not displayed in Veeam Explorer for Microsoft Teams.
* [For Linux-based backup servers] All open Explorer sessions become non-responsive after backup server switchover or failback. To continue browsing and restoring your data, you must reopen the sessions.

|  |
| --- |
| Note |
| To use an internet proxy server to restore backups created by Veeam Backup for Microsoft 365, make sure to provide appropriate proxy server address and the port number. To do this, go to the Control Panel > Internet Options Connections tab, click LAN Settings, select the Use a proxy server for your LAN check box and specify a proxy server you want to use. Credentials for such a proxy (if needed) will be taken from the Control Panel > Credential Manager > Windows Credentials console.  Consider that this functionality is only available in Veeam Explorer for Microsoft Teams that comes as part of the Veeam Backup for Microsoft 365 installation package. |

Data Restore

Consider the following when planning to restore Microsoft Teams data:

* Use of modern authentication with legacy protocols allowed is not supported for data restore with Veeam Explorer for Microsoft Teams.
* You can restore Microsoft Teams data to the original organization only.
* Veeam Explorer for Microsoft Teams does not change roles for team owners during restore. For example, you create a backup of your organization, and then change the role for a team member from Member to Owner. In this case, if you restore this team member from the backup, Veeam Explorer for Microsoft Teams will not set their role to Member.

* Restore of OneNote notebooks from backups of Microsoft Teams data for organizations with modern app-only authentication is not supported.

* When restoring a channel tab, Veeam Explorer for Microsoft Teams does not preserve relation between the link to a file published on the tab and the file itself. You will need to link the tab to the file manually after restore. This limitation does not apply to the scenario where you restore an entire team.
* Veeam Explorer for Microsoft Teams does not restore posts to their original location in the team channel. Instead, Veeam Explorer for Microsoft Teams exports posts to a file of the HTML format, creates a separate tab in the original channel and attaches the HTML file to this tab.
* Before restoring posts, make sure that Website App is unblocked both for your organization and the user account that you use to restore Microsoft Teams data.
* When restoring a channel, Veeam Explorer for Microsoft Teams cannot rename this channel.

* Before restoring team data for a tenant organization with modern app-only authentication, make sure that a user account used for authorization has access to the root SharePoint site of this tenant organization.

Page updated 11/20/2025

Page content applies to build 13.0.1.1071
