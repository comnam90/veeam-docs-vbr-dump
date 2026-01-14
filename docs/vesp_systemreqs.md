---
title: "System Requirements"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesp_systemreqs.html"
last_updated: "11/7/2025"
product_version: "13.0.1.1071"
---

# System Requirements

In this article

This section lists system requirements for Veeam Explorer for Microsoft SharePoint.

The set of supported Microsoft SharePoint versions depends on the product Veeam Explorer for Microsoft SharePoint is installed with: Veeam Backup & Replication or Veeam Backup for Microsoft 365.

| Product | Requirement |
| --- | --- |
| Veeam Backup & Replication | Veeam Explorer for Microsoft SharePoint supports restore of the following Microsoft SharePoint versions:  * Microsoft SharePoint Server Subscription Edition * Microsoft SharePoint Server 2019  * Microsoft SharePoint Server 2016   All editions are supported (Subscription, Foundation, Standard, Enterprise).  Restore of Microsoft SharePoint data may require an available staging Microsoft SQL Server. To learn how to configure this server, see [Staging SQL Server Settings](https://helpcenter.veeam.com/docs/vbr/explorers/vesp_configuring_sql_settings.html?ver=13). |
| Veeam Backup for Microsoft 365 | Veeam Explorer for Microsoft SharePoint supports restore of the following Microsoft SharePoint versions:  * Microsoft 365 SharePoint Online   [Microsoft 365 and Office 365 service families](https://docs.microsoft.com/en-us/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options#service-families-and-plans), standalone services and plans for Business, Education, and Government\* hosted by Microsoft are supported. For more information about system requirements and limitations for Microsoft 365, see [this Microsoft article](https://www.microsoft.com/en-us/microsoft-365/microsoft-365-and-office-resources#Office365forBEG).   * Microsoft SharePoint Server 2019   For more information about hardware and software requirements, see [this Microsoft article](https://learn.microsoft.com/en-us/sharepoint/install/hardware-and-software-requirements-2019).   * Microsoft SharePoint Server 2016   For more information about hardware and software requirements, see [this Microsoft article](https://learn.microsoft.com/en-us/sharepoint/install/hardware-and-software-requirements).   * Microsoft SharePoint Server Subscription Edition   For more information about hardware and software requirements, see [this Microsoft article](https://docs.microsoft.com/en-us/sharepoint/install/hardware-and-topology-requirements-for-sharepoint-server-subscription-editon) and [this Microsoft article](https://docs.microsoft.com/en-us/sharepoint/install/software-requirements-for-database-servers-for-sharepoint-server-subscription-edition). |

\*Government support is experimental. For more information on Veeam experimental support, see [this Veeam KB article](https://www.veeam.com/kb2976).

|  |
| --- |
| Note |
| [For machines with ReFS] The mount server, staging server, backup server and the machine where the console is installed must support the same or a later ReFS version than that on the source machine. For more information on which OSes support which ReFS version, see [ReFS versions and compatibility matrix](https://gist.github.com/XenoPanther/15d8fad49fbd51c6bd946f2974084ef8#mountability). |

Page updated 11/7/2025

Page content applies to build 13.0.1.1071
