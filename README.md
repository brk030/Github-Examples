# Github-Examples
A repo containing GitHub for programmatic examples

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

  