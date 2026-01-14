---
title: "Editing Protection Group Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/protection_group_edit.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Editing Protection Group Settings

In this article

You can edit the settings of a protection group. This operation may be required, if you want to add/remove computers to/from a protection group or change settings for protected computers discovery and Veeam components deployment defined in the properties of the protection group.

|  |
| --- |
| NOTE |
| Consider the following:   * You cannot change the type of a protection group when editing protection group settings.  * For the Manually Added protection group, you can change only a limited number of settings. In particular, you can edit protected computers discovery and Veeam components deployment options (except for changing the distribution server for the protection group). You can also remove from this protection group computers that are no longer included in an application backup policy.  * You cannot edit settings of default protection groups that act as filters used to display protected computers of a specific type: Unmanaged, Out of Date, Offline and Untrusted. |

To edit protection group settings:

1. Open the Inventory view.
2. In the inventory pane, expand the Physical Infrastructure node.
3. In the inventory pane, select the protection group that you want to edit and click Edit Group on the ribbon or right-click the protection group that you want to edit and select Edit Group.
4. Edit protection group settings as required.

[![Edit Protection Group Settings](images/protection_group_edit.webp)](images/protection_group_edit.webp "Edit Protection Group Settings")

Page updated 9/2/2025

Page content applies to build 13.0.1.1071
