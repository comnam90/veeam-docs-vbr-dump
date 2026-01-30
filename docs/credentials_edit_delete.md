---
title: "Editing and Deleting Credentials Records"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/credentials_edit_delete.html"
last_updated: "1/11/2024"
product_version: "13.0.1.1071"
---

# Editing and Deleting Credentials Records


You can edit or delete credentials records that you have created. For the system credentials records, you can only change a password and record description. These credentials records cannot be deleted.

To edit a credentials record:

1. From the main menu, select Credentials and Passwords > Datacenter Credentials.
2. Select the credentials record in the list and click Edit.
3. If the credentials record is already used for any component in the backup infrastructure, Veeam Backup & Replication will display a warning. Click Yes to confirm your intention.
4. Edit settings of the credentials record as required.

To delete a credentials record:

1. From the main menu, select Credentials and Passwords > Datacenter Credentials.
2. Select the credentials record in the list and click Remove.

|  |
| --- |
| Note |
| You cannot delete a record that is already used for any component in the backup infrastructure. If you still need to do it, use a temporary record with dummy credentials for the required component and perform the rescan operation for this component. After that, you will be able to delete the record. |

![Editing and Deleting Credentials Records](images/credentials_records_delete.webp)


