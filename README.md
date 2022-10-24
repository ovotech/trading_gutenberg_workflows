# Gutenberg Workflows
Reusable Github Action workflows for repos adopting the Ovo Trading Gutenberg template.

# ⚠️This repository is public
This is due to a [limitation](https://docs.github.com/en/actions/using-workflows/reusing-workflows#access-to-reusable-workflows) in Github Actions. Please edit with care.


# Using a workflow
### Publishing a Docker image
1. [Onboard your repository to the Gutenberg auth mechanism](https://github.com/ovotech/trading-infra/blob/master/gutenberg.tf#L6).
2. In the repo for your own service, check in a Dockerfile (or similar approach to creating a Docker image).
3. Create a Github Actions workflow like the one below:
```yaml
name: Deploy my image

on:
  push:
    branches: [ 'main' ]

jobs:
  publish_image:
    uses: ovotech/trading_gutenberg_workflows/.github/workflows/publish_image.yaml@main
    with:
      service_name: your_service_name
      build_command: docker build -t your_service_name
```
Your image will be built and pushed to Artifact Registry upon a merge to `main`.