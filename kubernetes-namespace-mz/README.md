## Kubernetes Namespace Management Zone Automation
![Kubernetes Namespace](https://raw.githubusercontent.com/popecruzdt/dt-workflow-samples/main/kubernetes-namespace-mz/img/k8s-mz.png)

## Summary:
This sample workflow automates the creation of management zones based on monitored kubernetes namespaces.  For each detected kubernetes namespace, a management zone is created with multiple rules to cover the broad scope of entity types relevant to kubernetes.

## Prerequisites:
#### Dynatrace OneAgent deployed on Kubernetes using Dynatrace Operator
  * Dynatrace OneAgent automatically creates Process Groups for Kubernetes workloads
  * Dynatrace Smartscape automatically relates Process Groups to Kubernetes namespaces
  * This workflow uses the relationship between Process Groups and Kubernetes namespaces
#### Dynatrace API token stored in Credential Vault
  * Create a Dynatrace API token with `ReadConfig` and `WriteConfig` scopes
  * Create a Credential Vault entry of `Type` equals `Token` and `Scope` equals `AppEngine`
  * Copy the `Credential ID` for later use

## Deployment:
#### Upload the Workflow Template into your Dynatrace SaaS tenant
  * Download `wftpl_kubernetes_namespace_mz.yaml`
  * From the Workflows App, choose Upload 

## Setup:
#### Modify the fixed time trigger
  * Configure the fixed time trigger by modifying the `Run at` and `Timezone` settings
  * It is recommended to run every day at the same time (once every 24 hours)
#### Set the workflow parameters
  * Configure the workflow parameters to work in your environment
  * Modify the variables in the `js_set_parameters` task