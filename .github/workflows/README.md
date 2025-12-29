# Reusable Workflows

These workflows apply to **every ApeWorX repo**, so care must be taken to ensure these workflows should **always** apply!

## `commitlint.yaml`

This workflow checks that each commit message in a branch matches https://www.conventionalcommits.org convention.
We do this in order to streamline the creation of changelogs from the release notes feature in Github.

## `prtitle.yaml`

This workflow checks that the title of each PR matches https://www.conventionalcommits.org convention.
Because we **always** use squash merging (with title as default message), this ensures consistency of our default branch commit history (see [`commitlint.yaml`](#commitlint-yaml)).
This also ensures consistency in our draft Github Releases.
