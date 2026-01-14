---
title: "Naming Conventions"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/naming_conventions.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Naming Conventions

In this article

Do not use Microsoft Windows reserved names for names of the backup server, managed servers, backup repositories, jobs, tenants and other objects created in Veeam Backup & Replication: CON, PRN, AUX, NUL, COM1, COM2, COM3, COM4, COM5, COM6, COM7, COM8, COM9, LPT1, LPT2, LPT3, LPT4, LPT5, LPT6, LPT7, LPT8 and LPT9.

If you plan to store backups on a repository operating in the per-machine mode, do not use Microsoft Windows reserved names for names of the virtual machines to back up.

If you use a reserved name, Veeam Backup & Replication may not work as expected. For more information on naming conventions in Microsoft Windows, see [Microsoft Docs](https://msdn.microsoft.com/en-us/library/aa365247.aspx?f=255&MSPPError=-2147217396#naming_conventions).

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
