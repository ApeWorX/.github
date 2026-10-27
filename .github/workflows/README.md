# Reusable Workflows

These workflows apply to **every ApeWorX repo**, so care must be taken to ensure these workflows should **always** apply!

## `commitlint.yaml`

This workflow checks that each commit message in a branch matches https://www.conventionalcommits.org convention.
We do this in order to streamline the creation of changelogs from the release notes feature in Github.

## `prtitle.yaml`

This workflow checks that the title of each PR matches https://www.conventionalcommits.org convention.
Because we **always** use squash merging (with title as default message), this ensures consistency of our default branch commit history (see [`commitlint.yaml`](#commitlint-yaml)).
This also ensures consistency in our draft Github Releases.

## `publish.yaml`

Reusable Trusted Publishing job: checkout, `uv build`, and `pypa/gh-action-pypi-publish` with OIDC (`id-token: write`).

Callers keep a thin workflow with `on: release: types: [published]` and:

```yaml
jobs:
  deploy:
    uses: ApeWorX/.github/.github/workflows/publish.yaml@main
    permissions:
      contents: read
      id-token: write
```

**Caveat:** the release *event trigger* stays in each consumer repo; only the job body is shared. Prefer `types: [published]` so GitHub prereleases also publish.

This workflow intentionally omits `environment:` (the org does not gate PyPI publish on GitHub Environments today).
