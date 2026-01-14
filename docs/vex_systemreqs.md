---
title: "System Requirements"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vex_systemreqs.html"
last_updated: "11/7/2025"
product_version: "13.0.1.1071"
---

# System Requirements

In this article

This section lists system requirements for Veeam Explorer for Microsoft Exchange.

The set of supported Microsoft Exchange versions depends on the product Veeam Explorer for Microsoft Exchange is installed with: Veeam Backup & Replication or Veeam Backup for Microsoft 365.

| Product | Requirement |
| --- | --- |
| Veeam Backup & Replication | Veeam Explorer for Microsoft Exchange supports restore of the following Microsoft Exchange versions:  * Microsoft Exchange Server Subscription Edition  * Microsoft Exchange Server 2019 * Microsoft Exchange Server 2016 |
| Veeam Backup for Microsoft 365 | Veeam Explorer for Microsoft Exchange supports restore of the following Microsoft Exchange versions:  * Microsoft 365 Exchange Online   [Microsoft 365 and Office 365 service families](https://docs.microsoft.com/en-us/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options#service-families-and-plans), standalone services and plans for Business, Education, and Government\* hosted by Microsoft are supported. For more information about system requirements and limitations for Microsoft 365, see [this Microsoft article](https://www.microsoft.com/en-us/microsoft-365/microsoft-365-and-office-resources#Office365forBEG).   * Microsoft Exchange Server 2019 (on-premises) * Microsoft Exchange Server 2016 (on-premises) * Microsoft Exchange Server 2013 (on-premises) |

\*Government support is experimental. For more information on Veeam experimental support, see [this Veeam KB article](https://www.veeam.com/kb2976).

Consider the following:

* To work with database files, Veeam Explorer for Microsoft Exchange requires a dynamic link library ese.dll supplied with Microsoft Exchange. The ese.dll file must be of the same version as that of Microsoft Exchange in which database files were created.
* To restore data that was backed up by Veeam Backup for Microsoft 365 using PowerShell, make sure to install Windows PowerShell 7.4.2 or later.
* [For machines with ReFS] The mount server, backup server and the machine where the console is installed must support the same or a later ReFS version than that on the source machine. For more information on which OSes support which ReFS version, see [ReFS versions and compatibility matrix](https://gist.github.com/XenoPanther/15d8fad49fbd51c6bd946f2974084ef8#mountability).

Page updated 11/7/2025

Page content applies to build 13.0.1.1071
