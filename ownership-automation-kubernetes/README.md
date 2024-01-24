## Ownership Problem Notifications
![workflow](https://raw.githubusercontent.com/popecruzdt/dt-workflow-samples/main/ownership-automation-kubernetes/img/workflow.png)

## Summary:
This sample workflow automates the ownership propagation for Kubernetes using tags. Documentation: https://docs.dynatrace.com/docs/manage/ownership

#### Ownership Propagation
  * Kubernetes Cluster (based on Kubernetes Cluster Node labels)
  * Service (based on Kubernetes Workload labels)

## Prerequisites:
#### Configure Ownership
  * Create and manage owners: https://docs.dynatrace.com/docs/manage/ownership/ownership-teams
  * Assign owners to entities: https://docs.dynatrace.com/docs/manage/ownership/assign-ownership
  * Follow best practices: https://docs.dynatrace.com/docs/manage/ownership/best-practices
#### Label Kubernetes Cluster Nodes
  * Apply a label `dt.owner` to the Kubernetes Cluster NodeGroup
  * Documentation: https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/
#### Label Kubernetes Workloads
  * Apply a label `dt.owner` to the Kubernetes Workloads
  * Documentation: https://docs.dynatrace.com/docs/manage/ownership/assign-ownership#kubernetes

## Deployment:
#### Upload the Workflow Template into your Dynatrace SaaS tenant
  * Download `wftpl_ownership_automation_kubernetes.yaml`
  * From the Workflows App, choose Upload 

## Setup:
#### Configure the execution trigger
  * Configure the workflow to trigger on a schedule or on-demand
  * It is recommended to run the workflow once per day

#### Filter Kubernetes Workfloads and Services by Kubernetes Cluster (optional)
  * Large environments may have thousands of services, consider modifying the DQL tasks to filter the scope of the automation to a specific cluster
  * Modify the `dql_query_workloads` task, remove the commented commands, update the value of `KUBERNETES_CLUSTER-*`
  * Modify the `dql_query_services` task, remove the commented commands, update the value of `KUBERNETES_CLUSTER-*`