## Ownership Problem Notifications
![workflow](https://raw.githubusercontent.com/popecruzdt/dt-workflow-samples/main/ownership-problem-notifications/img/workflow.png)
![problem_comments](https://raw.githubusercontent.com/popecruzdt/dt-workflow-samples/main/ownership-problem-notifications/img/problem_comments.png)

## Summary:
This sample workflow automates the problem notification destination based on details configured in the entity's ownership.  Documentation: https://docs.dynatrace.com/docs/manage/ownership

## Prerequisites:
#### Configure Ownership
  * Create and manage owners: https://docs.dynatrace.com/docs/manage/ownership/ownership-teams
  * Assign owners to entities: https://docs.dynatrace.com/docs/manage/ownership/assign-ownership
  * Follow best practices: https://docs.dynatrace.com/docs/manage/ownership/best-practices
#### Slack Notifications (optional)
  * Configure Slack for Workflows: https://docs.dynatrace.com/docs/platform-modules/automations/workflows/actions/slack
  * For teams that require Slack notifications, configure Ownership teams with Slack channel details
#### Teams Notifications (optional)
  * Configure Teams for Workflows: https://docs.dynatrace.com/docs/platform-modules/automations/workflows/actions/microsoft-teams
  * For teams that require Teams notifications, configure Ownership teams with Teams details
#### Jira Notifications (optional)
  * Configure Jira for Workflows: https://docs.dynatrace.com/docs/platform-modules/automations/workflows/actions/jira
  * For teams that require Jira notifications, configure Ownership teams with Jira details
#### Email (Microsoft 365) Notifications (optional)
  * Configure M365 for Workflows: https://docs.dynatrace.com/docs/platform-modules/automations/workflows/actions/microsoft365
  * For teams that require Email notifications, configure Ownership teams with Email details
#### Webhook Notifications (optional)
  * Create a Credential Vault entry containing the username and password (Basic Auth) or token (Api Token) values required to authenticate with the Webhook
  * Configure an `Additional Information` on the Ownership teams named `Webhook Notification` with the value set to the Credential Vault entry and the URL set to the webhook endpoint
  * Depending on the authentication mechanism of the Webhook, additional code modifications of the workflow may be required
![webhook](https://raw.githubusercontent.com/popecruzdt/dt-workflow-samples/main/ownership-problem-notifications/img/webhook.png)
  
## Deployment:
#### Upload the Workflow Template into your Dynatrace SaaS tenant
  * Download `wftpl_ownership_problem_notifications.yaml`
  * From the Workflows App, choose Upload 

## Setup:
#### Modify the Davis problem trigger
  * Configure the parameters of the Davis problem trigger to execute when Davis detects problems that require a notification
![trigger](https://raw.githubusercontent.com/popecruzdt/dt-workflow-samples/main/ownership-problem-notifications/img/trigger.png)

#### Set the workflow parameters
  * Configure the workflow parameters to work in your environment
  * Modify the variables in the `js_set_parameters` task