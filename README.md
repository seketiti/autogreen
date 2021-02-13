# Auto Green
A commit a day keeps your girlfriend away.

## GitHub Actions
### YAML
YAML is a human-readable data-serialization language. It is commonly used for configuration files and in applications where data is being stored or transmitted.
``` yaml
name: Auto-Green

on:
  schedule:
    - cron: "0 0 * * 0-5"

jobs:
  autogreen:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2

      - name: Commit
        run: |
          git config --local user.name "username"
          git config --local user.email "email@address.com"
          git remote set-url origin https://${{ github.actor }}:${{ secrets.GITHUB_TOKEN }}@github.com/${{ github.repository }}
          git pull --rebase
          git commit --allow-empty -m "a commit a day keeps your girlfriend away"
          git push
```
### Cron syntax
Cron syntax has five fields separated by a space, and each field represents a unit of time.
```
┌───────────── minute (0 - 59)
│ ┌───────────── hour (0 - 23)
│ │ ┌───────────── day of the month (1 - 31)
│ │ │ ┌───────────── month (1 - 12 or JAN-DEC)
│ │ │ │ ┌───────────── day of the week (0 - 6 or SUN-SAT)
│ │ │ │ │                                   
│ │ │ │ │
│ │ │ │ │
* * * * *
```
You can use [crontab guru](https://crontab.guru/) to help generate your cron syntax and confirm what time it will run.

## GitHub Docs
- [https://docs.github.com/en/actions](https://docs.github.com/en/actions)