`github-markdown-to-notion-db` is a GitHub Actions for syncing markdown docs to Notion DB.

### Usage

1. Create Notion Integration.
   - https://developers.notion.com/docs/create-a-notion-integration
1. Set env `NOTION_API_TOKEN`, `NOTION_DB_ID`, `GITHUB_MD_PATH` in your GitHub repository.
   - https://github.com/<your\>/<repository\>/settings
1. Create workflow yaml.

```yml
name: Sync markdown To Notion DB

on:
  workflow_dispatch:
  schedule:
    - cron: "00 * * * *"

jobs:
  sync:
    name: Sync docs
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Sync my docs to notion
        uses: vdubois/github-markdown-to-notion-db@main
        env:
          NOTION_API_TOKEN: ${{ secrets.NOTION_API_TOKEN }}
          NOTION_DB_ID: ${{ secrets.NOTION_DB_ID }}
          GITHUB_MD_PATH: "docs"
```
