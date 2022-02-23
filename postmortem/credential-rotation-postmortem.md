## Incident summary

The event was triggered by changing IAM credentials at 02/21/22 23:30. 

## Leadup

At 23:00 on 02/22/22, (9hrs before the incident in question), a change was introduced to k8s configmap and secrets of apicore, web-ui, velero, and gobackup in order to update the AWS IAM credentials.

This change resulted in accessability issues for services that uses AWS API such as S3.

## Fault

Although we've update configmap and secrets for the following services: apicore, web-ui, velero, and gobackup we didn't do a manual restart expecting it to have auto-restarted on it's own after the keys have been updated.

## Impact

This incident affected customers and services using web-ui such as apicore and importer, who experienced 403 forbidden issues while viewing or uploading S3 assets.

## Detection

This incident was detected when one of our customers alerted DevOps team on slack.

After very 90 days of IAM credential rotation, automated test and verification script  will be set up by Infra team so that this incident can be avoided.

## Response

After receiving the slack alert, Jeane and Ed came online to investigate. 

## Recovery

By activitating the old IAM security keys the services was able to re-connect to AWS API and S3 API operations. While infra team investigates further before removing the old keys.

See security/aws-credential-rotation.md for runbook remediation
