---
title: "Deleting CloudFormation Stack"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_uninstall_cloudformation.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Deleting CloudFormation Stack


When you deploy a backup appliance from AWS Marketplace, it is deployed using an AWS CloudFormation stack. In AWS CloudFormation, a stack is a collection of AWS services and resources that you can manage as a single unit. To uninstall the backup appliance, you must delete the CloudFormation stack from AWS. For more information on working with stacks, see [AWS Documentation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacks.html).

To delete the CloudFormation stack, perform the following steps:

1. Log in to the AWS Management Console using credentials of an AWS account where the backup appliance is deployed.
2. Use the region selector in the upper-right corner of the page to select the AWS Region in which the backup appliance resides.
3. Navigate to Services > CloudFormation.
4. From the Stacks list, select the CloudFormation stack created while deploying the backup appliance.
5. Click Delete.
6. In the confirmation window, click Delete stack to acknowledge deletion.

|  |
| --- |
| Note |
| * After you acknowledge the operation, the CloudFormation stack will acquire the DELETE\_IN\_PROGRESS state. When all AWS resources included in the stack are successfully deleted, the stack will acquire the DELETE\_COMPLETE state. By default, deleted CloudFormation stacks are not displayed in the AWS Management Console. To learn how to view deleted stacks and to troubleshoot deletion issues, see [AWS Documentation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-console-delete-stack.html).  * If a backup appliance managed by the Veeam Backup & Replication server has been upgraded from the Veeam Backup & Replication console, you will encounter the issue while deleting the CloudFormation stack of this appliance — you will not be able to delete it on the first try. To work around the issue, retry deleting stuck and choose the Force delete this entire stack option. |

Page updated 2026-05-20

