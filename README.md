# custom-workflows/reactivate

GitHub action to prevent GitHub from suspending cronjob based triggers due to repository inactivity.

## Found a bug? 💁‍♀️

Thanks for letting us know! Please [file an issue](../../issues/new?assignees=&labels=&template=bug_report.md&title=) and we should reply shortly.

## Configuration

This action requires the presence of inputs, which are listed below.

### Inputs

- `commit_message`: Commit message used while committing to the repository. (**optional**)
- `committer_username`: Username used while committing to the repository. (**optional**)
- `committer_email`: Email used while committing to the repository. (**optional**)
- `days_elapsed`: Time elapsed from the last commit to trigger a new automated commit (in days) (**optional**)

## Example

Below you will find an example of how you can use this action.

```yml
name: "Cronjob"

on:
  schedule:
    - cron: '0 0 * * *'  # every day at midnight
    
permissions:
  contents: "write" # required
  
jobs:
  cronjob:
    runs-on: "ubuntu-latest"
    
    steps:
      - name: "Checkout Repository"
        uses: "actions/checkout@v3"
        
      - name: "Reactivate Repository"
        uses: "custom-workflows/reactivate@latest"
        with: 
          commit_message: "github-actions: Reactivate repository"
          committer_username: "GitHub Actions [Bot]"
          committer_email: "github-actions[bot]@users.noreply.github.com"
          days_elapsed: 50
```
