---
title: Amazon Web Services
aliases:
  - AWS
tags: [ops, security, devops, sre, ops]
---

**Amazon Web Services (AWS)** is a hosted services offering from Amazon. Various
-- tons -- of services, as of 2019.

## Services
### IAM
#### Allowing console login for IAM users without an AWS console password
  * Allow federation to the same account for the user.

TODO: it probably isn't a solution. See further below.

Users can then login to themselves via CLI federation (e.g. `aws-vault login`).

Note: Keep in mind that this way, users with MFA are allowed to login without
MFA, so make sure you restrict their permissions if they have no MFA in the
session.

There are some problems with this approach: namely, when federating, you can't
use `${aws:username}`, even when you federate into a user instead of a role, so
IAM permissions become really fuckin' awkward. In fact it's probably not an
idea.

If you ever want your users to access the online AWS console and do anything of
use there, you have to give them a password. Sorry.

### CloudWatch
#### Retrieve billing metrics from CloudWatch
As of 2019-01-25, you must **use `us-east-1` to access CloudWatch billing metric
data**.

[AWS link](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html)
