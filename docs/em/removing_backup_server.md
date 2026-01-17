---
title: "Removing Backup Servers"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/removing_backup_server.html"
last_updated: "10/30/2025"
product_version: "13.0.1.1071"
---


In this article

To disconnect a backup server added to the Veeam Backup Enterprise Manager infrastructure, you must remove it from Enterprise Manager. After you remove a backup server, Enterprise Manager stops collecting data from the backup server and showing the backup server data such as jobs, backed up machines and so on.

On the backup server side, a record about the Enterprise Manager instance is deleted from the configuration database. The backup server continues using the license that Enterprise Manager pushed to the backup server until you remove the license or install a new one.

To remove a backup server, do the following:

1. Log in to Enterprise Manager using an administrative account.
2. To open the Configuration view, click Configuration in the upper-right corner.
3. Select the Backup Servers section on the left of the Configuration view.
4. Select a backup sever from the list and click Remove on the toolbar.

Alternatively, you can right-click the selected backup server and select Remove.

1. In the open window, click Yes to confirm the removal.

Page updated 10/30/2025

Page content applies to build 13.0.1.1071
