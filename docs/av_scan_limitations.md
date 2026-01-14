---
title: "Requirements and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/av_scan_limitations.html"
last_updated: "9/19/2025"
product_version: "13.0.1.1071"
---

# Requirements and Limitations

In this article

The antivirus scan has the following requirements and limitations:

* If you plan to use the antivirus scan feature for secure restore, the Linux mount server role must not be assigned to a Linux machine deployed from Veeam Software Appliance or Veeam Infrastructure Appliance.
* The antivirus software must be installed on the mount server and support the command line interface (CLI).
* The antivirus configuration file must be located on the mount server and properly configured. For details, see [Antivirus Configuration File](av_scan_xml.md).

* If you install several antivirus software on the mount server, the restore session may fail because of the antivirus conflict and file access problems. To avoid such issues, use only one antivirus software.

Page updated 9/19/2025

Page content applies to build 13.0.1.1071
