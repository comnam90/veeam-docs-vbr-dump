---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vex_considerations.html"
last_updated: "1/21/2026"
product_version: "13.0.1.1071"
---

# Considerations and Limitations


This section lists considerations and limitations of Veeam Explorer for Microsoft Exchange.

General

* When Veeam Explorer for Microsoft Exchange is installed on a server on which both Veeam Backup & Replication and Veeam Backup for Microsoft 365 are installed, the notification settings will be inherited from the Veeam Backup & Replication Global Notification settings.
* Veeam Explorer for Microsoft Exchange does not support data restore using a group Managed Service Account (gMSA) to connect to the target server.
* [For Linux-based backup servers] All open Explorer sessions become non-responsive after backup server switchover or failback. To continue browsing and restoring your data, you must reopen the sessions.
* When restoring your Exchange data from CDP replicas, consider the following limitations:

* When you restore your data from CDP replicas, you can only use long-term (both application-consistent and crash-consistent) restore points. Short-term restore points are not supported.

* You can restore your data from a CDP replica if its CDP policy is currently running. During data restore, the CDP policy does not create new long-term restore points and does not delete existing ones. Short-term restore points are still created.
* You cannot restore application items from a CDP replica in parallel with guest OS file restore, SureReplica, and failover.

* Veeam Explorer for Microsoft Exchange must stay open during all data recovery operations. If the user who started the operation logs out or is logged out automatically, the operation will be terminated.

* To work with database files, Veeam Explorer for Microsoft Exchange requires a dynamic link library ese.dll supplied with Microsoft Exchange. The ese.dll file must be of the same version as that of Microsoft Exchange in which database files were created.
* [For machines with ReFS] The mount server, backup server and the machine where the console is installed must support the same or a later ReFS version than that on the source machine. For more information on which OSes support which ReFS version, see [ReFS versions and compatibility matrix](https://gist.github.com/XenoPanther/15d8fad49fbd51c6bd946f2974084ef8#mountability).

Restore

* Veeam Explorer for Microsoft Exchange does not support restore using PowerShell Direct, VIX API or vSphere Automation API.
* Sending objects that exceed 3 MB in size may fail. To fix this issue, install [this Microsoft update](https://support.microsoft.com/en-us/help/2468871/update-for-the-net-framework-4-march-2011).
* Bulk restore (restore of multiple objects) is not supported for public folder mailboxes. Use the regular per-object restore instead.
* Mailboxes can be restored only to mailboxes of the same type. For example, a user mailbox to a user mailbox, an archive mailbox to an archive mailbox.
* To restore In-Place Hold Items or Litigation Hold Items to the original location, consider the following:

* In-Place Hold Items restore is not supported for On-Premises Exchange Server 2013 due to EWS limitations.
* To restore In-Place Hold Items of Exchange 2016 mailboxes, these mailboxes must have In-Place Hold enabled and applied at least once with DiscoveryHolds system folder creation. Otherwise, restore will fail with the following error:

"Failed to restore In-Place Hold Items. Restore of In-Place Hold Items into Exchange 2013 is not supported".

For information on enabling In-Place Hold and Litigation Hold, see [this Microsoft article](https://technet.microsoft.com/en-us/library/ff637980%28v%3Dexchg.160%29.aspx).

* [For Veeam Explorer for Microsoft Exchange that comes with Veeam Backup & Replication] Restore of an entire mailbox or selected mailbox items to the original location is available with Veeam Universal License. When using a legacy socket-based license, the Enterprise or Enterprise Plus editions of Veeam Backup & Replication is required.

* [For restore from Veeam Backup & Replication backups] If your Veeam Explorer for Microsoft Exchange comes as part of a standalone Veeam Backup for Microsoft 365 installation, you cannot restore your Microsoft Exchange data by default. To enable this functionality, install Veeam Backup & Replication Enterprise edition or higher on the machine.

|  |
| --- |
| Note |
| To use an internet proxy server to restore backups created by Veeam Backup for Microsoft 365, make sure to provide appropriate proxy server address and the port number. To do this, go to the Control Panel > Internet Options Connections tab, click LAN Settings, select the Use a proxy server for your LAN check box and specify a proxy server you want to use. Credentials for such a proxy (if needed) will be taken from the Control Panel > Credential Manager > Windows Credentials console.  Consider that this functionality is only available in Veeam Explorer for Microsoft Exchange that comes as part of the Veeam Backup for Microsoft 365 installation package. |

Export

* Export is available if you have a 64-bit version of Microsoft Outlook 2010 or later installed on a computer with Veeam Explorer for Microsoft Exchange.

|  |
| --- |
| Note |
| For Outlook for Microsoft 365, only the Semi-Annual Enterprise Channel is supported. For more information, see [this Microsoft article](https://docs.microsoft.com/en-us/officeupdates/semi-annual-enterprise-channel). |

* To avoid conflicts during export, make sure to exclude PST files from the indexing scope. Oftentimes conflicts may occur if a file you are exporting is being indexed at the same time. When exporting to shared folders, exclude Outlook files or disable Windows search on the destination computer.


