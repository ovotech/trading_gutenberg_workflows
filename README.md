# trading_gutenberg_workflows
Reusable Github Action workflows for services run by Ovo Trading.

# ⚠️This repository is public
This is due to a [limitation](https://docs.github.com/en/actions/using-workflows/reusing-workflows#access-to-reusable-workflows) in Github Actions. Please edit with care.


# Using workflows
### Publishing a Docker image
Call it like this:
```yaml
name: Deploy

on:
  push:
    branches: [ 'main' ]

jobs:
  publish_image:
    uses: ovotech/trading_gutenberg_workflows/.github/workflows/deploy.yaml@main
    with:
      service_name: your_service_name
      build_command: docker build
```