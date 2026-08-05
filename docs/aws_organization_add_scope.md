---
title: "Step 4. Specify Organization Scope"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_organization_add_scope.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 4. Specify Organization Scope


At the Scope step of the wizard, choose whether you want the backup appliance to have full or limited access to resources within the AWS Organization.

If you select the Limited scope option, you must also specify the scope explicitly — select organizational units containing resources that you plan to protect. To do that, click Add; then, select the necessary units to include in the scope and provide a unique name for it in the Specify scope of organizational units window.

|  |
| --- |
| Tips |
| * If the list of available organizational units does not show the units that you want to include, click Rescan to launch the data collection process. As soon as the process is over, the backup appliance will update the unit list. * You can specify multiple scopes to enable configuration flexibility while applying different data protection scenarios for resources from different organizational units. |

After you define the organization scope (either an entire AWS Organization or a limited scope of organizational units), you will be able to specify this scope while creating backup policies and completing restore wizards to allow the backup appliance to perform data protection and disaster recovery operations. For more information, see sections [Performing Backup](aws_performing_backup_web_ui.md) and [Performing Restore](aws_recovery.md).

[![Adding AWS Organization](images/aws_organization_scopes.webp)](images/aws_organization_scopes.webp "Adding AWS Organization")

Page updated 2026-05-20

