--8<-- "snippets/send-bizevent/2-getting-started.js"

## Prerequisites

### Environment Setup

1. Workflow Settings - Authorization
2. Slack for Workflows
3. Config Generator
4. Data Generator

## Workflow Settings - Authorization

To run a workflow with your user as the actor (this is the default on workflow creation), you need to authorize the AutomationEngine to use permissions in your name. Note: The AutomationEngine authorization only works for permissions granted to your user.

In your Dynatrace environment, open the Workflows App.

Validate that the following permissions are granted to workflow executions.

![./img//01-workflow-authorization-settings.png](./img//01-workflow-authorization-settings.png)

Primary permissions:

[ x ] app-engine:apps:run - Grants permission to list and run apps and gives basic access to the Launcher

[ x ] app-engine:functions:run - Grants permission to use the function-executor

[ x ] app-settings:objects:read - Grants permission to read app settings objects belonging to the schema

Secondary permissions:

[ x ] select all

## Slack for Workflows

In your Dynatrace environment, search, locate, and open the Hub App.

Search for the App `Slack for Workflows` and click on it.

![./img//01-hub-slack-workflows.png](./img//01-hub-slack-workflows.png)

Click on Install to install the App into your environment.

Close any notification prompts if necessary.

Validate that the App was installed into your environment.

![./img//01-slack-workflows-install.png](./img//01-slack-workflows-install.png)

In your Dynatrace environment, open the Workflows App.

Import the workflow 'Workflow Essentials - Config Generator' using the source file [Workflow Essentials - Config Generator](https://github.com/dynatrace-wwse/enablement-workflow-essentials/blob/main/lab-guide/assets/dt_wftpl_workflow_essentials_config_generator.yaml)

Workflows are imported using the Upload button.

![./img//01-import-config-generator.png](./img//01-import-config-generator.png)

Locate the `js_set_parameters` task.  Locate the code snippet for the Slack connection.

Set the `CONNECTION_TOKEN` value to the Slack App Bot User Token you have been provided (or have created).

![./img//01-config-generator-set-parameters.png](./img//01-config-generator-set-parameters.png)

Run the workflow and validate that it runs successfully.

![./img//01-config-generator-execution.png](./img//01-config-generator-execution.png)

As a result of the workflow, three configurations have been made to the Dynatrace environment:

1. A credential vault entry has been added containing a Dynatrace API token
    * Copy the credential vault ID from the result of the `js_create_credential` task and store it in your notes somewhere, it is needed in a future exercise
2. The allow list for outbound connections has been updated with the hosts/domains required for this lab
    * No action required, simply verify using screenshot below
3. A Slack Connection has been created called `workflow_essentials_demo`
    * No action required, simply verify using screenshot below

![./img//01-config-generator-results.png](./img//01-config-generator-results.png)

## Continue

In the next section, we'll launch our Codespaces instance.

<div class="grid cards" markdown>
- [Continue to Codespaces:octicons-arrow-right-24:](3-codespaces.md)
</div>
