# Skpr DB Image Pull Action

A [Github Action](https://docs.github.com/en/actions) for automated deployments to [Skpr](https://www.skpr.com.au)

This action pulls a Skpr Database Image for the specified environment.

## Secrets

You need to set your Skpr credentials by setting the `SKPR_USERNAME` and `SKPR_PASSWORD` secrets.

## Inputs

### `env`

**Required** The Skpr environment.

## Example Workflow Usage
```
name: build 
on: [push]

env:
  SKPR_USERNAME: ${{ secrets.SKPR_USERNAME }}
  SKPR_PASSWORD: ${{ secrets.SKPR_PASSWORD }}

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v3
        with: { fetch-depth: 0 }
      - name: Setup Skpr
        uses: skpr/setup-action
      - name: Pull Skpr DB Image
        uses: skpr/image-pull
        with: { env: dev }
```
