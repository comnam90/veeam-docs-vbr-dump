---
title: "Editing Storage Templates"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_storage_edit.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Editing Storage Templates


|  |
| --- |
| Important |
| If a storage template is already assigned to at least one SLA-based backup policy and the backup appliance has already stored image-level backups in the specified location, modifying its location settings will cause the backup appliance to start a new chain of restore points in this location. The old chain of restore points will be retained in the previous location until removed according to retention settings specified for the SLA template assigned to this SLA-based backup policy. |

For each storage template, you can modify settings configured while creating the template:

1. Switch to the Configuration page.
2. Navigate to Policy Templates > Storage and click Edit.
3. Complete the Edit Storage Template wizard:

1. To provide a new name and description for the template, follow the instructions provided in section [Adding Storage Templates](aws_storage_add_name.md) (step 2).
2. To modify the configured location settings, follow the instructions provided in section [Adding Storage Templates](aws_storage_add_location_settings.md) (step 3).
3. At the Summary step of the wizard, review configuration information and click Finish to confirm the changes.

|  |
| --- |
| Tip |
| After you click Finish, the backup appliance will update the timestamp in the Last Modified column on the Storage page, regardless of whether you have actually modified the template settings or not. If you want to simply view the configured settings without making any changes, click View Info. |

[![Editing Storage Template](images/aws_storage_edit.webp)](images/aws_storage_edit.webp "Editing Storage Template")

Page updated 2026-05-20

