---
title: "Step 5. Choose Restore Mode"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_entire_mode.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Choose Restore Mode


At the Restore Mode step of the wizard, choose whether you want to restore the selected EC2 instance to the original or to a custom location. If you select the Restore to new location, or with different settings option, specify the target AWS Region where the restored EC2 instance will operate.

|  |
| --- |
| Important |
| * For the backup appliance to be able to perform restore to the original location, the IAM role specified at the [Account](aws_restore_entire_account.md) step of the wizard must belong to the AWS account to which the source EC2 instance belongs.  * Veeam Plug-in for AWS does not support restore to the original location if the source EC2 instance is still present in the location and [stop protection](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-stop-protection.html) or [termination protection](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/terminating-instances.html#Using_ChangingDisableAPITermination) are enabled for the instance.   For more information on limitations and considerations, see [Before You Begin](aws_restore_entire_before_you_begin.md). |

[![Restoring Entire EC2 Instance](images/aws_restore_entire_mode.webp)](images/aws_restore_entire_mode.webp "Restoring Entire EC2 Instance")

Page updated 2026-05-22

