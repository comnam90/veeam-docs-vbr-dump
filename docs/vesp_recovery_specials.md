---
title: "Considerations and Limitations"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesp_recovery_specials.html"
last_updated: "11/20/2025"
product_version: "13.0.1.1071"
---

# Considerations and Limitations

In this article

This section lists considerations and limitations of Veeam Explorer for Microsoft SharePoint.

General

Consider the following:

* When Veeam Explorer for Microsoft SharePoint is installed on a server on which both Veeam Backup & Replication and Veeam Backup for Microsoft 365 are installed, the notification settings will be inherited from the Veeam Backup & Replication Global Notification settings.
* Restore using PowerShell Direct, VIX API or vSphere Automation API is not supported.
* Restore of backed-up Microsoft SharePoint data to another Microsoft organization cannot be performed to a target Microsoft SharePoint organization whose version is earlier than the version of the restored backups.

* When restoring your SharePoint data from CDP replicas, consider the following limitations:

* Before you restore custom Microsoft SharePoint lists, you must import their schemas manually. For more information, see [Custom List Settings](vesp_configuring_custom_lists.md).

* When you restore your data from CDP replicas, you can only use long-term (both application-consistent and crash-consistent) restore points. Short-term restore points are not supported.
* You can restore your data from a CDP replica if its CDP policy is currently running. During data restore, the CDP policy does not create new long-term restore points and does not delete existing ones. Short-term restore points are still created.
* You cannot restore application items from a CDP replica in parallel with guest OS file restore, SureReplica, and failover.

* [For Linux-based backup servers] All open Explorer sessions become non-responsive after backup server switchover or failback. To continue browsing and restoring your data, you must reopen the sessions.
* For VMs that run Microsoft SQL Server backed up by Veeam Agent for Microsoft Windows and Microsoft SharePoint backed up by Veeam Backup & Replication, to perform SharePoint item restore, you must start Veeam Explorer for Microsoft SharePoint from the Veeam Backup Browser. To do this, start File Level Recovery for the backup of the required SQL Server VM, and then launch Veeam Explorer for Microsoft SharePoint from the toolbar in the Veeam Backup Browser.

If you start item-level recovery directly for the backup of the SharePoint VM, mapping of a SharePoint site to a content database in the Restore wizard will fail, and Veeam Backup & Replication will display the following error: Unable to find SQL Server VM hosting the content database for the selected SharePoint site.

Backup of the same VM by both Veeam Backup & Replication and Veeam Agent for Microsoft Windows may be required, for example, if Microsoft SQL Server running on the VM operates as part of a failover cluster.

* Veeam Explorer for Microsoft SharePoint must stay open during all data recovery operations. If the user who started the operation logs out or is logged out automatically, the operation will be terminated.

|  |
| --- |
| Note |
| To use an internet proxy server to restore backups created by Veeam Backup for Microsoft 365, make sure to provide appropriate proxy server address and the port number. To do this, go to the Control Panel > Internet Options Connections tab, click LAN Settings, select the Use a proxy server for your LAN check box and specify a proxy server you want to use. Credentials for such a proxy (if needed) will be taken from the Control Panel > Credential Manager > Windows Credentials console.  Consider that this functionality is only available in Veeam Explorer for Microsoft SharePoint that comes as part of the Veeam Backup for Microsoft 365 installation package. |

General Restore Limitations

If your Veeam Explorer for Microsoft SharePoint comes as part of a standalone Veeam Backup for Microsoft 365 installation, you cannot restore from Veeam Backup & Replication backups by default. To enable this functionality, install Veeam Backup & Replication Enterprise edition or higher on the machine.

Status Restore Limitations

Consider the following when planning documents or list items restore:

* If a document or an item was in the Check Out state when the backup was created, the last version of the item will not be restored to the target SharePoint and will be available for viewing only. Previous versions (if any) will be restored.
* If automatic declaration of items as records was originally applied to the list item, the relevant status will not be preserved. Instead, the restored item status will be set in accordance with the target list or target library content approval workflow.
* If the On Hold status was originally applied to the list item, this item will not be restored.

Restore of Documents, Libraries and Lists

Consider the following:

* Versioning settings of SharePoint lists are not preserved during restore.
* Restoring Generic List and Pages Library may fail with the No content type 'XXX' found in web YYY error.
* The Created By field of restored documents is updated with the account performing restore.
* Some values of the Rating Settings of Discussion lists are not restored.
* Make sure to view information about unsupported Microsoft SharePoint lists before restoring them. In particular, hidden lists are not displayed in Veeam Explorer for Microsoft SharePoint after a site backup. Thus, such lists cannot be exported. For more information, see [Unsupported SharePoint Lists](unsupported_sharepoint_lists.md).
* [For restore from Veeam Backup & Replication backups] Restore of values in custom columns is not supported for folders and document sets.

Restore of List Items

Consider that when restoring a list item, Veeam Explorer for Microsoft SharePoint works in the following way:

1. Deletes an existing item.
2. Creates the latest version of the item anew using data from the backup.
3. Checks whether it is declared as a record.
4. If the check is a success, the process finishes.
5. If not, the created version is deleted and item versions are restored sequentially.

This logic leads to the following peculiarities of list item restore:

