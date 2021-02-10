# Auto Green
A commit a day keeps your girlfriend away.

## GitHub Actions
### autogreen.yml
``` yaml
name: Auto-Green

on:
  schedule:
    - cron: "0 0 * * *"

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

## GitHub Docs
- [https://docs.github.com/en/actions](https://docs.github.com/en/actions)