---
title: "Creating Custom Maintenance Mode Notification"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cc_maintenance_message.html"
last_updated: "2/8/2024"
product_version: "13.0.1.1071"
---


In this article

If a tenant backup or backup copy job is performing at the time when the SP backup server is operating in the Maintenance mode, the Maintenance mode notification is displayed in the job statistics window. By default, Veeam Backup & Replication is set up to display the following Maintenance mode notification: Service provider is currently undergoing scheduled maintenance. The SP can use the default notification or create a custom message, if necessary. The created notification will be displayed to all tenants who use cloud resources of the SP instead of the default one.

To create a custom Maintenance mode notification:

1. On the SP Veeam backup server, launch the Registry Editor.
2. Navigate to the key: HKEY\_LOCAL\_MACHINE\SOFTWARE\Veeam\Veeam Backup and Replication\.
3. Create a new String Value with the name CloudMaintenanceModeMessage, and set its data to the Maintenance mode notification that you want to display on the tenant side.

|  |
| --- |
| Note |
| Consider the following:   * Veeam Backup & Replication uses the UTF-8 encoding for the Maintenance mode notification. This lets you include characters of a large number of languages in your custom Maintenance mode message. * Veeam Backup & Replication has no limitations on the maximum length of a custom Maintenance mode notification. However, it is recommended to create messages that contain 300 to 350 symbols or less. Longer notifications may be displayed incorrectly in the Veeam Backup & Replication or Veeam Agent for Microsoft Windows user interface. |

Related Topics

[Maintenance Mode](cc_maintenance_mode.md)

Page updated 2/8/2024

Page content applies to build 13.0.1.1071
