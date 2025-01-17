# `jest-serial-runner`

<p align="center">
  <a href="https://www.npmjs.com/package/@codejedi365/jest-serial-runner">
    <img src="https://img.shields.io/npm/v/@codejedi365/jest-serial-runner" />
  </a>
  <a href="https://github.com/codejedi365/jest-serial-runner/LICENSE.md">
    <img src="https://img.shields.io/npm/l/@codejedi365/jest-serial-runner?color=lightgrey">
  </a>
  <a href="https://github.com/codejedi365/jest-serial-runner/releases">
    <img src="https://img.shields.io/badge/&#9741-changelog-lightgrey">
  </a>
  <!-- <a href="https://github.com/codejedi365/jest-serial-runner/actions/workflows/cicd.yml">
    <img src="https://github.com/codejedi365/jest-serial-runner/actions/workflows/cicd.yml/badge.svg" >
  </a> -->
  <a href="https://github.com/codejedi365/jest-serial-runner/issues">
    <img src="https://img.shields.io/github/issues/codejedi365/jest-serial-runner">
  </a>
  <a href="https://github.com/codejedi365/jest-serial-runner/pulls">
    <img src="https://img.shields.io/github/issues-pr/codejedi365/jest-serial-runner?label=PRs">
  </a>
  <a href="https://snyk.io/advisor/npm-package/@codejedi365/jest-serial-runner">
    <img src="https://img.shields.io/snyk/vulnerabilities/npm/@codejedi365/jest-serial-runner">
  </a>
</p>
<p align="center">
  <img src="https://img.shields.io/npm/dependency-version/@codejedi365/jest-serial-runner/peer/jest-runner">
  <img src="https://img.shields.io/static/v1?logo=javascript&label=JavaScript&message=CommonJs">
  <img src="https://img.shields.io/github/last-commit/codejedi365/jest-serial-runner">
</p>
<p align="center">
  <!-- <a href="https://github.com/semantic-release/semantic-release">
    <img src="https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg" >
  </a> -->
  <img src="https://img.shields.io/badge/Contributors-PR's_welcome-pink">
</p>
<p align="center">
  Extending the <a href="https://jestjs.io/">Jest</a>
  default runner to run tests serially by default
</p>

---

Simple wrapper over the default Jest runner that forces serial execution of test files. This is equivalent to running with `--runInBand` flag by default.

**Why?** Sometimes you have limited/restricted resources on the test machine (like in a docker container) and running the default `jest-runner` always runs in parallel unless specified otherwise. Integration tests are another scenario where running concurrent instances causes issues so using this runner ensures only 1 test runs at a time.

## Installation

```sh
npm install @codejedi365/jest-serial-runner --save-dev
```

## Usage

**Option 1:** Specify the runner in your `Jest` config

```jsonc
/* jest.config.json */
{
    // ...
    "runner": "@codejedi365/jest-serial-runner"
    // ...
}
```

**Option 2:** To specify the runner for a subset of files such as for integration tests.

```js
/* jest.config.js */
module.exports = {
    // ...
    projects: [
        {
            // Uses the jest default runner for specification testing
            displayName: "UNIT",
            testMatch: ["<rootDir>/src/**/__tests__/*.spec.ts"]
        },
        {
            // Uses the serial runner instead for integration test files
            displayName: "INTEGRATION",
            runner: "@codejedi365/jest-serial-runner",
            testMatch: ["<rootDir>/tests/**/*.integration-test.ts"]
        }
    ]
}
```

## Contributors

PR's & Issue contributions welcome! Please adhere to
[contributing guidelines](./CONTRIBUTING.md)
or your submission will be closed or delayed.

## Acknowledgements

**Origin:** [gabrieli/jest-serial-runner](https://github.com/gabrieli/jest-serial-runner)

**Contributors**

1. [Adam Uhlíř](https://github.com/AuHau)