* If a list or list items column is used as a lookup column in the dependent list, consider that restoring an item from the source list causes the relevant items deletion in the dependent list.
* If a lookup column in the dependent list has the enforced relationship behavior set to Cascade Delete, then restoring an item from the source list may cause item deletion in the dependent list due to Microsoft implementation. For more information, see [this Microsoft article](https://support.office.com/en-au/article/Create-list-relationships-by-using-unique-and-lookup-columns-80a3e0a6-8016-41fb-ad09-8bf16d490632).

To prevent this issue, you should turn off enforced relationship behavior. As a work-around, you can roll-back the SharePoint database using Veeam Explorer for Microsoft SQL Server (see [this section](vesql_user_guide.md)) or roll-back the whole SharePoint server machine to the desired state using any Veeam Backup & Replication recovery option.

Also, consider the following limitations:

* If a lookup column in the dependent list has the enforced relationship behavior set to Restrict Delete, then item restore with Veeam Explorer for Microsoft SharePoint will fail.
* If an .ASPX page references an item using ItemID, this reference may fail to restore (as the item will be created anew with a different ItemID).
* If a list item cannot be deleted (for example, the Welcome page of the site), consider that restore process will restore all versions of the item sequentially without deletions, adding them to Version History.
* The restored Issue list items are assigned a new IssueID.
* Restore of the Time Card list is not supported.

Restore of List Items with Links (Attachments)

Consider the following when planning for the restore of list items with links (attachments):

* If the retention policy for the target list or target document library was configured to declare items as records automatically, only the last version of the item will be restored to the target list or target document library. Target retention policy settings will be applied to the restored item. However, links (attachments) will not be restored.
* Alternatively (with different retention policy settings), all versions of the original item will be restored to the target list or target document library; item links (attachments) will be restored only if such item does not exist on target SharePoint.
* If automatic declaration of items as records was originally applied to the list item, this item will not be restored.

Restore of Items with Custom Content Type

For item restore, Veeam Explorer for Microsoft SharePoint uses content types that exist in the target library or list. If you restore an item with a custom content type, and the target location does not contain this content type, the restore process will fail with the following error: Cannot find corresponding Content-Type for: 15\_.000. Original ContentTypeID: ‘XXX’.

Restore of Surveys

Consider the following limitations when planning for the restore of surveys, survey questions and responses:

* Survey items can be restored to a new survey, created automatically by Veeam Explorer for Microsoft SharePoint in the specified destination instead of the previously deleted survey. However, if a new survey is created by user from scratch (not replacing a deleted one), items cannot be restored to such a survey.
* A survey can be restored to an existing target survey only if that target survey includes at least one item (question) same as survey questions stored in the content database.
* If a survey question was not answered completely in the source survey, after restore the response status in the target survey will be set to Completed, anyway.
* When restoring a single response to a survey, target response item with the same number will be deleted and restored item will be placed in the target survey after the last numbered response.

For example, if the target survey has responses numbered from 1 to 15 and you try to restore a response that used to be number 6 on the source, target response number 6 will be deleted, and the restored response will be assigned number 16.

Restore of Sites

Consider the following:

* When restoring site collections, make sure that such collections exist in the target location; Veeam Explorer for Microsoft SharePoint does not create site collections.

* If you plan to restore SharePoint site pages, consider that Veeam Explorer for Microsoft SharePoint does not support restore of items that are not stored in the SharePoint content database (in particular, pages, page references and items based on default templates). Such items cannot be restored (neither by Restore nor by Save menu option), except for data from Wiki Content (text and images), which is stored in the database. Thus, site pages that contain only text and images can be restored and displayed properly.

|  |
| --- |
| Note |
| Consider the following:   * In case you attempt to restore such items, the following error message will be logged: Item <item> is skipped: restoration of items based on SharePoint default template is not supported. * In case you attempt to save such items, the following error message will be logged: Unable to save document <item>. Document content is not available. |

Export and Import

Consider the following:

* In on-premises Microsoft SharePoint organizations, importing exported Picture Library may result in IDs changed for some items.
* Importing an exported Project Tasks list does not preserve column order.
* Importing an exported SharePoint list does not preserve Validation Settings.
* Export is unavailable for backups created by Veeam Backup for Microsoft 365. The operation is available only for backups created by Veeam Backup & Replication.
* Make sure to view information about unsupported Microsoft SharePoint lists before exporting them. In particular, hidden lists are not displayed in Veeam Explorer for Microsoft SharePoint after a site backup. Thus, such lists cannot be exported. For more information, see [Unsupported SharePoint Lists](unsupported_sharepoint_lists.md).
* Export of empty SharePoint folders is not supported.

Data Type Limitations

Consider the column (field) data type when planning for the restore of your SharePoint libraries or lists:

* If source column (field) data type was set to Lookup, but the referenced list or library was deleted, such columns (fields) will not be restored even if you restore that referenced list. The reason is that if referenced list is deleted, the reference (link) to that list is no longer valid.
* If source column (field) data type was set to Managed Metadata, such columns (fields) will not be restored.

Workflow-Related Considerations

You may need to restore the items originally belonging to a list with no content approval required, to another list. If you try to restore such items to a list that requires content approval, item version and status will be modified in the following way:

* If a target list is configured to include major versions only, then all versions of restored item will become major (despite the original versioning); item status will be set to Pending.
* If a target list is configured to include both major and minor versions, then all versions of restored item will become minor (despite the original versioning); item status will be set in the following way:

* If the last version (original) was major — status will be set to Pending.
* If the last version was minor — status will be set to Draft.

Also, consider the following when planning for the restore of list items (with or without content approval originally required):

* If the retention policy for the target list or target document library was configured to declare items as records automatically, only the last version of the item will be restored to the target list or target document library. Target retention policy settings will be applied to the restored item. Besides, if the Require content approval for submitted items option was enabled for the original list, then the item status will be set to Pending after restore.
* Alternatively (with different retention policy settings), all versions of the original item will be restored to the target list or target document library. Besides, if the Require content approval for submitted items option was enabled for the original list, then after restore the item status in the content approval workflow will be also restored, except for the states listed. For more information, see [Status Restore Limitations](#status_restore_lim).

Page updated 11/20/2025

Page content applies to build 13.0.1.1071
