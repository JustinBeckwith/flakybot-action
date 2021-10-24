# flakybot-action
> A GitHub Action that opens bugs for failing tests on your default branch.  Detect flakes and control issue management.

## Example usage
With no arguments, flakbot will look for an `xunit.xml` in the root directory where your tests were run, and automatically apply issues against failed tests run in the default branch.  This is useful for things like integration tests and nightlies.

```yaml
on:
  push:
    branches:
      - main
  pull_request:
name: ci
jobs:
  integration:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v2
        with:
          node-version: 14
      - run: npm install
      - run: npm test
      - uses: JustinBeckwith/flakybot-action@v1
        with:
          path: xunit.xml
```

# License
[Apache 2.0](/LICENSE)
