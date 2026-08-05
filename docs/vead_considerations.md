---
title: "Considerations and Limitations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vead_considerations.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Considerations and Limitations


This section lists considerations and known limitations of Veeam Explorer for Microsoft Active Directory.

General

* [For data recovery with Explorer console] When Veeam Explorer for Microsoft Active Directory is installed on a server on which both Veeam Backup & Replication and Veeam Backup for Microsoft 365 are installed, the notification settings will be inherited from the Veeam Backup & Replication Global Notification settings.
* When recovering your Active Directory data from CDP replicas, consider the following limitations:

* When you recover your data from CDP replicas, you can only use long-term (both application-consistent and crash-consistent) restore points. Short-term restore points are not supported.
* You can recover your data from a CDP replica if its CDP policy is currently running. During recovery, the CDP policy does not create new long-term restore points and does not delete existing ones. Short-term restore points are still created.
* You cannot restore application items from a CDP replica in parallel with guest OS file restore, SureReplica, and failover.

* Connecting to the target server using a group Managed Service Account (gMSA) is supported in PowerShell and the Explorer web UI.
* [For data recovery with Explorer console] Veeam Explorer for Microsoft Active Directory must stay open during all data recovery operations. If the user who started the operation logs out or is logged out automatically, the operation will be terminated.

* Veeam Explorer for Microsoft Active Directory does not support Active Directory Lightweight Directory Services (AD LDS).
* [For data recovery with Explorer console] When you launch Veeam Explorer for Microsoft Active Directory, the Veeam Mount Service running on the mount server associated with the backup repository mounts the backed-up file system to the machine where the Explorer is running. The Veeam Mount Service unmounts the file system when you close the Explorer session.
* [For data recovery with Explorer console] Veeam Explorer for Microsoft Active Directory can only export items to the machine where the Explorer is running.
* For object recovery, Veeam Explorer for Microsoft Active Directory opens database files created by the domain controller on the machine where the Explorer is running (for data recovery with the Explorer console) or on the mount server machine (for data recovery with the Explorer web UI).

To open database files, make sure that the following requirements are met on that machine:

* The machine must have the same OS version as the domain controller, or a later one.
* The service dynamic link library (Esent.dll) file on the machine must be the same version as the Microsoft Active Directory Domain Services that created the database files. The Esent.dll file is installed with Microsoft Active Directory Domain Services and can be found in the %SystemRoot% directory of the machine.

* [For machines with ReFS] The mount server, backup server and the machine where the Veeam Backup & Replication console is installed must support the same or a later ReFS version than that on the source machine. For more information on which OSes support which ReFS version, see [ReFS versions and compatibility matrix](https://gist.github.com/XenoPanther/15d8fad49fbd51c6bd946f2974084ef8#mountability).
* [For Linux-based backup servers] All open Explorer sessions become non-responsive after backup server switchover or failback. To continue browsing and restoring your data, you must reopen the sessions.

Restore

* Veeam Explorer for Microsoft Active Directory does not support restore using PowerShell Direct, VIX API or vSphere Automation API.

* Data can only be restored back to the original domain. Cross-domain restore is not supported.

* [For data recovery with Explorer console] Veeam Explorer for Microsoft Active Directory does not support recovery of the contents of the Domain Controllers container and most of the contents of the System container (in particular, the Password Settings container), as this may cause system stability issues on the target machine. Moreover, some of the contents of the System container, as well as the entire Configuration Partition container, the Microsoft Exchange System Options container, the Integrated DNS container and so on, can be recovered with Veeam Explorer for Microsoft Active Directory, but they are only visible in the Advanced Features view to prevent accidental errors during the recovery process. For more information, see the [Browsing, Searching and Viewing Items](vead_browsing.md) section.

* Veeam Explorer for Microsoft Active Directory supports restore of both mailbox-enabled objects (including hard-deleted items and Online Archives), and mail-enabled objects for the following Microsoft Exchange versions: Microsoft Exchange Server 2019, Microsoft Exchange Server 2016, Microsoft Exchange Server 2013 and Microsoft Exchange Server 2010 SP1. For other Microsoft Exchange versions, restore of mailbox-enabled objects is not supported (only mail-enabled objects can be restored).
* To restore passwords, Veeam Explorer for Microsoft Active Directory uses the registry database. To restore passwords, make sure the System registry hive is available. The default location of the hive is %systemroot%\System32\Config. When restoring an Active Directory database from the Active Directory backup using Veeam file-level restore, the registry hive will be located automatically. When restoring from an imported backup or from VeeamZIP backups, make sure that the system registry hive and the .dit file are located in the same directory.

* Veeam Explorer for Microsoft Active Directory does not support restore of custom objects (objects not listed in the Active Directory [classes](https://learn.microsoft.com/en-us/windows/win32/adschema/classes-all) and [attributes](https://learn.microsoft.com/en-us/windows/win32/adschema/attributes-all)). For example, you cannot restore some objects created by 3rd party applications. To restore custom objects, restore the entire machine.

Also, note that Veeam Explorer for Microsoft Active Directory does not support restore of some Active Directory classes and attributes.

* Restore of Group Policy objects, AD-integrated DNS records and objects from the Configuration Partition is supported in the Enterprise and Enterprise Plus editions only.

* Veeam Explorer for Microsoft Active Directory does not restore object attributes such as objectSID and objectGUID from the backup. To restore deleted Active Directory objects, Veeam Explorer for Microsoft Active Directory uses existing tombstone objects on the target Active Directory server or objects in the AD Recycle Bin. In this case, the restored object will have its original objectSID and objectGUID. If an object you want to restore does not exist in the tombstone container or recycle bin in the target domain, Active Directory will assign new objectSID and objectGUID attributes to the restored object.

* To restore business-critical objects for which the tombstone object is missing, you can perform authoritative restore of the entire domain from the old DC backups. For more information on tombstone objects, see [this Microsoft article](http://technet.microsoft.com/en-us/library/dd379542%28v%3Dws.10%29.aspx).

* Always use backups that are newer than the tombstone lifetime interval for the Active Directory forest. To determine a tombstone lifetime interval, you can use ADSIEdit or Dsquery. For more information, see [this Microsoft article](http://technet.microsoft.com/en-us/library/cc784932%28v%3Dws.10%29.aspx).

* When you move an object from one domain to another within a forest (for example, using the Movetree.exe utility or any other 3rd party tool), no tombstone for this object will remain in the source Active Directory; such an object cannot be fully recovered to the original domain.

Export

* Veeam Explorer for Microsoft Active Directory uses Lightweight Data Interchange Format to save Active Directory objects and containers to .ldf files. You can make an .ldf file available to the Active Directory Domain Services server by importing it with the ldifde utility. For more information, see [this Microsoft article](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc816781%28v%3Dws.10%29).
* Veeam Explorer for Microsoft Active Directory does not support exporting passwords.

Page updated 2026-07-14

