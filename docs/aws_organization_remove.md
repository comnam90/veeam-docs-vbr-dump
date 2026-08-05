---
title: "Removing Organizations"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_organization_remove.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Removing Organizations


The backup appliance allows you to permanently remove an AWS Organization from the appliance configuration database if it is no longer used to perform data protection and disaster recovery operations:

1. Switch to the Configuration page.

1. Navigate to Infrastructure > Organizations.

1. Select the AWS Organization and click Remove.

1. In the Remove Organization window, click Yes to acknowledge the operation.

|  |
| --- |
| Important |
| You cannot remove an AWS Organization or limited scope of organizational units that are specified in the settings of any configured backup policy. |

[![Removing AWS Organizations](images/aws_organizations_remove.webp)](images/aws_organizations_remove.webp "Removing AWS Organizations")

Page updated 2026-05-21

