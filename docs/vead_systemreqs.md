---
title: "System Requirements"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vead_systemreqs.html"
last_updated: "11/7/2025"
product_version: "13.0.1.1071"
---

# System Requirements

In this article

This section lists system requirements for Veeam Explorer for Microsoft Active Directory.

| Component | Requirement |
| --- | --- |
| Microsoft Active Directory Domain Services | Veeam Explorer for Microsoft Active Directory supports restore of domain controllers running on the following operating systems:   * Microsoft Windows Server 2025 * Microsoft Windows Server 2022 * Microsoft Windows Server 2019 * Microsoft Windows Server 2016 * Microsoft Windows Server 2012 R2   Minimum supported domain and forest functional level is Windows 2012 R2. |

Consider the following:

* Veeam Explorer for Microsoft Active Directory does not support Active Directory Lightweight Directory Services (AD LDS).
* Database files created by the domain controller can be opened for object recovery with Veeam Explorer for Microsoft Active Directory only if Veeam Explorer for Microsoft Active Directory is installed on a Windows machine with the same OS version or later than the version of the domain controller OS.
* To open database files, Veeam Explorer for Microsoft Active Directory uses a service dynamic link library (esent.dll) which is installed with Microsoft Active Directory Domain Services and can be found in the %SystemRoot% directory. The Esent.dll file on a machine with Veeam Explorer for Microsoft Active Directory must be of the same version as that of Microsoft Active Directory Domain Services that was used to create database files.

* [For machines with ReFS] The mount server, backup server and the machine where the Veeam Backup & Replication console is installed must support the same or a later ReFS version than that on the source machine. For more information on which OSes support which ReFS version, see [ReFS versions and compatibility matrix](https://gist.github.com/XenoPanther/15d8fad49fbd51c6bd946f2974084ef8#mountability).

Page updated 11/7/2025

Page content applies to build 13.0.1.1071
