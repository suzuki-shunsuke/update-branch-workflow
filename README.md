# update-branch-workflow

GitHub Actions Reusable Workflow to update branch by pull request comment

## Workflow

[workflow](.github/workflows/update-branch.yaml)

## How to use

e.g.

```yaml
---
name: update pull request branch by pull request comment
on: issue_comment
jobs:
  update-branch:
    uses: suzuki-shunsuke/update-branch-workflow/.github/workflows/update-branch.yaml@29187410ef7122d48f004f01b5244013a5880d2f # v0.1.0
    secrets:
      gh_app_id: ${{secrets.APP_ID}}
      gh_app_private_key: ${{secrets.APP_PRIVATE_KEY}}
```

## Why is this workflow needed?

GitHub has already supported updating branch via Web UI, so basically you don't have to use this workflow.

https://github.blog/changelog/2022-02-03-more-ways-to-keep-your-pull-request-branch-up-to-date/

This feature is useful when you allow users who don't have the permission to push a commit to update branch.
For example, when users can't push a commit to the branch because of the branch protection rule, this workflow is useful.

## :warning: This workflow creates a commit even if the branch is up-to-date

This workflow uses [GitHub REST API](https://docs.github.com/en/rest/reference/pulls#update-a-pull-request-branch), but this API creates a commit without error even if the branch is up-to-date.

## LICENSE

[MIT](LICENSE)
