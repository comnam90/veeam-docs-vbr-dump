---
title: "Step 5. Specify Guest Processing Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_add_policy_guest_processing.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Specify Guest Processing Settings


If you want to back up EC2 instances that are currently running, you can configure guest processing settings at the Guest Processing step of the wizard. These settings allow you to specify what actions the backup appliance will perform when communicating with the guest OSes.

Particularly, you can specify the following guest processing settings:

* [Application-aware processing](aws_add_policy_app_aware_processing.md)

Application-aware processing is a Veeam technology that is based on Volume Shadow Copy Service (VSS), a Microsoft solution responsible for quiescing applications on EC2 instances and creating a consistent view of application data. For more information on VSS, see [Microsoft Docs](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2003/cc785914%28v%3Dws.10%29?redirectedfrom=MSDN).

You can enable application-aware processing for Windows-based EC2 instances running VSS-aware applications to ensure that the applications will be able to recover successfully, without data loss.

* [Guest scripting](aws_add_policy_scripting.md)

Guest scripting allows the backup appliance to run custom scripts on processed EC2 instances before and after backup operations.

For example, you can instruct the backup appliance to execute a pre-snapshot script on an EC2 instance to quiesce its applications — this will allow the appliance to create a transactionally consistent snapshot while no write operations occur on on the instance volumes. After the snapshot is created, a post-snapshot script can start the applications again.

Limitations and Requirements

To be able to communicate with instance guest OSes, the backup appliance uses the AWS Systems Manager (SSM) service. Thus, if you plan to enable guest processing for EC2 instances protected by the policy, you must consider the following:

* The backup appliance must have outbound internet access to the SSM service.
* * EC2 instances must have the 443 network port opened for outbound internet access to the SSM service.
  * The EC2 instances must be configured to communicate with AWS System Manager. To learn how to configure instance permissions for Systems Manager, see [AWS Documentation](https://docs.aws.amazon.com/systems-manager/latest/userguide/setup-instance-permissions.html).
  * SSM Agent must be installed on the EC2 instances. To learn how to install SSM Agent, see [AWS Documentation](https://docs.aws.amazon.com/systems-manager/latest/userguide/ssm-agent.html).

Note that SSM Agent is already preinstalled on EC2 instances launched from certain AMIs.

For more information on the SSM service, see [AWS Documentation](https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html).

Page updated 2026-05-21

