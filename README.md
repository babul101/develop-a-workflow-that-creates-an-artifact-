# Artifact Creation Workflow

This GitHub Actions workflow automates the process of creating an artifact and uploading it to the repository. It is triggered by a push event.

## Workflow Triggers

The workflow is triggered on the following event:
- Push to any branch

## Environment Variable

An environment variable named `ARTIFACT_NAME` is defined to specify the name of the artifact. In this workflow, the artifact name is set to `my_artifact`. You can customize this variable as needed.

## Jobs

### Main Job

The `main` job executes the following steps:

1. **Checkout Repository**: This step uses the `actions/checkout@v2` action to clone the repository's code onto the runner environment.

2. **Upload Artifact**: This step utilizes the `actions/upload-artifact@v2` action to create an artifact with the name specified by the `ARTIFACT_NAME` environment variable. The artifact is uploaded with files from the root directory of the repository.

## Workflow YAML

```yaml
name: Artifact Creation Workflow

on:
  push

env:
  ARTIFACT_NAME: my_artifact

jobs:
  main:
    runs-on: ubuntu-latest
    
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v2
      
      - name: Upload Artifact
        uses: actions/upload-artifact@v2
        with:
          name: ${{ env.ARTIFACT_NAME }}
          path: .
