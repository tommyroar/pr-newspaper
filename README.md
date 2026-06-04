# pr-newspaper — reusable PR "newspaper" validation

The model-free CI half of the newspaper PR framework. Repos opt in with a 4-line
caller workflow:

```yaml
name: PR newspaper
on:
  pull_request:
    types: [opened, edited, reopened]
jobs:
  newspaper:
    uses: tommyroar/pr-newspaper/.github/workflows/validate.yml@main
```

- `.github/workflows/validate.yml` — reusable workflow (`workflow_call`).
- `scripts/validate_pr.py` — pure-stdlib validator (height/page budget + structure).
- `scripts/tier.py` — sizes the 2- vs 4-page budget from a PR's non-prose churn.

The format **rules** + the PR template live in [`tommyroar/.github`](https://github.com/tommyroar/.github)
(`PR_FRAMEWORK.md` + `pull_request_template.md`). Generation happens once, by the
agent that opens/updates a PR; this repo only enforces.
