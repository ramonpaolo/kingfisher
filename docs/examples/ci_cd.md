## Examples

This documentation will show about how to use the kingfisher with the CI/CD on GitHub Actions!

### GitHub Action

The following yml code is an example to use on a real action on GitHub!

This action will run every time that when the PR are opened or receive a new commit signal.

```yml
name: Analyze PR
on:
  pull_request:
    types:
      - opened
      - synchronize

jobs:
  build:
    name: build
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@main

      - name: Kingfisher Scan
        run: |
            git clone https://github.com/mongodb/kingfisher/tree/v1.9.0 kingfisher
            cd kingfisher
            make linux-x64
            kingfisher scan

```
