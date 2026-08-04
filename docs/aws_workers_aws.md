---
title: "Worker Instances"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_workers_aws.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Worker Instances


To optimize the cost of running worker instances, the backup appliance first attempts to use the c6a or c6i instance family for default worker profiles, depending on availability at the worker instance location. If neither instance family is available, the backup appliance uses the instance types listed in the table below. Note that the size of the worker instance depends on the total EBS volume size.

Worker Instances

| Worker Profile | Default Instance Type | Usage |
| Small | c5.large | Processing EBS volumes under 1024 GB (default) |
| Medium | c5.2xlarge | Processing EBS volumes between 1024 GB and 16 TB (default) |
| Large | c5.4xlarge | Processing EBS volumes over 16 TB (default) |
| Archiving | c5.2xlarge | Processing EBS volumes under 6 TB |
| c5.4xlarge | Processing EBS volumes over 6 TB |

If you want initial full backups to be processed quickly, it is recommended that you use a larger worker instance profile, and then change it to a smaller profile for incremental backup. You can change worker instance profile settings on a regional basis, so make sure that the worker instance size is appropriate to process the largest workload within the required time.

For more information on AWS pricing, see [AWS Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-on-demand-instances.html).

Related Topics

* [Worker Instances](aws_worker_instances.md)
* [Managing Worker Profiles](aws_worker_profiles.md)

Page updated 2026-07-23

