## Log Permissions Security Context Automation
![Policies](https://raw.githubusercontent.com/popecruzdt/dt-workflow-samples/main/log-permissions-security-context/img/policies.png)

## Summary:
This sample workflow automates the creation of IAM Policies based on observed values of `dt.security_context` attribute for logs.  For each detected security context, a policy is created with a statement providing access to logs with the matching value. Optionally, the policies will be bound/applied to groups with the same name.

## Prerequisites:
#### Logs stored in Grail obtained from OneAgent or Log Ingest API
  * Upgrade to Grail: https://docs.dynatrace.com/docs/observe-and-explore/logs/logs-upgrade/lma-upgrade
  * OneAgent Log Sources: https://docs.dynatrace.com/docs/observe-and-explore/logs/log-management-and-analytics/lma-log-ingestion-via-oa
  * Log Ingest API: https://docs.dynatrace.com/docs/observe-and-explore/logs/log-management-and-analytics/lma-log-ingestion-via-api
#### Evaluate existing security context values
Query logs for existing security context values:
```
fetch logs, from: now()-24h
| summarize count(), by: {dt.security_context}
| fields dt.security_context
```
#### Clean up security context values with log processing rules
  * Documentation: https://docs.dynatrace.com/docs/observe-and-explore/logs/log-management-and-analytics/lma-security-context
#### Dynatrace OAuth Client stored in Credential Vault
  * Create a Dynatrace OAuth Client: https://docs.dynatrace.com/docs/manage/account-management/identity-access-management/account-api-oauth
  * OAuth Client Permissions must include `View users and groups`, `Manage users and groups`, `View and manage policies`
  * Copy the `Client ID` and `Client secret` for later use
  * Create a Credential Vault entry of `Type` equals `Token` and `Scope` equals `AppEngine`
  * Copy the `Credential ID` for later use
  

## Deployment:
#### Upload the Workflow Template into your Dynatrace SaaS tenant
  * Download `wftpl_log_permissions_security_context.yaml`
  * From the Workflows App, choose Upload 

## Setup:
#### Modify the fixed time trigger
  * Configure the fixed time trigger by modifying the `Run at` and `Timezone` settings
  * It is recommended to run every day at the same time (once every 24 hours)
#### Set the workflow parameters
  * Configure the workflow parameters to work in your environment
  * Modify the variables in the `js_set_parameters` task