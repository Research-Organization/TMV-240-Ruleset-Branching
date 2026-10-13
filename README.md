# TMV-240-Ruleset-Branching

This repository simulates protected promotion branches.

## Promotion flow

```text
task branch → PR → develop
develop → automated PR → staging → auto-merge
staging → manual PR → main
main → automated PR → production → auto-merge
production → automatic version tag
```

The staging and production promotion workflows create a pull request and request
auto-merge. They do not push directly to either protected branch.

## Ruleset settings for the simulation

Enable `Require a pull request before merging` on `staging`, `main`, and
`production`. Keep `Block force pushes` and `Restrict deletions` enabled.

For a fully automated test, require zero approvals and use the `CI` check as
the required status check. A production approval requirement will intentionally
leave the automated production PR waiting for a human approval.

- Test workflow
