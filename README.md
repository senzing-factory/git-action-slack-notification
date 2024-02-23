# Git Action Slack Notification

Git Action to send messages to Slack. This action can be used to send message about the status of a Git Action workflow.

## Usage

This action can be used after any other action. Below is simple example on using it:

1\. Create a `.github/workflows/git-action-slack-notification.yml`

2\. Add the following properties to `git-action-slack-notification.yml` file

```yaml
on: push
name: Slack Notification Demo
jobs:
    slackNotification:
      name: Slack Notification Demo
      runs-on: ubuntu-latest
      steps:
      - uses: actions/checkout@master
      - name: Slack Notification Demo
        uses: senzing/git-action-slack-notification@1.0.0
        env:
          SLACK_WEBHOOK: ${{ secrets.SLACK_WEBHOOK }}
          SLACK_TITLE: Slack Notification Demo
          SLACK_MESSAGE: Demo'ing the Slack Notification
```

Go [here](deployment/git-actions/template_git_action_slack_notification.yml) for a template yml with all environment variables.

3\. Generate Slack WebHook [here](https://entelexeia.slack.com/apps/A0F7XDUAZ-incoming-webhooks?next_id=0)

4\. Encrypt Slack Webhook as a secret in the repository using this app.

## Environment Variables

These are the environment variables that can be set to pass in additional information about the Git Action.

| Variable Name      | Required | Description |
|--------------------|:--------:|-------------|
| GITHUB_ACTION | No | GitHub Action name variable passed from Git Actions |
| GITHUB_ACTOR | No | GitHub Actor variable passed from Git Actions |
| GITHUB_EVENT_NAME | No | GitHub Action event name variable passed from Git Actions |
| GITHUB_REF | No | GitHub reference variable passed from Git Actions |
| GITHUB_REPOSITORY | No | GitHub Repository variable passed from Git Actions |
| GITHUB_WORKFLOW | No | GitHub Action workflow varaible passed from Git Actions |
| SLACK_CHANNEL | No | The Slack channel to use instead of the default |
| SLACK_COLOR | No | Format color to use for the Slack message |
| SLACK_ICON | No | The Slack user icon to use instead of the default |
| SLACK_MESSAGE | Yes | The message payload to be sent to Slack|
| SLACK_TITLE | Yes | Title of the Slack message being sent. |
| SLACK_USERNAME | No | The Slack username to use instead of the default |
| SLACK_WEBHOOK | Yes | The Webhook URL generated by Slack to send messages too. |

## Reference

* [Using environment variables](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/using-environment-variables) lists the default environment variables set in Git Actions.

## License

[Apache 2](LICENSE)
