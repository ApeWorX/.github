# Reusable Workflows

These workflows apply to **every ApeWorX repo**, so care must be taken to ensure these workflows should **always** apply!

## `commitlint.yaml`

This workflow checks that each commit message in a branch matches https://www.conventionalcommits.org convention.
We do this in order to streamline the creation of changelogs from the release notes feature in Github.

## `prtitle.yaml`

This workflow checks that the title of each PR matches https://www.conventionalcommits.org convention.
Because we **always** use squash merging (with title as default message), this ensures consistency of our default branch commit history (see [`commitlint.yaml`](#commitlint-yaml)).
This also ensures consistency in our draft Github Releases.

## Publish (composite action, not a reusable workflow)

PyPI Trusted Publishing does **not** support cross-repository reusable workflows
(`pypi/warehouse#11096`). Centralized publish steps live in a **composite action**:

`ApeWorX/.github/.github/actions/publish`

Caller (thin per-repo `.github/workflows/publish.yaml`) keeps the release trigger
and the workflow filename PyPI already trusts:

```yaml
name: Release
on:
  release:
    types: [published]
jobs:
  deploy:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      id-token: write
    steps:
      - uses: ApeWorX/.github/.github/actions/publish@main
```

**Caveat:** the `on: release` trigger stays in each consumer repo. Prefer
`types: [published]` so GitHub prereleases also publish. No `environment:`
(org does not gate PyPI publish on GitHub Environments today).
