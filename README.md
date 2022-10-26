# PR Validation Action

This is a GitHub action that does two things when a PR is opened. 

1. It validates that a sentinel value is not found in the PR comments.
2. It validates that a regular expression is found in the PR comments.

This is to be used to ensure that we have both removed the fixme.addi.com links from our PR template, and that we've
replaced them with a properly formatted Asana link.

## How to use
This is a normal GitHub Action, so create a workflow step to use it. For example

```yaml
name: Asana Link Validation

on:
  pull_request:

jobs:
  valid-asana-link:
    runs-on: ubuntu-latest

    steps:
      - name: Validate Asana link
        uses: /pr-validation-action@v0.0.1
        with:
          sentinel: "fixme.addi.com"
          regex: 'https://app.asana.com/\d/\d+/\d+/f'
```

## Modifying this action
This is based off of GitHub's TypeScript template. The original template README is in template_readme.md.
The tl;dr is: make your changes, run `npm run build && npm run package`, then commit and push. 
Create a release, and update the version in the workflow.

