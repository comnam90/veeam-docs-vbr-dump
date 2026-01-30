---
title: "Editing and Deleting Virtual Labs"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/edit_delete_vlab_hv.html"
last_updated: "9/3/2025"
product_version: "13.0.1.1071"
---

# Editing and Deleting Virtual Labs


You can edit settings of a virtual lab or delete the virtual lab.

Always use Veeam Backup & Replication to modify or delete a virtual lab. If you change lab settings or delete any of its components from outside, for example, in Hyper-V Manager, the lab will be corrupted and its component such as the created virtual switch will remain in the virtual infrastructure.

To edit settings of a virtual lab:

1. Open the Backup Infrastructure view.
2. In the inventory pane, select Virtual Labs under SureBackup.
3. In the working area, select a virtual lab and click Edit Virtual Lab on the ribbon or right-click the virtual lab and select Properties.
4. Edit virtual lab settings as required.

To remove a virtual lab:

1. Open the Backup Infrastructure view.
2. In the inventory pane, select Virtual Labs under SureBackup.
3. In the working area, select a virtual lab and click Remove on the ribbon or right-click the virtual lab and select Remove.
4. If you want to remove virtual lab objects from the virtual environment, in the displayed window select the Remove virtual lab objects from host check box. If you do not select this option, Veeam Backup & Replication will disconnect the virtual lab from the backup server. You will be able to connect to this virtual lab later.

[![Editing and Deleting Virtual Labs](images/delete_vlab_hv.webp)](images/delete_vlab_hv.webp)


