# Github-Examples
A repo containing GitHub for programmatic examples

## GitHub Action Basics
### Workflow Triggers

- Are events that cause a workflow to run such as:
  - Events that occur in your workflow's repository
  - Events that occur outside GitHub and trigger a repository_dispatch event on GitHub
  - Scheduled Times
  - Manual

- A repo can contain multiple workflows

### Workflow Components
- Actions: Reusable tasks that perform a specific job within workflows
- Workflows: Automated processes defined in your repo that coordinate one or more jobs, triggered by events or on a schedule
- Jobs: Groups of steps that execute on the same runner, typically running in parallel unless configured otherwise
- Steps: Individual tasks within a job that run commands or actions sequentially 
- Runs: Instances of workflow execution triggered by events, representing the complete run-thorugh of a workflow 
- Runners: Servers that host the environment where jobs are executed, available as GitHib-hosted or self-hosted options
- Marketplace: A platform to find and share reusable actions, enhancing workflow capabilities with community-developed tools

### Scheduled events
- "schedule" can use a "cron" expression (argument such as "cron:") to trigger a workflow at specific time or day
- https://crontab.guru helps to tranlate time into cron expression 

### Single Event vs. Multiple Events
- If you specify multiple events, only one of those events need to occur to trigger your workflow. 
If multiple triggering events for your workflow occur at the same time, multiple workflow runs will be triggered.

### Manual Events
- Workflows can be triggered manually using the GitHub UI, GitHub CLI or GitHub REST API
- to run a workflow manually, the workflow must be configured to run on "workflow_dispatch" event
  - can define up to 10 inputs for a "workflow_dispatch" event
- using the CLI:
  - gh workflow run [name_of_files] -f [can_input_variables_using_flags]

### Webhook Events 
- Webhook - is an public facing URL that can be sent an HTTP request (often requiring authorization) to trigger events 
from external resources
- many of the listed GitHub Workflow Triggers are triggered by a webhook
- using "repository_dispatch" with webhook type you can trigger the Workflow via an external 
HTTP endpoint 
  - will only trigger a workflow run if the workflow is on the default branch

Example of curl webhook 
1. send a POST request to the rep's dispatched endpoint
2. set 'Accept' type for 'application/vnd.github+json'
3. provide authorization for your personal access token
4. pass the event type 'webhook'
```sh
curl -X POST \
-H "Accept: application/vnd.github+json" \
-H "Authorization: token {PAT/AUTH} \  # token word has to stay 
-d '{"event_type": "webhook", "client_payload": {"key": "value"} }' \
https://api.github.com/repos/{owner}/{repo}/dispatches
```


## Runners and Commands
### Runners
- determines the underlying compute and OS that the workflow will execute on
- can be GitHub- or self-hosted