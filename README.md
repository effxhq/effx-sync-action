# effx-sync-action 🔄

GitHub action for syncing data to [effx](https://www.effx.com) 🔥

### Usage

```
name: effx sync
on:
  push:
    branches:
      - master

jobs:
  sync:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master
      - name: Sync effx configuration with effx account
        uses: effxhq/effx-sync-action@master
        with:
          directory: ${GITHUB_WORKSPACE}
        env:
          EFFX_API_KEY: ${{ secrets.EFFX_API_KEY }}
```

### Environment Variables

📁 **`directory`** _(required)_ - The relative path to the directory containing configuration files you'd like synced.\
🔑 **`EFFX_API_KEY`** _(required)_ - Your effx API key.

Setting `directory` to `${GITHUB_WORKSPACE}` enables syncing for **all** files with the suffix **`effx.yaml`** in your repo.

### Workflow

1. Add this action to your repo.
2. Head over to the **[effx website](https://app.effx.com/account_settings)**, navigate to **Account Settings** and find your API key.
3. Add your effx API key by
   - navigating to your repo's settings
   - selecting **Secrets** from the side bar
   - typing **`EFFX_API_KEY`** into the name field
   - pasting your effx API key into the value field
4. The **`yml`** file for **`effx-sync-action`** will live in **`.github/workflows`**.
5. Create a file named, **`effx.yaml`** or matching **`*.effx.yaml`**and populate it with configurations.
6. On pushing to **`master`**, **`effx-sync-action`** will parse your configuration file. 🥳
