---
title: "How Restoring Objects from Tape Works"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/tape_restoring_objects_from_tape.html"
last_updated: "11/12/2025"
product_version: "13.0.1.1071"
---

# How Restoring Objects from Tape Works


When Veeam Backup & Replication restores object storage data archived to tape, it performs the following operations:

1. Veeam Backup & Replication checks the Tape Catalog in the configuration database to discover the tapes containing the needed restore point of the objects. If the tapes are offline, Veeam Backup & Replication prompts the user to insert the required tapes.
2. Veeam Backup & Replication connects to Veeam Data Mover deployed on a tape server.
3. Veeam Data Mover copies the relevant objects from the tapes.
4. The copied objects are transferred to a chosen target location, original or new one. If the target location is object storage, the role of the gateway server can be assigned to different components depending on the object storage configuration:

* In case the object storage has automatic gateway selection enabled, the role of the gateway server is assigned to the tape server.
* If you explicitly specify gateway servers for the object storage, Veeam Backup & Replication uses only gateway servers selected in the list.

1. Veeam Backup & Replication updates the Tape Catalog in the configuration database.

![How Restoring Objects from Tape Works](images/tape_restore_object_storage.webp)


