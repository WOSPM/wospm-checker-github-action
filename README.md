# WOSPM Checker Github Action

This action is for executing [WOSPM Checker](https://github.com/WOSPM/checker) tool in your pipeline. It will create HTML report which is downloadable as artifact.

## Inputs

No input is needed.

## Outputs

No output is given.

## Example usage

```
name: WOSPM Checker
on: [push]

jobs:
  wospm_checker:
    runs-on: ubuntu-latest
    name: WOSPM Checker
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: WOSPM Checker Github Action
        uses: WOSPM/wospm-checker-github-action@v1
      - name: Upload HTML Report When Success
        uses: actions/upload-artifact@v1
        with:
          name: HTML Report
          path: wospm.html
      - name: Upload HTML Report When Failed
        uses: actions/upload-artifact@v1
        if: failure()
        with:
          name: HTML Report
          path: wospm.html
```
