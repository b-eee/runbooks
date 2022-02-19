# Root account mis-use runbook

## Objective
The objective of this runbook is to provide specific guidance on how to manage Root AWS account compromise. This runbook focuses on the IR lifecycle:

- Establish control.
- Determine impact.
- Recover as needed.
- Investigate the root cause.
- Improve.

## Indicators of compromise 

- Activity that is abnormal for the account.
    - Creation of unexpected EC2 resources.
    - Creation of IAM users.
    - CloudTrail turned off.
    - Cloudwatch turned off.
    - SNS paused.
- Launching of new or unexpected AMIs.
- Changes to the contacts on the account.

## Steps to Remediate – Establish Control

[What do I do if I notice unauthorized activity in my AWS account?](https://aws.amazon.com/premiumsupport/knowledge-center/potential-account-compromise/)

1. Contact AWS Support and TAM as soon as possible.
2. Change and rotate Root password and add an MFA device associated with Root.
3. Rotate passwords, access/secret keys, and CLI commands relevant to remediation steps.
4. Review actions taken by the root user.
5. Open the runbooks for those actions.
6. Close incident.
7. Review the incident and understand what happened.
8. Fix the underlying issues, implement improvements, and update the runbook as needed.

### Further Action Items – Determine Impact

Review created resources and AWS API calls. There are may be items that have been created to allow access in the future. Some things to look at:

- IAM Cross account roles.
- IAM Users.
- S3 buckets.
- EC2 instances.
- CloudTrail
- Security Groups
- GuardDuty
- Security Hub
