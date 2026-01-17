---
title: "Deleting Enterprise Manager Keyset"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_delete_em_keyset.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---


In this article

You can delete an Enterprise Manager keyset in case it is no longer needed.

Only keys in the Inactive state can be deleted. You cannot delete keys that are currently active.

To delete a keyset:

1. In Veeam Backup Enterprise Manager, open the Settings section of the Configuration view.
2. On the Key Management tab, in the Managed keys section, select the necessary keyset in the list and click Delete Key.

|  |
| --- |
| Important |
| It is strongly recommended that you export a keyset before you delete it. If you delete a keyset and do not make its backup copy, you will not be able to restore data from a backup or tape encrypted with keys from this keyset in case a password is lost. For more information, see [Exporting and Importing Enterprise Manager Keyset](em_export_import_keys.md). |

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
