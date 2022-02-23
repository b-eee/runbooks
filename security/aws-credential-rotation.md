# AWS credential rotation

As part of AWS Security compliance, we are required to rotate IAM security credentials every 90 days.

## Affected services

Namespace: default
- deployment/apicore
- deployment/web-ui
- deployment/importer

Namespace: dbbackups
- job/gobackup

Namespace: velero
- deployment/velero

## Commands

After new IAM security keys have been created and configmap as well as secrets have been updated with the new keys, the following commands is required to be run in order for the new keys to be used.

```bash
kubectl scale --replicas=0 deployment/apicore -n default
kubectl scale --replicas=3 deployment/apicore -n default

kubectl scale --replicas=0 deployment/importer -n default
kubectl scale --replicas=1 deployment/importer -n default

kubectl scale --replicas=0 deployment/web-ui -n default
kubectl scale --replicas=1 deployment/web-ui -n default

kubectl scale --replicas=0 deployment/velero -n velero
kubectl scale --replicas=1 deployment/velero -n velero
```
