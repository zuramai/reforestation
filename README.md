# Reforestation

**Reforestation** is a simple "commit cheat" workflow that periodically updates a `LAST_UPDATED` file with a timestamp and commits it back to the repository. This helps keep the repository active and can be useful for maintaining a regular commit history (e.g., for personal projects, learning, or testing GitHub Actions).

## Description

The repository contains a single GitHub Actions workflow (`.github/workflows/reforestation.yml`) that runs on two triggers:

* **Push to `main`** – when you push any change, the workflow updates the timestamp.
* **Scheduled runs** – every 4 hours (`0 1/4 * * *`) – to automatically keep the repository "fresh" without manual intervention.

Each run writes the current UTC timestamp to `LAST_UPDATED` and commits the change with a playful commit message. The workflow uses a personal GitHub token to push the commit, overwriting the branch with `--force`.

## Installation / Setup

No additional setup is required. Simply:

1. **Copy this repository** as a template or add the workflow file to any GitHub repository you own.
2. **Enable the repository** (or ensure Actions are allowed) and push an initial commit to the `main` branch.
3. The workflow will automatically start running on pushes and according to the scheduled cron.

## Usage

* **Observe automatic updates** – Check the `LAST_UPDATED` file in the repository; it will be updated with the current timestamp after each workflow run.
* **Monitor workflow runs** – View the Actions tab in your GitHub repository to see each commit event and any failures.
* **Customize the workflow** – If needed, edit `.github/workflows/reforestation.yml` to change the cron schedule, commit message, or the file being updated.

This cheat is lightweight, requires no external dependencies, and can be used as a baseline for more complex automation or as a way to keep personal repos "reforested" with regular commits.
