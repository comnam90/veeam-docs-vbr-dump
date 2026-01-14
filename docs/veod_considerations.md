---
title: "Considerations and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/veod_considerations.html"
last_updated: "11/20/2025"
product_version: "13.0.1.1071"
---

# Considerations and Limitations

In this article

This section lists considerations and limitations of Veeam Explorer for Microsoft OneDrive for Business.

* Veeam Explorer for Microsoft OneDrive for Business must stay open during all data recovery operations. If the user who started the operation logs out or is logged out automatically, the operation will be terminated.

* Restore of OneNote notebooks from backups of Microsoft OneDrive for Business data for organizations with modern app-only authentication is not supported.

* If the size of a OneNote notebook is greater 2 GB, Veeam Explorer for Microsoft OneDrive for Business saves this OneNote notebook as a folder with OneNote items.
* [For Linux-based backup servers] All open Explorer sessions become non-responsive after backup server switchover or failback. To continue browsing and restoring your data, you must reopen the sessions.

|  |
| --- |
| Note |
| To use an internet proxy server to restore backups created by Veeam Backup for Microsoft 365, make sure to provide appropriate proxy server address and the port number. To do this, go to the Control Panel > Internet Options Connections tab, click LAN Settings, select the Use a proxy server for your LAN check box and specify a proxy server you want to use. Credentials for such a proxy (if needed) will be taken from the Control Panel > Credential Manager > Windows Credentials console.  Consider that this functionality is only available in Veeam Explorer for Microsoft OneDrive for Business that comes as part of the Veeam Backup for Microsoft 365 installation package. |

Page updated 11/20/2025

Page content applies to build 13.0.1.1071
