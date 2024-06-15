# pre-commit-hooks

This repository is a collection of Git hooks to be used with the
[pre-commit](https://pre-commit.com/) framework.

- [Available Hooks](#available-hooks)
  - [Terramate](#terramate)
- [Installation & Dependencies](#installation--dependencies)
- [Usage](#usage)
  - [Run](#run)
    - [Example: Run All Hooks](#example-run-all-hooks)
    - [Example: Run A Specific Hook](#example-run-a-specific-hook)
  - [Pre-Commit and Continuous Integration](#pre-commit-and-continuous-integration)
  - [Add Custom Hooks](#add-custom-hooks)
- [Module Versioning](#module-versioning)
  - [Backwards compatibility in `0.0.z` and `0.y.z` version](#backwards-compatibility-in-00z-and-0yz-version)
- [About Mineiros](#about-mineiros)
- [Reporting Issues](#reporting-issues)
- [Contributing](#contributing)
- [Makefile Targets](#makefile-targets)
- [License](#license)

## Available Hooks

Currently, the following hooks are supported:

### Terramate

- [terramate-fmt](https://github.com/terramate-io/terramate): The terramate generate command formats code in Terramate configuration files.
- [terramate-generate](https://github.com/terramate-io/terramate): The terramate generate command generates code from Terramate configuration files.

## Installation & Dependencies

1. Install [pre-commit](https://pre-commit.com/). E.g. `brew install pre-commit`
1. Install [Terraform](https://www.terraform.io/), [TFLint](https://github.com/terraform-linters/tflint),
   [Go](https://golang.org/), [markdown-link-check](https://github.com/tcort/markdown-link-check),
   [shellcheck](https://github.com/koalaman/shellcheck). E.g

   ```shell script
     brew install terraform \
         tflint \
         go \
         golangci/tap/golangci-lint \
         shellcheck && \
         npm install -g markdown-link-check && \
         go install github.com/terramate-io/terradoc/cmd/terradoc@latest
   ```

## Usage

Create a `.pre-commit-config.yaml` inside your repositories and add the desired list of hooks.
Please see the [documentation](https://pre-commit.com/#usage) for further information.

```yaml
repos:
  - repo: https://github.com/mineiros-io/pre-commit-hooks
    rev: <VERSION> # Check for the latest version: https://github.com/mineiros-io/pre-commit-hooks/releases
    hooks:
      - id: terraform-fmt
      - id: terraform-validate
      - id: tflint
      - id: golangci-lint
      - id: phony-targets
      - id: markdown-link-check
        args: [-p] # When adding the -p flag, markdown-link-check will always with an exit code 0, even if dead links are found
      - id: shellcheck
      - id: terradoc-validate
      - id: terradoc-fmt
      - id: terradoc-generate
      - id: terramate-generate

      # The following hooks are redundant when golangci-lint is being. Our recommendation is to use golangci-lint
      # as the main linter for go since it enables you to run all available linters in parallel.
      # For details please see the example configuration https://github.com/mineiros-io/pre-commit-hooks/blob/master/.golangci.example.yml
      # - id: gofmt
      # - id: goimports
```

Once you created the configuration file inside your repository, you must run `pre-commit install` to activate the hooks.
That's it, pre-commit will now listen for changes in your files and run the checks accordingly.

### Run

It's usually a good idea to run the hooks against all of the files when adding new hooks (usually pre-commit will only
run on the changed files during git hooks).

#### Example: Run All Hooks

```shell script
pre-commit run --all-files
```

#### Example: Run A Specific Hook

```shell script
pre-commit run terraform-validate --all-files
```

### Pre-Commit and Continuous Integration

It's recommended to run pre-commit as part of CI pipeline/build as there will be always that one rebel in the team
who won't run them locally. On CI, replace `pre-commit install` by `pre-commit run -a`. We don't need to install it on
CI as it'll be a one-shot operation. run -a will run the hooks over all files (taking into account excludes if
configured).

### Add Custom Hooks

All `*.sh` files inside pre_commit_hooks need to be flagged as executable. Otherwise the pre-commit hooks won't be
executable by default. You apply the flag to all `*.sh` files with the following command:

```bash
find pre_commit_hooks/ -type f -iname "*.sh" -exec chmod +x {} \;
```

## Module Versioning

This Module follows the principles of [Semantic Versioning (SemVer)](https://semver.org/).

Using the given version number of `MAJOR.MINOR.PATCH`, we apply the following constructs:

1. Use the `MAJOR` version for incompatible changes.
1. Use the `MINOR` version when adding functionality in a backwards compatible manner.
1. Use the `PATCH` version when introducing backwards compatible bug fixes.

### Backwards compatibility in `0.0.z` and `0.y.z` version

- In the context of initial development, backwards compatibility in versions `0.0.z` is **not guaranteed** when `z` is
  increased. (Initial development)
- In the context of pre-release, backwards compatibility in versions `0.y.z` is **not guaranteed** when `y` is
  increased. (Pre-release)

## About Mineiros

Mineiros is a [DevOps as a Service](https://mineiros.io/?ref=pre-commit-hooks) company based in Berlin, Germany. We offer commercial support
for all of our projects and encourage you to reach out if you have any questions or need help.
Feel free to send us an email at [hello@mineiros.io](mailto:hello@mineiros.io).

We can also help you with:

- Terraform modules for all types of infrastructure such as VPCs, Docker clusters, databases, logging and monitoring, CI, etc.
- Consulting & training on AWS, Terraform and DevOps

## Reporting Issues

We use GitHub [Issues](https://github.com/mineiros-io/pre-commit-hooks/issues)
to track community reported issues and missing features.

## Contributing

Contributions are always encouraged and welcome! For the process of accepting changes, we use
[Pull Requests](https://github.com/AzgadAGZ/pre-commit-hooks/pulls). If you'd like more information, please
see our [Contribution Guidelines](https://github.com/AzgadAGZ/pre-commit-hooks/blob/master/CONTRIBUTING.md).

## License

This module is licensed under the Apache License Version 2.0, January 2004.
Please see [LICENSE](https://github.com/AzgadAGZ/pre-commit-hooks/blob/master/LICENSE) for full details.

