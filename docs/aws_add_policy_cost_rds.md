---
title: "Step 10. Review Estimated Cost"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_add_policy_cost_rds.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 10. Review Estimated Cost


[This step applies only if you have created a schedule for the backup policy at the Schedule step of the wizard]

At the Cost Estimation step of the wizard, review the estimated monthly cost of AWS services and resources that will be consumed to protect the instances added to the backup policy. The total estimated cost includes the following:

* The cost of creating and maintaining cloud-native snapshots of the instances.

For each instance included in the backup policy, the backup appliance takes into account the number of restore points to be kept in the snapshot chain, and the configured scheduling settings.

* The cost of creating snapshot replicas and maintaining them in the target AWS Region.

For each instance included in the backup policy, the backup appliance takes into account the number of restore points to be kept in the snapshot chain, and the configured scheduling settings.

* The cost of sending API requests to AWS during data protection operations.

To calculate the estimated cost, the backup appliance uses the capabilities of the [AWS Pricing Calculator](https://calculator.aws/#/?key=new) that estimates the cost of services in USD only. This calculator is intended for informational and estimation purposes only.

|  |
| --- |
| Note |
| Due to technical limitations, the backup appliance does not estimate the cost of creating and maintaining cloud-native snapshots of Aurora DB clusters, the cost of creating and storing in backup repositories image-level backups of RDS instances, and the cost of creating and storing in archive repositories archived backups of RDS instances. |

The estimated cost may occur to be significantly higher due to the snapshot charges. To reduce the cost, you can try to adjust the snapshot retention settings to keep less restore points in the snapshot chain. For more information on cost estimation, see [this Veeam KB article](https://www.veeam.com/kb3054).

|  |
| --- |
| Tip |
| You can save the cost estimation as a .CSV or .XML file. To do that, click Export to and select the necessary format. |

[![Creating RDS Backup Policy](images/aws_rds_backup_cost.webp)](images/aws_rds_backup_cost.webp "Creating RDS Backup Policy")

Related Resources

[How AWS Pricing Works](https://docs.aws.amazon.com/whitepapers/latest/how-aws-pricing-works/welcome.html)

Page updated 2026-05-21

