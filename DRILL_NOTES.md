# Drill Notes — CI Failure Triage Drill

This repository is a **hands-on CI-failure triage drill** for the on-call rotation.

## What this is

A deliberately failing GitHub Actions workflow (`.github/workflows/drill-check.yml`, added in the `drill/seed-failure` branch) was opened as a pull request titled **"Drill: deliberate CI failure"**. The workflow is triggered by `pull_request` and contains a single job whose one step echoes:

```
simulated flaky network error (drill)
```

and then runs `exit 1`, guaranteeing a visible, greppable failure.

## Triage findings (from the failed run)

- **Workflow:** `Drill Check`
- **Failing job:** `drill`
- **Failing step:** `Simulate flaky network error`
- **Failure line in the logs:** `simulated flaky network error (drill)` followed by `##[error]Process completed with exit code 1.`

## This file

This file was added directly to `main` while the drill pull request was open, to simulate a teammate landing a change on the default branch during triage. It's also used to test the **"update branch"** step of the drill: syncing the PR branch with the latest `main` re-triggers the checks.

**Note:** No real networking issue exists — everything in this repo is simulated for training purposes.
